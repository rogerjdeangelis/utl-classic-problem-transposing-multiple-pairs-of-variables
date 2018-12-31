# utl-classic-problem-transposing-multiple-pairs-of-variables
Classic problem transposing multiple pairs of variables

    SAS Forum: Classic problem transposing multiple groups of variables

    github
    https://tinyurl.com/y7y9736x
    https://github.com/rogerjdeangelis/utl-classic-problem-transposing-multiple-pairs-of-variables

    Seven techniques
    https://tinyurl.com/yd7gawmn
    https://github.com/rogerjdeangelis/utl-classic-problem-with-proc-transpose-and-mutiple-variables-seven-solutions

    SAS Forum
    https://tinyurl.com/ybqtyuq6
    https://communities.sas.com/t5/SAS-Programming/How-to-copy-multiple-variables-with-transpose/m-p/523771

    other transpose repos
    https://tinyurl.com/y96alxns
    https://github.com/rogerjdeangelis?utf8=%E2%9C%93&tab=repositories&q=transpose+in%3Aname&type=&language=


    macros
    https://tinyurl.com/y9nfugth
    https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories


    Transpose macro by (classic transpose limitation overcome by)

     AUTHORS: Arthur Tabachneck, Xia Ke Shan, Robert Virgile and Joe Whitehurst
     CREATED: January 20, 2013
     MODIFIED: September 4, 2014
     MODIFIED: September 15, 2017


    INPUT
    =====

    * make data;
    data have;
      input block type $ count;
    cards4;
    2 A 10
    6 B 15
    6 C 5
    8 D 25
    8 E 32
    9 E 12
    ;;;;
    run;

                              |
    WORK.HAVE total obs=6     |
                              |
      BLOCK    TYPE    COUNT  |  BLOCK    TYPE_1    COUNT_1    TYPE_2    COUNT_2
                              |
        2       A        10   |    2        A          10                    .
                              |
        6       B        15   |
        6       C         5   |    6        B          15        C           5

        8       D        25   |   ..
        8       E        32   |
        9       E        12   |


    EXAMPLE OUTPUT
    ----------------

     WORK.WANT total obs=4

      BLOCK    TYPE_1    COUNT_1    TYPE_2    COUNT_2

        2        A          10                    .
        6        B          15        C           5
        8        D          25        E          32
        9        E          12                    .


    PROCESS
    =======

    %utl_transpose(data=have, out=want, by=block, delimiter=_,var=type count)

