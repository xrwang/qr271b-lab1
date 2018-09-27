technotrust
================
xiaowei
9/27/2018

``` r
responses <- readxl::read_xls('Techno trust (Responses).xls')
responses
```

    ## # A tibble: 21 x 12
    ##    Timestamp           Score `1. Select the tec… `2. Select the category …
    ##    <dttm>              <dbl> <chr>               <chr>                    
    ##  1 2018-09-21 16:38:33    0. VR (Oculus rift)    Social media (Facebook, …
    ##  2 2018-09-21 16:42:07    0. Bitcoins or other … Social media (Facebook, …
    ##  3 2018-09-21 16:47:41    0. Haven't used any o… Social media (Facebook, …
    ##  4 2018-09-21 18:14:06    0. Bitcoins or other … Social media (Facebook, …
    ##  5 2018-09-21 19:22:41    0. Home virtual assit… Social media (Facebook, …
    ##  6 2018-09-21 20:05:38    0. Haven't used any o… Social media (Facebook, …
    ##  7 2018-09-21 20:37:09    0. VR (Oculus rift)    Navigation               
    ##  8 2018-09-22 09:12:56    0. Haven't used any o… Daily Planner, Navigation
    ##  9 2018-09-22 11:07:11    0. Wearables (fitbit,… Social media (Facebook, …
    ## 10 2018-09-22 11:45:46    0. VR (Oculus rift)    Social media (Facebook, …
    ## # ... with 11 more rows, and 8 more variables: `Who do you believe should
    ## #   be most responsible for the spread of biased or incorrect content on
    ## #   Facebook's news feed?` <chr>, `4. Please indicate how much you agree
    ## #   or disagree with the statement: I am comfortable with the use of
    ## #   emerging technologies (Chatbots, RoboAdvisors or VR etc.)` <chr>, `5.
    ## #   Please indicate how much you agree or disagree with the statement:
    ## #   Chatbots are likely to be more efficient than human beings in
    ## #   responding to customer service complaints` <chr>, `6. Please indicate
    ## #   how much you agree or disagree with the statement: I am likely to
    ## #   consider an investment opportunity recommended by an algorithm` <chr>,
    ## #   `7. Please indicate how much you agree or disagree with the statement:
    ## #   I am afraid that emerging technologies (Chatbots, self driving cars,
    ## #   Robo Advisors) are going to replace the need for humans in places of
    ## #   employment` <chr>, `8. In March 2018, a woman was hit and killed by a
    ## #   self driving car. What do you view as the most appropriate next
    ## #   step?` <chr>, `9. Which emerging technology has been the most useful
    ## #   to you` <chr>, `10. Would you trust emerging technologies (Robo
    ## #   advisors, chatbots, self driving cars) enough to include them in your
    ## #   personal life, and why?` <chr>

``` r
#write_csv(responses, 'TechnoTrustResponses.csv')

#Nominal Categorical Questions: columns/qs
#1 2 3 8 

#Question 1
responses %>% group_by(., `1. Select the technology that you have used the most from the list below`) %>% 
  count(sort = TRUE)
```

    ## Warning: package 'bindrcpp' was built under R version 3.4.4

    ## # A tibble: 5 x 2
    ## # Groups:   1. Select the technology that you have used the most from the
    ## #   list below [5]
    ##   `1. Select the technology that you have used the most from the li…     n
    ##   <chr>                                                              <int>
    ## 1 Haven't used any of the above                                          7
    ## 2 Home virtual assitants (Google home, Alexa)                            4
    ## 3 Wearables (fitbit, Apple watch)                                        4
    ## 4 Bitcoins or other crypto currencies                                    3
    ## 5 VR (Oculus rift)                                                       3

