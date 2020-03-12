Network Analysis
================

## Coronavirus (and HW)

Here we analyze infection data for the 2019 novel Coronavirus COVID-19
(2019-nCoV) epidemic. The raw data is pulled from the Johns Hopkins
University Center for Systems Science and Engineering (JHU CCSE)
Coronavirus repository.

A CSV file is available here
<https://github.com/RamiKrispin/coronavirus-csv>

``` r
url <- "https://tinyurl.com/COVID-2019"
virus <- read.csv(url)

tail(virus)
```

    ##      Province.State Country.Region     Lat     Long       date cases      type
    ## 2675         Shanxi Mainland China 37.5777 112.2922 2020-03-03     5 recovered
    ## 2676        Sichuan Mainland China 30.6171 102.7103 2020-03-03     8 recovered
    ## 2677        Tianjin Mainland China 39.3054 117.3230 2020-03-03    13 recovered
    ## 2678       Xinjiang Mainland China 41.1129  85.2401 2020-03-03     2 recovered
    ## 2679         Yunnan Mainland China 24.9740 101.4870 2020-03-03     1 recovered
    ## 2680       Zhejiang Mainland China 29.1832 120.0934 2020-03-03    24 recovered

> Q1. How many total cases around the world?

``` r
total <- sum(virus$cases)
total
```

    ## [1] 144233

> Q2. How many deaths linked to infected cases have there been?

``` r
table(virus$type)
```

    ## 
    ## confirmed     death recovered 
    ##      1461       194      1025