``` r
#Question 2
responses %>% group_by(., `2. Select the category that you most use your phone for. You may select more than one.`) %>% count(sort = TRUE)
```

    ## # A tibble: 16 x 2
    ## # Groups:   2. Select the category that you most use your phone for. You
    ## #   may select more than one. [16]
    ##    `2. Select the category that you most use your phone for. You ma…     n
    ##    <chr>                                                             <int>
    ##  1 Social media (Facebook, Instagram, LinkedIn,Snap, etc), Messagin…     4
    ##  2 Social media (Facebook, Instagram, LinkedIn,Snap, etc), Daily Pl…     2
    ##  3 Social media (Facebook, Instagram, LinkedIn,Snap, etc), Messagin…     2
    ##  4 Daily Planner, Messaging apps (Whatsapp, Wechat, e.t.c.), Naviga…     1
    ##  5 Daily Planner, Messaging apps (Whatsapp, Wechat, e.t.c.), Web br…     1
    ##  6 Daily Planner, Navigation                                             1
    ##  7 Messaging apps (Whatsapp, Wechat, e.t.c.), Navigation                 1
    ##  8 Messaging apps (Whatsapp, Wechat, e.t.c.), Navigation, Web brows…     1
    ##  9 Navigation                                                            1
    ## 10 Social media (Facebook, Instagram, LinkedIn,Snap, etc), Daily Pl…     1
    ## 11 Social media (Facebook, Instagram, LinkedIn,Snap, etc), Daily Pl…     1
    ## 12 Social media (Facebook, Instagram, LinkedIn,Snap, etc), Daily Pl…     1
    ## 13 Social media (Facebook, Instagram, LinkedIn,Snap, etc), Health t…     1
    ## 14 Social media (Facebook, Instagram, LinkedIn,Snap, etc), Messagin…     1
    ## 15 Social media (Facebook, Instagram, LinkedIn,Snap, etc), Messagin…     1
    ## 16 Social media (Facebook, Instagram, LinkedIn,Snap, etc), Navigati…     1

``` r
#Question 3
responses %>% group_by(., `Who do you believe should be most responsible for the spread of biased or incorrect content on Facebook's news feed?`) %>% count(sort = TRUE)
```

    ## # A tibble: 8 x 2
    ## # Groups:   Who do you believe should be most responsible for the spread
    ## #   of biased or incorrect content on Facebook's news feed? [8]
    ##   `Who do you believe should be most responsible for the spread of …     n
    ##   <chr>                                                              <int>
    ## 1 Engineers that build the algorithm                                     5
    ## 2 Government - Lack of regulations                                       5
    ## 3 No opinion                                                             3
    ## 4 Users themselves                                                       3
    ## 5 Facebook CEO                                                           2
    ## 6 All of the above                                                       1
    ## 7 Policies that govern  platforms like Facebook                          1
    ## 8 The company's miss as well as users' lack of active probing            1

``` r
#Question 8
responses %>% group_by(., `8. In March 2018, a woman was hit and killed by a self driving car. What do you view as the most appropriate next step?`) %>% count(sort = TRUE)
```

    ## # A tibble: 7 x 2
    ## # Groups:   8. In March 2018, a woman was hit and killed by a self driving
    ## #   car. What do you view as the most appropriate next step? [7]
    ##   `8. In March 2018, a woman was hit and killed by a self driving c…     n
    ##   <chr>                                                              <int>
    ## 1 Further moral and ethical study of automation needs to be underta…     8
    ## 2 These incidents will lessen as engineering becomes more sophistic…     7
    ## 3 Government should regulate these new technologies                      2
    ## 4 a combination of several of the above answers                          1
    ## 5 Almost all of the above                                                1
    ## 6 Multiple of above options. Government should regulate, company sh…     1
    ## 7 Restrict automation to only certain contexts                           1

## Technology use and implications for trust / delegation?

``` r
#Group by technology used and response to facebook question

responses %>% group_by(., `1. Select the technology that you have used the most from the list below`,`2. Select the category that you most use your phone for. You may select more than one.`,`Who do you believe should be most responsible for the spread of biased or incorrect content on Facebook's news feed?`) %>% count(sort = TRUE)
```

    ## # A tibble: 20 x 4
    ## # Groups:   1. Select the technology that you have used the most from the
    ## #   list below, 2. Select the category that you most use your phone for.
    ## #   You may select more than one., Who do you believe should be most
    ## #   responsible for the spread of biased or incorrect content on
    ## #   Facebook's news feed? [20]
    ##    `1. Select the tec… `2. Select the category… `Who do you believe…     n
    ##    <chr>               <chr>                    <chr>                <int>
    ##  1 Haven't used any o… Social media (Facebook,… Government - Lack o…     2
    ##  2 Bitcoins or other … Messaging apps (Whatsap… Government - Lack o…     1
    ##  3 Bitcoins or other … Social media (Facebook,… Engineers that buil…     1
    ##  4 Bitcoins or other … Social media (Facebook,… Facebook CEO             1
    ##  5 Haven't used any o… Daily Planner, Messagin… Users themselves         1
    ##  6 Haven't used any o… Daily Planner, Navigati… Facebook CEO             1
    ##  7 Haven't used any o… Social media (Facebook,… Users themselves         1
    ##  8 Haven't used any o… Social media (Facebook,… Engineers that buil…     1
    ##  9 Haven't used any o… Social media (Facebook,… No opinion               1
    ## 10 Home virtual assit… Social media (Facebook,… Engineers that buil…     1
    ## 11 Home virtual assit… Social media (Facebook,… All of the above         1
    ## 12 Home virtual assit… Social media (Facebook,… Users themselves         1
    ## 13 Home virtual assit… Social media (Facebook,… No opinion               1
    ## 14 VR (Oculus rift)    Navigation               Government - Lack o…     1
    ## 15 VR (Oculus rift)    Social media (Facebook,… No opinion               1
    ## 16 VR (Oculus rift)    Social media (Facebook,… The company's miss …     1
    ## 17 Wearables (fitbit,… Daily Planner, Messagin… Policies that gover…     1
    ## 18 Wearables (fitbit,… Messaging apps (Whatsap… Engineers that buil…     1
    ## 19 Wearables (fitbit,… Social media (Facebook,… Engineers that buil…     1
    ## 20 Wearables (fitbit,… Social media (Facebook,… Government - Lack o…     1

``` r
#group by question 1 and facebook q
responses %>% group_by(., `1. Select the technology that you have used the most from the list below`,`Who do you believe should be most responsible for the spread of biased or incorrect content on Facebook's news feed?`) %>% count(sort = TRUE)
```

    ## # A tibble: 18 x 3
    ## # Groups:   1. Select the technology that you have used the most from the
    ## #   list below, Who do you believe should be most responsible for the
    ## #   spread of biased or incorrect content on Facebook's news feed? [18]
    ##    `1. Select the technology t… `Who do you believe should be most …     n
    ##    <chr>                        <chr>                                <int>
    ##  1 Haven't used any of the abo… Government - Lack of regulations         2
    ##  2 Haven't used any of the abo… Users themselves                         2
    ##  3 Wearables (fitbit, Apple wa… Engineers that build the algorithm       2
    ##  4 Bitcoins or other crypto cu… Engineers that build the algorithm       1
    ##  5 Bitcoins or other crypto cu… Facebook CEO                             1
    ##  6 Bitcoins or other crypto cu… Government - Lack of regulations         1
    ##  7 Haven't used any of the abo… Engineers that build the algorithm       1
    ##  8 Haven't used any of the abo… Facebook CEO                             1
    ##  9 Haven't used any of the abo… No opinion                               1
    ## 10 Home virtual assitants (Goo… All of the above                         1
    ## 11 Home virtual assitants (Goo… Engineers that build the algorithm       1
    ## 12 Home virtual assitants (Goo… No opinion                               1
    ## 13 Home virtual assitants (Goo… Users themselves                         1
    ## 14 VR (Oculus rift)             Government - Lack of regulations         1
    ## 15 VR (Oculus rift)             No opinion                               1
    ## 16 VR (Oculus rift)             The company's miss as well as users…     1
    ## 17 Wearables (fitbit, Apple wa… Government - Lack of regulations         1
    ## 18 Wearables (fitbit, Apple wa… Policies that govern  platforms lik…     1

## Count Likert responses