``` r
inds <- virus$type == "death"
virus[inds, ]
```

    ##                    Province.State Country.Region       Lat      Long       date
    ## 30                          Hubei Mainland China  30.97560  112.2707 2020-01-22
    ## 60                          Hebei Mainland China  38.04280  114.5149 2020-01-23
    ## 94                   Heilongjiang Mainland China  47.86200  127.7615 2020-01-24
    ## 95                          Hubei Mainland China  30.97560  112.2707 2020-01-24
    ## 133                         Hubei Mainland China  30.97560  112.2707 2020-01-25
    ## 178                         Henan Mainland China  33.88202  113.6140 2020-01-26
    ## 179                         Hubei Mainland China  30.97560  112.2707 2020-01-26
    ## 180                      Shanghai Mainland China  31.20200  121.4491 2020-01-26
    ## 222                       Beijing Mainland China  40.18240  116.4142 2020-01-27
    ## 223                        Hainan Mainland China  19.19590  109.7453 2020-01-27
    ## 224                         Hubei Mainland China  30.97560  112.2707 2020-01-27
    ## 266                         Hubei Mainland China  30.97560  112.2707 2020-01-28
    ## 305                         Henan Mainland China  33.88202  113.6140 2020-01-29
    ## 306                       Sichuan Mainland China  30.61710  102.7103 2020-01-29
    ## 357                  Heilongjiang Mainland China  47.86200  127.7615 2020-01-30
    ## 358                         Hubei Mainland China  30.97560  112.2707 2020-01-30
    ## 413                         Hubei Mainland China  30.97560  112.2707 2020-01-31
    ## 468                     Chongqing Mainland China  30.05720  107.8740 2020-02-01
    ## 469                         Hubei Mainland China  30.97560  112.2707 2020-02-01
    ## 525                                  Philippines  13.00000  122.0000 2020-02-02
    ## 526                     Chongqing Mainland China  30.05720  107.8740 2020-02-02
    ## 527                         Hubei Mainland China  30.97560  112.2707 2020-02-02
    ## 580                         Hubei Mainland China  30.97560  112.2707 2020-02-03
    ## 638                     Hong Kong      Hong Kong  22.30000  114.2000 2020-02-04
    ## 639                         Hubei Mainland China  30.97560  112.2707 2020-02-04
    ## 695                       Guizhou Mainland China  26.81540  106.8748 2020-02-05
    ## 696                         Hubei Mainland China  30.97560  112.2707 2020-02-05
    ## 697                       Tianjin Mainland China  39.30540  117.3230 2020-02-05
    ## 758                  Heilongjiang Mainland China  47.86200  127.7615 2020-02-06
    ## 759                         Hubei Mainland China  30.97560  112.2707 2020-02-06
    ## 827                     Guangdong Mainland China  23.34170  113.4244 2020-02-07
    ## 828                        Hainan Mainland China  19.19590  109.7453 2020-02-07
    ## 829                         Henan Mainland China  33.88202  113.6140 2020-02-07
    ## 830                         Hubei Mainland China  30.97560  112.2707 2020-02-07
    ## 831                         Jilin Mainland China  43.66610  126.1923 2020-02-07
    ## 895                       Beijing Mainland China  40.18240  116.4142 2020-02-08
    ## 896                         Gansu Mainland China  36.06110  103.8343 2020-02-08
    ## 897                  Heilongjiang Mainland China  47.86200  127.7615 2020-02-08
    ## 898                         Henan Mainland China  33.88202  113.6140 2020-02-08
    ## 899                         Hubei Mainland China  30.97560  112.2707 2020-02-08
    ## 900                         Hunan Mainland China  27.61040  111.7088 2020-02-08
    ## 965                         Anhui Mainland China  31.82570  117.2264 2020-02-09
    ## 966                         Gansu Mainland China  36.06110  103.8343 2020-02-09
    ## 967                       Guangxi Mainland China  23.82980  108.7881 2020-02-09
    ## 968                        Hainan Mainland China  19.19590  109.7453 2020-02-09
    ## 969                         Hebei Mainland China  38.04280  114.5149 2020-02-09
    ## 970                  Heilongjiang Mainland China  47.86200  127.7615 2020-02-09
    ## 971                         Henan Mainland China  33.88202  113.6140 2020-02-09
    ## 972                         Hubei Mainland China  30.97560  112.2707 2020-02-09
    ## 973                      Shandong Mainland China  36.34270  118.1498 2020-02-09
    ## 1037                        Anhui Mainland China  31.82570  117.2264 2020-02-10
    ## 1038                 Heilongjiang Mainland China  47.86200  127.7615 2020-02-10
    ## 1039                        Hubei Mainland China  30.97560  112.2707 2020-02-10
    ## 1040                      Jiangxi Mainland China  27.61400  115.7221 2020-02-10
    ## 1101                        Anhui Mainland China  31.82570  117.2264 2020-02-11
    ## 1102                      Beijing Mainland China  40.18240  116.4142 2020-02-11
    ## 1103                    Chongqing Mainland China  30.05720  107.8740 2020-02-11
    ## 1104                 Heilongjiang Mainland China  47.86200  127.7615 2020-02-11
    ## 1105                        Henan Mainland China  33.88202  113.6140 2020-02-11
    ## 1106                        Hubei Mainland China  30.97560  112.2707 2020-02-11
    ## 1107                      Tianjin Mainland China  39.30540  117.3230 2020-02-11
    ## 1174                       Hainan Mainland China  19.19590  109.7453 2020-02-12
    ## 1175                        Henan Mainland China  33.88202  113.6140 2020-02-12
    ## 1176                        Hunan Mainland China  27.61040  111.7088 2020-02-12
    ## 1177                     Liaoning Mainland China  41.29560  122.6085 2020-02-12
    ## 1178                     Shandong Mainland China  36.34270  118.1498 2020-02-12
    ## 1254                                       Japan  36.00000  138.0000 2020-02-13
    ## 1255                        Anhui Mainland China  31.82570  117.2264 2020-02-13
    ## 1256                    Chongqing Mainland China  30.05720  107.8740 2020-02-13
    ## 1257                    Guangdong Mainland China  23.34170  113.4244 2020-02-13
    ## 1258                      Guangxi Mainland China  23.82980  108.7881 2020-02-13
    ## 1259                        Hebei Mainland China  38.04280  114.5149 2020-02-13
    ## 1260                 Heilongjiang Mainland China  47.86200  127.7615 2020-02-13
    ## 1261                        Henan Mainland China  33.88202  113.6140 2020-02-13
    ## 1262                        Hubei Mainland China  30.97560  112.2707 2020-02-13
    ## 1263                      Tianjin Mainland China  39.30540  117.3230 2020-02-13
    ## 1264                     Xinjiang Mainland China  41.11290   85.2401 2020-02-13
    ## 1332                        Anhui Mainland China  31.82570  117.2264 2020-02-14
    ## 1333                    Chongqing Mainland China  30.05720  107.8740 2020-02-14
    ## 1334                 Heilongjiang Mainland China  47.86200  127.7615 2020-02-14
    ## 1335                        Henan Mainland China  33.88202  113.6140 2020-02-14
    ## 1336                        Hubei Mainland China  30.97560  112.2707 2020-02-14
    ## 1396                                      France  47.00000    2.0000 2020-02-15
    ## 1397                      Beijing Mainland China  40.18240  116.4142 2020-02-15
    ## 1398                        Henan Mainland China  33.88202  113.6140 2020-02-15
    ## 1399                        Hubei Mainland China  30.97560  112.2707 2020-02-15
    ## 1471                        Hubei Mainland China  30.97560  112.2707 2020-02-16
    ## 1472                        Hunan Mainland China  27.61040  111.7088 2020-02-16
    ## 1473                      Sichuan Mainland China  30.61710  102.7103 2020-02-16
    ## 1474                       Taiwan         Taiwan  23.70000  121.0000 2020-02-16
    ## 1541                    Guangdong Mainland China  23.34170  113.4244 2020-02-17
    ## 1542                        Henan Mainland China  33.88202  113.6140 2020-02-17
    ## 1543                        Hubei Mainland China  30.97560  112.2707 2020-02-17
    ## 1602                      Guizhou Mainland China  26.81540  106.8748 2020-02-18
    ## 1603                        Hebei Mainland China  38.04280  114.5149 2020-02-18
    ## 1604                        Henan Mainland China  33.88202  113.6140 2020-02-18
    ## 1605                        Hubei Mainland China  30.97560  112.2707 2020-02-18
    ## 1606                        Hunan Mainland China  27.61040  111.7088 2020-02-18
    ## 1607                     Shandong Mainland China  36.34270  118.1498 2020-02-18
    ## 1668                                        Iran  32.00000   53.0000 2020-02-19
    ## 1669                    Guangdong Mainland China  23.34170  113.4244 2020-02-19
    ## 1670                 Heilongjiang Mainland China  47.86200  127.7615 2020-02-19
    ## 1671                    Hong Kong      Hong Kong  22.30000  114.2000 2020-02-19
    ## 1672                        Hubei Mainland China  30.97560  112.2707 2020-02-19
    ## 1673                     Shanghai Mainland China  31.20200  121.4491 2020-02-19
    ## 1674                       Yunnan Mainland China  24.97400  101.4870 2020-02-19
    ## 1734                                 South Korea  36.00000  128.0000 2020-02-20
    ## 1735                    Chongqing Mainland China  30.05720  107.8740 2020-02-20
    ## 1736 Diamond Princess cruise ship         Others  35.44370  139.6380 2020-02-20
    ## 1737                       Fujian Mainland China  26.07890  117.9874 2020-02-20
    ## 1738                        Hebei Mainland China  38.04280  114.5149 2020-02-20
    ## 1739                        Hubei Mainland China  30.97560  112.2707 2020-02-20
    ## 1740                      Shaanxi Mainland China  35.19170  108.8701 2020-02-20
    ## 1741                     Shandong Mainland China  36.34270  118.1498 2020-02-20
    ## 1742                       Yunnan Mainland China  24.97400  101.4870 2020-02-20
    ## 1743                     Zhejiang Mainland China  29.18320  120.0934 2020-02-20
    ## 1805                                        Iran  32.00000   53.0000 2020-02-21
    ## 1806                                       Italy  43.00000   12.0000 2020-02-21
    ## 1807                                 South Korea  36.00000  128.0000 2020-02-21
    ## 1869                                        Iran  32.00000   53.0000 2020-02-22
    ## 1870                                       Italy  43.00000   12.0000 2020-02-22
    ## 1871                        Hebei Mainland China  38.04280  114.5149 2020-02-22
    ## 1872                        Hubei Mainland China  30.97560  112.2707 2020-02-22
    ## 1873                     Shanghai Mainland China  31.20200  121.4491 2020-02-22
    ## 1874                     Xinjiang Mainland China  41.11290   85.2401 2020-02-22
    ## 1919                                        Iran  32.00000   53.0000 2020-02-23
    ## 1920                                       Italy  43.00000   12.0000 2020-02-23
    ## 1921                                 South Korea  36.00000  128.0000 2020-02-23
    ## 1922 Diamond Princess cruise ship         Others  35.44370  139.6380 2020-02-23
    ## 1923                    Guangdong Mainland China  23.34170  113.4244 2020-02-23
    ## 1924                       Hainan Mainland China  19.19590  109.7453 2020-02-23
    ## 1985                                        Iran  32.00000   53.0000 2020-02-24
    ## 1986                                       Italy  43.00000   12.0000 2020-02-24
    ## 1987                                 South Korea  36.00000  128.0000 2020-02-24
    ## 1988                        Hubei Mainland China  30.97560  112.2707 2020-02-24
    ## 1989                     Shandong Mainland China  36.34270  118.1498 2020-02-24
    ## 2048                                        Iran  32.00000   53.0000 2020-02-25
    ## 2049                                       Italy  43.00000   12.0000 2020-02-25
    ## 2050                                 South Korea  36.00000  128.0000 2020-02-25
    ## 2051                    Guangdong Mainland China  23.34170  113.4244 2020-02-25
    ## 2052                        Hubei Mainland China  30.97560  112.2707 2020-02-25
    ## 2053                     Shandong Mainland China  36.34270  118.1498 2020-02-25
    ## 2121                                      France  47.00000    2.0000 2020-02-26
    ## 2122                                        Iran  32.00000   53.0000 2020-02-26
    ## 2123                                       Italy  43.00000   12.0000 2020-02-26
    ## 2124                                       Japan  36.00000  138.0000 2020-02-26
    ## 2125                                 South Korea  36.00000  128.0000 2020-02-26
    ## 2126 Diamond Princess cruise ship         Others  35.44370  139.6380 2020-02-26
    ## 2127                        Hubei Mainland China  30.97560  112.2707 2020-02-26
    ## 2195                                        Iran  32.00000   53.0000 2020-02-27
    ## 2196                                       Italy  43.00000   12.0000 2020-02-27
    ## 2197                                       Japan  36.00000  138.0000 2020-02-27
    ## 2198                                 South Korea  36.00000  128.0000 2020-02-27
    ## 2199                      Beijing Mainland China  40.18240  116.4142 2020-02-27
    ## 2200                 Heilongjiang Mainland China  47.86200  127.7615 2020-02-27
    ## 2201                        Henan Mainland China  33.88202  113.6140 2020-02-27
    ## 2202                        Hubei Mainland China  30.97560  112.2707 2020-02-27
    ## 2269                                        Iran  32.00000   53.0000 2020-02-28
    ## 2270                                       Italy  43.00000   12.0000 2020-02-28
    ## 2271                      Beijing Mainland China  40.18240  116.4142 2020-02-28
    ## 2272 Diamond Princess cruise ship         Others  35.44370  139.6380 2020-02-28
    ## 2273                        Hubei Mainland China  30.97560  112.2707 2020-02-28
    ## 2274                     Xinjiang Mainland China  41.11290   85.2401 2020-02-28
    ## 2358                                        Iran  32.00000   53.0000 2020-02-29
    ## 2359                                       Italy  43.00000   12.0000 2020-02-29
    ## 2360                                       Japan  36.00000  138.0000 2020-02-29
    ## 2361                                 South Korea  36.00000  128.0000 2020-02-29
    ## 2362                      Beijing Mainland China  40.18240  116.4142 2020-02-29
    ## 2363                        Henan Mainland China  33.88202  113.6140 2020-02-29
    ## 2364                        Hubei Mainland China  30.97560  112.2707 2020-02-29
    ## 2365              King County, WA             US  47.60620 -122.3321 2020-02-29
    ## 2447                                        Iran  32.00000   53.0000 2020-03-01
    ## 2448                                       Italy  43.00000   12.0000 2020-03-01
    ## 2449                                       Japan  36.00000  138.0000 2020-03-01
    ## 2450                                 South Korea  36.00000  128.0000 2020-03-01
    ## 2451                                    Thailand  15.00000  101.0000 2020-03-01
    ## 2452                        Henan Mainland China  33.88202  113.6140 2020-03-01
    ## 2453                        Hubei Mainland China  30.97560  112.2707 2020-03-01
    ## 2454            Western Australia      Australia -31.95050  115.8605 2020-03-01
    ## 2543                                      France  47.00000    2.0000 2020-03-02
    ## 2544                                        Iran  32.00000   53.0000 2020-03-02
    ## 2545                                       Italy  43.00000   12.0000 2020-03-02
    ## 2546                                 South Korea  36.00000  128.0000 2020-03-02
    ## 2547                        Hubei Mainland China  30.97560  112.2707 2020-03-02
    ## 2548              King County, WA             US  47.60620 -122.3321 2020-03-02
    ## 2549         Snohomish County, WA             US  48.03300 -121.8339 2020-03-02
    ## 2639                                      France  47.00000    2.0000 2020-03-03
    ## 2640                                        Iran  32.00000   53.0000 2020-03-03
    ## 2641                                       Italy  43.00000   12.0000 2020-03-03
    ## 2642                                  San Marino  43.94240   12.4578 2020-03-03
    ## 2643                                       Spain  40.00000   -4.0000 2020-03-03
    ## 2644                        Hubei Mainland China  30.97560  112.2707 2020-03-03
    ## 2645               Inner Mongolia Mainland China  44.09350  113.9448 2020-03-03
    ## 2646              King County, WA             US  47.60620 -122.3321 2020-03-03
    ##      cases  type
    ## 30      17 death
    ## 60       1 death
    ## 94       1 death
    ## 95       7 death
    ## 133     16 death
    ## 178      1 death
    ## 179     12 death
    ## 180      1 death
    ## 222      1 death
    ## 223      1 death
    ## 224     24 death
    ## 266     49 death
    ## 305      1 death
    ## 306      1 death
    ## 357      1 death
    ## 358     37 death
    ## 413     42 death
    ## 468      1 death
    ## 469     45 death
    ## 525      1 death
    ## 526      1 death
    ## 527    101 death
    ## 580     64 death
    ## 638      1 death
    ## 639     65 death
    ## 695      1 death
    ## 696     70 death
    ## 697      1 death
    ## 758      1 death
    ## 759     69 death
    ## 827      1 death
    ## 828      1 death
    ## 829      1 death
    ## 830     81 death
    ## 831      1 death
    ## 895      1 death
    ## 896      1 death
    ## 897      2 death
    ## 898      1 death
    ## 899     81 death
    ## 900      1 death
    ## 965      1 death
    ## 966      1 death
    ## 967      1 death
    ## 968      1 death
    ## 969      1 death
    ## 970      1 death
    ## 971      2 death
    ## 972     91 death
    ## 973      1 death
    ## 1037     2 death
    ## 1038     1 death
    ## 1039   103 death
    ## 1040     1 death
    ## 1101     1 death
    ## 1102     1 death
    ## 1103     1 death
    ## 1104     1 death
    ## 1105     1 death
    ## 1106    94 death
    ## 1107     1 death
    ## 1174     1 death
    ## 1175     1 death
    ## 1176     1 death
    ## 1177     1 death
    ## 1178     1 death
    ## 1254     1 death
    ## 1255     1 death
    ## 1256     1 death
    ## 1257     1 death
    ## 1258     1 death
    ## 1259     1 death
    ## 1260     1 death
    ## 1261     2 death
    ## 1262   242 death
    ## 1263     1 death
    ## 1264     1 death
    ## 1332     1 death
    ## 1333     1 death
    ## 1334     2 death
    ## 1335     1 death
    ## 1336   147 death
    ## 1396     1 death
    ## 1397     1 death
    ## 1398     2 death
    ## 1399   139 death
    ## 1471   100 death
    ## 1472     1 death
    ## 1473     2 death
    ## 1474     1 death
    ## 1541     2 death
    ## 1542     3 death
    ## 1543    93 death
    ## 1602     1 death
    ## 1603     1 death
    ## 1604     3 death
    ## 1605   132 death
    ## 1606     1 death
    ## 1607     1 death
    ## 1668     2 death
    ## 1669     1 death
    ## 1670     1 death
    ## 1671     1 death
    ## 1672   108 death
    ## 1673     1 death
    ## 1674     1 death
    ## 1734     1 death
    ## 1735     1 death
    ## 1736     2 death
    ## 1737     1 death
    ## 1738     1 death
    ## 1739   115 death
    ## 1740     1 death
    ## 1741     1 death
    ## 1742     1 death
    ## 1743     1 death
    ## 1805     2 death
    ## 1806     1 death
    ## 1807     1 death
    ## 1869     1 death
    ## 1870     1 death
    ## 1871     1 death
    ## 1872   202 death
    ## 1873     1 death
    ## 1874     1 death
    ## 1919     3 death
    ## 1920     1 death
    ## 1921     4 death
    ## 1922     1 death
    ## 1923     1 death
    ## 1924     1 death
    ## 1985     4 death
    ## 1986     4 death
    ## 1987     2 death
    ## 1988   149 death
    ## 1989     1 death
    ## 2048     4 death
    ## 2049     3 death
    ## 2050     2 death
    ## 2051     1 death
    ## 2052    68 death
    ## 2053     1 death
    ## 2121     1 death
    ## 2122     3 death
    ## 2123     2 death
    ## 2124     1 death
    ## 2125     2 death
    ## 2126     1 death
    ## 2127    52 death
    ## 2195     7 death
    ## 2196     5 death
    ## 2197     2 death
    ## 2198     1 death
    ## 2199     1 death
    ## 2200     1 death
    ## 2201     1 death
    ## 2202    26 death
    ## 2269     8 death
    ## 2270     4 death
    ## 2271     2 death
    ## 2272     2 death
    ## 2273    41 death
    ## 2274     1 death
    ## 2358     9 death
    ## 2359     8 death
    ## 2360     1 death
    ## 2361     3 death
    ## 2362     1 death
    ## 2363     1 death
    ## 2364    45 death
    ## 2365     1 death
    ## 2447    11 death
    ## 2448     5 death
    ## 2449     1 death
    ## 2450     1 death
    ## 2451     1 death
    ## 2452     1 death
    ## 2453    34 death
    ## 2454     1 death
    ## 2543     1 death
    ## 2544    12 death
    ## 2545    18 death
    ## 2546    11 death
    ## 2547    42 death
    ## 2548     4 death
    ## 2549     1 death
    ## 2639     1 death
    ## 2640    11 death
    ## 2641    27 death
    ## 2642     1 death
    ## 2643     1 death
    ## 2644    32 death
    ## 2645     1 death
    ## 2646     1 death

``` r
totaldeaths <- sum(virus[inds, "cases"])
totaldeaths
```

    ## [1] 3160

> Q3. What is the overall dealth rate?

``` r
round(totaldeaths/total * 100, 2)
```

    ## [1] 2.19

> Q4. What is the death rate in Mainland China?

``` r
totalchina <- virus$Country.Region == "Mainland China"
tc<- sum(virus[totalchina, "cases"])

chinadeath <- virus$type == "death" & virus$Country.Region == "Mainland China"
cd<- sum(virus[chinadeath, "cases" ])

round(cd/tc * 100, 2)
```

    ## [1] 2.26

> Q5. What is the death rate in Italy, Iran, and the US?

``` r
#Italy

totalitaly <- virus$Country.Region == "Italy"
ti<- sum(virus[totalitaly, "cases"])

italydeath <- virus$type == "death" & virus$Country.Region == "Italy"
id<- sum(virus[italydeath, "cases" ])

round(id/ti * 100, 2)
```

    ## [1] 2.88

``` r
#Iran

totaliran <- virus$Country.Region == "Iran"
tir<- sum(virus[totaliran, "cases"])

irandeath <- virus$type == "death" & virus$Country.Region == "Iran"
ird<- sum(virus[irandeath, "cases" ])

round(ird/tir * 100, 2)
```

    ## [1] 2.85

``` r
#US

totalUS <- virus$Country.Region == "US"
tUS<- sum(virus[totalUS, "cases"])

USdeath <- virus$type == "death" & virus$Country.Region == "US"
USd<- sum(virus[USdeath, "cases" ])

round(USd/tUS * 100, 2)
```

    ## [1] 5.11
