---
title: "scte65scan - need help implementing"
date: 2009-12-09
forum: Mythbuntu
---

### Post by B34N on 2009-12-09
I'm a Comcast subscriber in NJ.  I don't have any QAM TVs.  I only have two QAM tuners in my Mythbuntu 9.10 box.  I finally noticed that if I assign all of those conflicting channels to another channel that I actually have many more channels than I had thought.  Unfortunately the mapping of the channels is incorrect and they don't match up to Schedules Direct.  My understanding is that scte65scan is the tool to do what I need.  Is that correct?

I read the instructions at [http://www.mythtv.org/wiki/Comcast_Users_And_scte65scan](http://www.mythtv.org/wiki/Comcast_Users_And_scte65scan) but since I'm a beginner, I got lost very quickly.

I don't know my VCT_ID and it is not listed in the table.  When I ran scte65scan it did show me a few VCT_IDs, but I'm not able to determine which one I should be using.  I'm not sure what I should be looking for when they said "it can also sometimes be found by inspection through an examination of the text-mode output of scte65scan"  My thought was to try the process with each of the VCT_IDS to determine which was correct.  Does this make sense?

I then tried "./scte65scan -f3 -V 3010 itfile > vct.sql" which generated the vct.sql file but gave me an error "itfile: No such file or directory".  Am I supposed to replace itfile with something, am I missing a file or am I being to literal?

I did try the next step and did "mysql mythconverg < vct.sql" but got back "ERROR 1045 (28000): Access denied for user 'mark'@'localhost' (using password: NO)"  What am I doing wrong?  Do I need to execute as a different user?  I tried sudo and got the same response.

Will the scte65scan instructions fix the channel mappings or will I need to do another channel scan or fetch channels from listing source?  I have yet to get fetch channels from listing source to setup the channels for me.

Thank you!

---

### Post by B34N on 2009-12-09
> **st8ofmi9d said:**
> 
I don't know my VCT_ID and it is not listed in the table.  When I ran scte65scan it did show me a few VCT_IDs, but I'm not able to determine which one I should be using.  I'm not sure what I should be looking for when they said "it can also sometimes be found by inspection through an examination of the text-mode output of scte65scan"

I'm fairly confident that I figured out my VCT_ID by comparing the output from scte65scan to what Comcast has as their show listings for my zip code.

---

### Post by B34N on 2009-12-13
I got it working.  I just needed to specify the username was root in mysql.  For all of those with Comcast, this is the best way that I know of to map channels for their guides.

---

### Post by yonkiman on 2009-12-19
How did you figure it out?  I managed to compile scte65scan on my Mythbuntu 9.10 0.22 system, but whenever I run it, I get nothing...

$ ./scte65scan
PID 0x1ffc timeout

$ ./scte65scan -f3 -V 3001 itfile > debug.txt
itfile: No such file or directory
PID 0x1ffc timeout

$ ./scte65scan -f3 -V 3001 > debug.txt
PID 0x1ffc timeout

I have NO IDEA what I am supposed to do.  But I'm in San Jose and would like to get my Comcast clearqam, so any help is much appreciated!

---

### Post by B34N on 2009-12-19
> **yonkiman said:**
> How did you figure it out?

I did nothing special.  I'm running the same version of Mythbuntu and I'm such a newbie that I wouldn't know how to do more than type make to compile it.   Did you have any troubles compiling it?  What tuner card are you using? I have two in my box and I just realized that I never even specified which tuner to use.

---

### Post by yonkiman on 2009-12-19
> **st8ofmi9d said:**
> Did you have any troubles compiling it?  What tuner card are you using? I have two in my box and I just realized that I never even specified which tuner to use.

No trouble compiling it.

But now that I have it, all I get is the above error messages.  I have no idea what command lines to type, or even exactly what it's supposed to do.  I also have two tuner cards, one attached to Comcast and the other to an OTA antenna.

---

### Post by B34N on 2009-12-19
> **yonkiman said:**
> I have no idea what command lines to type, or even exactly what it's supposed to do.  I also have two tuner cards, one attached to Comcast and the other to an OTA antenna.
I'm won't be near my Mythbuntu box until after Christmas.  When you run scte65scan without any arguments, you should get something like this:
```
VCT_ID 3018 (0x0bca), version 13
  VC CD.PROG M# NAME
====================
   2   82.1   4 C-SPAN -c-span
   3   80.1   4 KYW    -kyw-3
   4   82.10  4 QVC    -qvc
   5   80.6   4 WTXF   -wtxf-29
   6   80.2   4 WPVI   -wpvi-6
   7  106.2   4 WABC   -WABC(7)-NY
   8   80.12  4 CNPH   -comcast network
   9   80.5   4 WPHL   -wphl-17
  10   80.3   4 WCAU   -wcau-10
  11   82.9   4 HSN    -home shopping network
  12   80.4   4 WHYY   -whyy-12
  13  106.4   4 WNET   -WNET-13
  14   80.8   4 WPSG   -wpsg-57
  15   80.11  4 WFMZ   -wfmz-69
  16   80.10  4 WUVP   -wuvp-65
  17   80.9   4 WPPX   -wppx-61
  18   80.7   4 WGTW   -wgtw-48
  19  118.1   4 LOCAL  -CH19
  20   79.12  4 WYBE   -WYBE-35
  21   79.8   4 WBPH   -wbph-60
  22   79.10  4 WWSI   -wwsi-62
  23   79.3   4 WNJS   -wnjs-23
  24  118.3   4 LOCAL  -CH24TREN & 16LAMB
  26  118.4   4 MERCER COUNTY COLLEGE
  27   79.6   4 WMCN   -wmcn-53 (formally wwac)
  40   87.6   4 TWC    -the weather channel
  47   88.4   4 CNBC   -cnbc
  53   82.8   4 GOLF   -golf channel
  57   82.12  4 HN     -headline news
  60   90.3   4 HGTV   -HGTV
  63   90.6   4 FOOD   -food network
  70  101.6   4 NICK   -nickelodeon
  95  118.2   4 LOCAL  -CH95 TRENTON
 104   82.2   4 C-SPAN2-c-span 2
 136  101.5   4 DISNEY CHANNEL
 190  118.10  4 LEASED -LEASED ACCESS
 246  113.4   4 WPVI-WC
 248  113.5   4 WCAU-DT- WCAU_DT WEATHER
 249  113.6   4 UNISPRT-  Universal Sports
 250  106.6   4 WNYW   -WNYW-5
 251  114.4   4 WFPA - TELEFUTURA
 252   30.3   4 THIS   - WPHL-DT THIS TV
 253  106.3   4 WNBC   -WNBC(4)-NY
 254   87.12  4 WPIX   -WPIX-11
 255   79.9   4 WWOR   -WWOR-9
 256  106.1   4 WCBS  -WCBS(2)-NY
 257  117.3   4 WHYY2
 258  117.4   4 WHYY3
 259   20.3   4 WNETKID-WNET Kids 13
 260   20.2   4 WNETVME -WNET V-ME
 261   79.3   4 WNJS   -wnjs-23
 262  103.2   4 WNJS-JV
 264   13.6   4 WYBEM - MHZ WORLDVIEW
 265   13.5   4 WYBEG - GLOBAL MIND
 287  116.11  4 DAYSTAR-Daystar
 291  114.7   4 EWTN   -ewtn
 612  114.4   4 WFPA - TELEFUTURA
 965  118.11  4 GAVEL  -GAVEL 2 GAVEL/JEWELRY TV
1075   80.51  4 TVWorks InBand Channel



VCT_ID 3027 (0x0bd3), version 13
  VC CD.PROG M# NAME
====================
   2   82.1   4 C-SPAN -c-span
   3   80.1   4 KYW    -kyw-3
   4   82.10  4 QVC    -qvc
   5   80.6   4 WTXF   -wtxf-29
   6   80.2   4 WPVI   -wpvi-6
   7  106.2   4 WABC   -WABC(7)-NY
   8   80.12  4 CNPH   -comcast network
   9   80.5   4 WPHL   -wphl-17
  10   80.3   4 WCAU   -wcau-10
  11   82.9   4 HSN    -home shopping network
  12   80.4   4 WHYY   -whyy-12
  13  106.4   4 WNET   -WNET-13
  14   80.8   4 WPSG   -wpsg-57
  15   80.11  4 WFMZ   -wfmz-69
  16   80.10  4 WUVP   -wuvp-65
  17   80.9   4 WPPX   -wppx-61
  18   80.7   4 WGTW   -wgtw-48
  19  118.1   4 LOCAL  -CH19
  20   79.12  4 WYBE   -WYBE-35
  21   79.8   4 WBPH   -wbph-60
  22   79.10  4 WWSI   -wwsi-62
  23   79.3   4 WNJS   -wnjs-23
  24  118.3   4 LOCAL  -CH24TREN & 16LAMB
  26  118.4   4 MERCER COUNTY COLLEGE
  27   79.6   4 WMCN   -wmcn-53 (formally wwac)
  95  118.2   4 LOCAL  -CH95 TRENTON
 104   82.2   4 C-SPAN2-c-span 2
 136  101.5   4 DISNEY CHANNEL
 162   90.10  4 G4TTV  -g4 tech tv
 169   88.5   4 TCM    -turner classic movies
 190  118.10  4 LEASED -LEASED ACCESS
 246  113.4   4 WPVI-WC
 248  113.5   4 WCAU-DT- WCAU_DT WEATHER
 249  113.6   4 UNISPRT-  Universal Sports
 250  106.6   4 WNYW   -WNYW-5
 251  114.4   4 WFPA - TELEFUTURA
 252   30.3   4 THIS   - WPHL-DT THIS TV
 253  106.3   4 WNBC   -WNBC(4)-NY
 254   87.12  4 WPIX   -WPIX-11
 255   79.9   4 WWOR   -WWOR-9
 256  106.1   4 WCBS  -WCBS(2)-NY
 257  117.3   4 WHYY2
 258  117.4   4 WHYY3
 259   20.3   4 WNETKID-WNET Kids 13
 260   20.2   4 WNETVME -WNET V-ME
 261   79.3   4 WNJS   -wnjs-23
 262  103.2   4 WNJS-JV
 264   13.6   4 WYBEM - MHZ WORLDVIEW
 265   13.5   4 WYBEG - GLOBAL MIND
 282  119.8   4 ACN    -ACN
 291  114.7   4 EWTN   -ewtn
 612  114.4   4 WFPA - TELEFUTURA
 965  118.11  4 GAVEL  -GAVEL 2 GAVEL/JEWELRY TV
1075   80.51  4 TVWorks InBand Channel



VCT_ID 3006 (0x0bbe), version 13
  VC CD.PROG M# NAME
====================
   2   82.1   4 C-SPAN -c-span
   3   80.1   4 KYW    -kyw-3
   4   82.10  4 QVC    -qvc
   5   80.6   4 WTXF   -wtxf-29
   6   80.2   4 WPVI   -wpvi-6
   7  106.2   4 WABC   -WABC(7)-NY
   8   80.12  4 CNPH   -comcast network
   9   80.5   4 WPHL   -wphl-17
  10   80.3   4 WCAU   -wcau-10
  11   82.9   4 HSN    -home shopping network
  12   80.4   4 WHYY   -whyy-12
  13  106.4   4 WNET   -WNET-13
  14   80.8   4 WPSG   -wpsg-57
  15   80.11  4 WFMZ   -wfmz-69
  16   80.10  4 WUVP   -wuvp-65
  17   80.9   4 WPPX   -wppx-61
  18   80.7   4 WGTW   -wgtw-48
  19  118.1   4 LOCAL  -CH19
  20   79.12  4 WYBE   -WYBE-35
  21   79.8   4 WBPH   -wbph-60
  22   79.10  4 WWSI   -wwsi-62
  23   79.3   4 WNJS   -wnjs-23
  24  118.3   4 LOCAL  -CH24TREN & 16LAMB
  26  118.4   4 MERCER COUNTY COLLEGE
  27   79.6   4 WMCN   -wmcn-53 (formally wwac)
  31   88.9   4 ESPN   -espn
  32   88.10  4 ESPN2  -espn2
  33   90.12  4 VERSUS -VERSUS (Formerly OLN)
  34   87.9   4 YES    -YES
  35   88.11  4 WTBS   -wtbs
  36   90.1   4 SPIKE  -tnn
  37   88.3   4 TVLND  -TV LAND
  38  101.2   4 TOON   -cartoon network
  39   90.2   4 BRAVO  -BRAVO
  40   87.6   4 TWC    -the weather channel
  41   87.1   4 FX     -f/x
  42  101.9   4 DIS    -discovery channel east
  43  101.1   4 BET    -bet
  44   87.4   4 A&E    -arts & entertainment
  45   87.10  4 MSG    -MSG
  46   90.7   4 LIFE   -lifetime
  47   88.4   4 CNBC   -cnbc
  48  101.3   4 COM    -comedy
  49   87.2   4 HIST   -history
  50   88.8   4 TNT    -tnt
  51  101.12  4 USA    -usa
  52   90.4   4 E!     -e!
  53   82.8   4 GOLF   -golf channel
  54   88.12  4 CSN    -comcast sportsnet
  55   88.7   4 FNC    -fox news
  56   82.7   4 CNN    -cnn
  57   82.12  4 HN     -headline news
  58   90.8   4 SPEED  -SPEEDVISION
  59   88.2   4 MSNBC  -msnbc
  60   90.3   4 HGTV   -HGTV
  61  101.8   4 AMC    -american movie classics
  62   87.11  4 NEWS12 -NEWS12
  63   90.6   4 FOOD   -food network
  64  101.7   4 SYFY   -SCI-FI
  65  101.11  4 VH1    -vh1
  66   82.3   4 ANIMP  -animal planet
  67   90.5   4 FAM    -abc family
  68  114.5   4 DISC HEALTH
  69  101.10  4 TLC    -the learning channel
  70  101.6   4 NICK   -nickelodeon
  71  101.4   4 MTV    -mtv
  72   88.6   4 STYLE  -e! style
  73  104.9   4 FSNY  -FOX SPORTS NY
  75   90.9   4 MSG2   -MSG2
  95  118.2   4 LOCAL  -CH95 TRENTON
 103  102.12  4 BLOOM  - BLOOMBERG
 104   82.2   4 C-SPAN2-c-span 2
 105  105.11  4 CSPN3  -C-SPAN 3
 118   88.6   4 STYLE  -e! style
 119  115.11  4 LIFEMVE-Lifetime Movies
 136  101.5   4 DISNEY CHANNEL
 137   82.5   4 HALL   -Hallmark
 157   89.10  4 HALLMARK MOVIE CHANNEL
 162   90.10  4 G4TTV  -g4 tech tv
 169   88.5   4 TCM    -turner classic movies
 184  119.8   4 ACN    -ACN
 190  118.10  4 LEASED -LEASED ACCESS
 246  113.4   4 WPVI-WC
 248  113.5   4 WCAU-DT- WCAU_DT WEATHER
 249  113.6   4 UNISPRT-  Universal Sports
 250  106.6   4 WNYW   -WNYW-5
 251  114.4   4 WFPA - TELEFUTURA
 252   30.3   4 THIS   - WPHL-DT THIS TV
 253  106.3   4 WNBC   -WNBC(4)-NY
 254   87.12  4 WPIX   -WPIX-11
 255   79.9   4 WWOR   -WWOR-9
 256  106.1   4 WCBS  -WCBS(2)-NY
 257  117.3   4 WHYY2
 258  117.4   4 WHYY3
 259   20.3   4 WNETKID-WNET Kids 13
 260   20.2   4 WNETVME -WNET V-ME
 261   79.3   4 WNJS   -wnjs-23
 262  103.2   4 WNJS-JV
 264   13.6   4 WYBEM - MHZ WORLDVIEW
 265   13.5   4 WYBEG - GLOBAL MIND
 282  119.8   4 ACN    -ACN
 283  119.5   4 SNBC   -SHOP NBC
 287  116.11  4 DAYSTAR-Daystar
 291  114.7   4 EWTN   -ewtn
 612  114.4   4 WFPA - TELEFUTURA
 965  118.11  4 GAVEL  -GAVEL 2 GAVEL/JEWELRY TV
1075   80.51  4 TVWorks InBand Channel



VCT_ID 3010 (0x0bc2), version 13
  VC CD.PROG M# NAME
====================
   2   82.1   4 C-SPAN -c-span
   3   80.1   4 KYW    -kyw-3
   4   82.10  4 QVC    -qvc
   5   80.6   4 WTXF   -wtxf-29
   6   80.2   4 WPVI   -wpvi-6
   7  106.2   4 WABC   -WABC(7)-NY
   8   80.12  4 CNPH   -comcast network
   9   80.5   4 WPHL   -wphl-17
  10   80.3   4 WCAU   -wcau-10
  11   82.9   4 HSN    -home shopping network
  12   80.4   4 WHYY   -whyy-12
  13  106.4   4 WNET   -WNET-13
  14   80.8   4 WPSG   -wpsg-57
  15   80.11  4 WFMZ   -wfmz-69
  16   80.10  4 WUVP   -wuvp-65
  17   80.9   4 WPPX   -wppx-61
  18   80.7   4 WGTW   -wgtw-48
  19  118.1   4 LOCAL  -CH19
  20   79.12  4 WYBE   -WYBE-35
  21   79.8   4 WBPH   -wbph-60
  22   79.10  4 WWSI   -wwsi-62
  23   79.3   4 WNJS   -wnjs-23
  24  118.3   4 LOCAL  -CH24TREN & 16LAMB
  26  118.4   4 MERCER COUNTY COLLEGE
  27   79.6   4 WMCN   -wmcn-53 (formally wwac)
  36   90.1   4 SPIKE  -tnn
  37   88.3   4 TVLND  -TV LAND
  38  101.2   4 TOON   -cartoon network
  40   87.6   4 TWC    -the weather channel
  42  101.9   4 DIS    -discovery channel east
  43  101.1   4 BET    -bet
  44   87.4   4 A&E    -arts & entertainment
  46   90.7   4 LIFE   -lifetime
  48  101.3   4 COM    -comedy
  49   87.2   4 HIST   -history
  51  101.12  4 USA    -usa
  52   90.4   4 E!     -e!
  55   88.7   4 FNC    -fox news
  56   82.7   4 CNN    -cnn
  61  101.8   4 AMC    -american movie classics
  63   90.6   4 FOOD   -food network
  66   82.3   4 ANIMP  -animal planet
  70  101.6   4 NICK   -nickelodeon
  75   90.9   4 MSG2   -MSG2
  95  118.2   4 LOCAL  -CH95 TRENTON
 103  102.12  4 BLOOM  - BLOOMBERG
 104   82.2   4 C-SPAN2-c-span 2
 105  105.11  4 CSPN3  -C-SPAN 3
 119  115.11  4 LIFEMVE-Lifetime Movies
 136  101.5   4 DISNEY CHANNEL
 137   82.5   4 HALL   -Hallmark
 162   90.10  4 G4TTV  -g4 tech tv
 169   88.5   4 TCM    -turner classic movies
 184  119.8   4 ACN    -ACN
 190  118.10  4 LEASED -LEASED ACCESS
 246  113.4   4 WPVI-WC
 248  113.5   4 WCAU-DT- WCAU_DT WEATHER
 249  113.6   4 UNISPRT-  Universal Sports
 250  106.6   4 WNYW   -WNYW-5
 251  114.4   4 WFPA - TELEFUTURA
 252   30.3   4 THIS   - WPHL-DT THIS TV
 253  106.3   4 WNBC   -WNBC(4)-NY
 254   87.12  4 WPIX   -WPIX-11
 255   79.9   4 WWOR   -WWOR-9
 256  106.1   4 WCBS  -WCBS(2)-NY
 257  117.3   4 WHYY2
 258  117.4   4 WHYY3
 259   20.3   4 WNETKID-WNET Kids 13
 260   20.2   4 WNETVME -WNET V-ME
 261   79.3   4 WNJS   -wnjs-23
 262  103.2   4 WNJS-JV
 264   13.6   4 WYBEM - MHZ WORLDVIEW
 265   13.5   4 WYBEG - GLOBAL MIND
 282  119.8   4 ACN    -ACN
 283  119.5   4 SNBC   -SHOP NBC
 287  116.11  4 DAYSTAR-Daystar
 291  114.7   4 EWTN   -ewtn
 612  114.4   4 WFPA - TELEFUTURA
 965  118.11  4 GAVEL  -GAVEL 2 GAVEL/JEWELRY TV
1075   80.51  4 TVWorks InBand Channel



VCT_ID 3012 (0x0bc4), version 13
  VC CD.PROG M# NAME
====================
 251  114.4   4 WFPA - TELEFUTURA
1075   80.51  4 TVWorks InBand Channel



VCT_ID 0 (0x0000), version 13
  VC CD.PROG M# NAME
====================
 251  114.4   4 WFPA - TELEFUTURA
1075   80.51  4 TVWorks InBand Channel



 CD    FREQUENCY
================
  1   75250000hz
  2   57000000hz
  3   63000000hz
  4   69000000hz
  5   79000000hz
  6   85000000hz
  7  177000000hz
  8  183000000hz
  9  189000000hz
 10  195000000hz
 11  201000000hz
 12  207000000hz
 13  213000000hz
 14  123000000hz
 15  129000000hz
 16  135000000hz
 17  141000000hz
 18  147000000hz
 19  153000000hz
 20  159000000hz
 21  165000000hz
 22  171000000hz
 23  219000000hz
 24  225000000hz
 25  231000000hz
 26  237000000hz
 27  243000000hz
 28  249000000hz
 29  255000000hz
 30  261000000hz
 31  267000000hz
 32  273000000hz
 33  279000000hz
 34  285000000hz
 35  291000000hz
 36  297000000hz
 37  303000000hz
 38  309000000hz
 39  315000000hz
 40  321000000hz
 41  327000000hz
 42  333000000hz
 43  339000000hz
 44  345000000hz
 45  351000000hz
 46  357000000hz
 47  363000000hz
 48  369000000hz
 49  375000000hz
 50  381000000hz
 51  387000000hz
 52  393000000hz
 53  399000000hz
 54  405000000hz
 55  411000000hz
 56  417000000hz
 57  423000000hz
 58  429000000hz
 59  435000000hz
 60  441000000hz
 61  447000000hz
 62  453000000hz
 63  459000000hz
 64  465000000hz
 65  471000000hz
 66  477000000hz
 67  483000000hz
 68  489000000hz
 69  495000000hz
 70  501000000hz
 71  507000000hz
 72  513000000hz
 73  519000000hz
 74  525000000hz
 75  531000000hz
 76  537000000hz
 77  543000000hz
 78  549000000hz
 79  555000000hz
 80  561000000hz
 81  567000000hz
 82  573000000hz
 83  579000000hz
 84  585000000hz
 85  591000000hz
 86  597000000hz
 87  603000000hz
 88  609000000hz
 89  615000000hz
 90  621000000hz
 91  627000000hz
 92  633000000hz
 93  639000000hz
 94  645000000hz
 95   93000000hz
 96   99000000hz
 97  105000000hz
 98  111000000hz
 99  117000000hz
100  651000000hz
101  657000000hz
102  663000000hz
103  669000000hz
104  675000000hz
105  681000000hz
106  687000000hz
107  693000000hz
108  699000000hz
109  705000000hz
110  711000000hz
111  717000000hz
112  723000000hz
113  729000000hz
114  735000000hz
115  741000000hz
116  747000000hz
117  753000000hz
118  759000000hz
119  765000000hz
120  771000000hz
121  777000000hz
122  783000000hz
123  789000000hz
124  795000000hz
125  801000000hz
126  807000000hz
127  813000000hz
128  819000000hz
129  825000000hz
130  831000000hz
131  837000000hz
132  843000000hz
133  849000000hz
134  855000000hz
135  861000000hz
136  867000000hz
137  873000000hz
138  879000000hz
139  885000000hz
140  891000000hz
141  897000000hz
142  903000000hz
143  909000000hz
144  915000000hz
145  921000000hz
146  927000000hz
147  933000000hz
148  939000000hz
149  945000000hz
150  951000000hz
151  957000000hz
152  963000000hz
153  969000000hz
154  975000000hz
155  981000000hz
156  987000000hz
157  993000000hz
158  999000000hz



M#     MODE
===========
 1     QPSK
 2   QAM_64
 3  UNKNOWN
 4  QAM_256

```

I used the listing to guess at which ID was correct for me.

I'm guessing that the problem is that sct65scan is trying to find the mappings on your ATSC interface instead of your cable interface.  That would explain why it would timeout.  Is there a way to specify which interface to use?  If not, maybe just remove the ATSC interface.

I hope this helps!

---

### Post by radnor on 2009-12-24
Well....  I'm in the same boat.  I cannot get it working.  Hopefully soon.

---

### Post by B34N on 2009-12-24
> **radnor said:**
> Well....  I'm in the same boat.  I cannot get it working.  Hopefully soon.

How far do you get?  Do you also have two tuners?

---

### Post by radnor on 2009-12-24
Well, using the HDHR tuners (1 box, 2 tuners).
Compiled libhdhomerun.  Copied the libhdhomerun.so to /usr/lib. 

Had hdhomerun_config, but moved stuff around and removed it to recompile.  working on that now.

---

### Post by radnor on 2009-12-24
hdhomerun_config compiled

Per Silicondust website, the "sudo make install" is a no go.  
[hdhr web site]("http://www.silicondust.com/downloads/linux")

But the hdhomerun_config discover - works fine.

---

### Post by radnor on 2009-12-24
scte65scan compiled.  but when I run it I get the follow error message:
"/dev/dvb/adapter0/demux0: No such file or directory"

---

### Post by radnor on 2009-12-24
This is the out put when I try to compile scte65scan:

```
make -f Makefile.hdhr
cc -O2 -DHDHR -I./libhdhomerun scte65scan.o tunerdmx.o ../libhdhomerun/hdhomerun_os_posix.o ../libhdhomerun/hdhomerun_pkt.o ../libhdhomerun/hdhomerun_debug.o ../libhdhomerun/hdhomerun_discover.o ../libhdhomerun/hdhomerun_channels.o ../libhdhomerun/hdhomerun_channelscan.o ../libhdhomerun/hdhomerun_control.o ../libhdhomerun/hdhomerun_video.o ../libhdhomerun/hdhomerun_device.o -lpthread -o scte65scan
../libhdhomerun/hdhomerun_os_posix.o: In function `getcurrenttime':
hdhomerun_os_posix.c:(.text+0xe3): undefined reference to `clock_gettime'
collect2: ld returned 1 exit status
make: *** [scte65scan] Error 1

```

---

### Post by radnor on 2009-12-24
Compiled it with the help of: [link]("http://mythtv.org/pipermail/mythtv-users/2009-November/270972.html")


When it runs, back to this:
"/dev/dvb/adapter0/demux0: No such file or directory"



[COLOR="Red"]Getting a scan!!!![/COLOR]  With this:
"./scte65scan -H FFFFFFFF -f3 us-Cable-Standard-center-frequencies-QAM256 > myth-vct.sql"

---

### Post by radnor on 2009-12-24
Have my file.  ran this:
"sudo mysql -u root -p mythconverg < myth-vct.sql"

Now going to shut this down and log in to myth (another partition).

FINGERS CROSSED.....

---

### Post by radnor on 2009-12-24
Well, it worked sorta...  I went to watch TV.  Right back to menu.  Moved BE AND FE logs out of the way. Restart. Watch TV. Right back to menu. Looked at BE log.  Did not like starting channel.  Went to channel editor.  Had 2 channels 251 & 1065.


The myth-vct.sql file.  It looked like it had 4 sections in it.
[LIST=1]
[*]-- WARNING: The following line clears out dtv_multiplex table
[*]-- WARNING: The following line clears out channel table
[*]-- WARNING: The following line clears out channel table
[*]-- WARNING: The following line clears out channel table
[/LIST]

The last 2 had only channel 251 and 1065 in it. So this is why I had only the 2.  So I made a copy of it (CYA) and edited the last 2 sections out.  reapplied the file.  restart BE.  Now I have TV!!!!


So, now I have just 2 more things to do and I'm done.  1 is schedules direct, and the 2nd is LVM for my storage.  I have a 500G HDD now.  My thinking for the LVM is....  If my drive starts getting full, I can ADD a drive and not lose recorded stuff on the "old" drive.  If someone is more familiar with LVM, PLEASE correct me if my thinking is off.

---

### Post by radnor on 2009-12-24
For others following, I found a site which said to do this for your scan:
"./scte65scan -H FFFFFFFF -f3 us-Cable-Standard-center-frequencies-QAM256 > myth-vct.sql"

Where the FFFFFFFF is, I was substuting the ID of my HDHR box which begins with 1014xxxx.  Do [COLOR="Red"]**NOT**[/COLOR] do this, KEEP the FFFFFFFF in place.    The reason I was id(ing) it by 1014xxxx when I set up mythtv I could have put FFFFFFF if I only had 1 HDHR or the address if I was going to have more than one HDHR (which is in my case 1014xxxx).

Hopefully between what the OP has and my stumbling around (and detailed here), others that follow will have an easier go at this.

---

### Post by the_pod on 2010-01-04
> **radnor said:**
> Well, it worked sorta...  I went to watch TV.  Right back to menu.  Moved BE AND FE logs out of the way. Restart. Watch TV. Right back to menu. Looked at BE log.  Did not like starting channel.  Went to channel editor.  Had 2 channels 251 & 1065.


The myth-vct.sql file.  It looked like it had 4 sections in it.
[LIST=1]
[*]-- WARNING: The following line clears out dtv_multiplex table
[*]-- WARNING: The following line clears out channel table
[*]-- WARNING: The following line clears out channel table
[*]-- WARNING: The following line clears out channel table
[/LIST]

The last 2 had only channel 251 and 1065 in it. So this is why I had only the 2.  So I made a copy of it (CYA) and edited the last 2 sections out.  reapplied the file.  restart BE.  Now I have TV!!!!


So, now I have just 2 more things to do and I'm done.  1 is schedules direct, and the 2nd is LVM for my storage.  I have a 500G HDD now.  My thinking for the LVM is....  If my drive starts getting full, I can ADD a drive and not lose recorded stuff on the "old" drive.  If someone is more familiar with LVM, PLEASE correct me if my thinking is off.
Radnor - posting here hoping you still check this thread.

This weekend I re-did my myth system with plans on using the scte65scan feature.  I was able to compile it and create the channel maps. I don't have a doodad so I'm ok just trying 1 setup after another until I get the right map.

I've tried importing the file into the myth DB with success - i.e., the channel list shows the channels per the map file. That said, I'm unable to watch TV at all. Is this the problem you were having?

I've tried 4 or 5 of the maps and am unable to get any of them to actually allow me to watch TV so I'm going back to the drawing board and mapping the channels by hand like I used to do.

It sounds like you found a solution (if I'm reading your comments above correctly).  If my assumption is correct, any assistance you can provide would be much appreciated and would save me hours of tedium.

Thanks.

---

### Post by radnor on 2010-01-04
I' not subscribed to this thread, but I do look several pages deep for my own solutions.

No, I could watch TV.  Did some recording but it WAS manual, until I fixed it with the info from this post.

Dont know what your setup is.  I have a BE/FE and a RFE.  I do NOT like using the FE because I am having desktop lockups.  When the desktop locks, the BE works just fine. Eventually the BE will be headless and remote (basement).

Tuner is a HD Home Run.

This is from MEMORY, so if I forget something please do not FLAME me.  I am going to assume you are using a HDHR too.

After installing Mythbuntu I had to configure the BE. I did mythtv-setup.  If I recall, there are about 5 or 6 items you can select from the menu.  I went 1 at a time and filled in the info.  I STOPPED before selecting the storage groups options since I do not use them YET.  Then when setup exits, it would like to run mythfilldatabase.  I let it do so.

I will tell you, I'm a noob.  I'm on cable and ASSUME you are too.  I selected freq table of us-cable.

I am not sure where you are at, I'm east coast.  I'm willing to share a verizon cell number and talk to you directly (it will be faster).  But, you MUST agree to do one thing, add what we did to solve your problem to a post to help others.  Or, we can keep chugging here.

---

### Post by radnor on 2010-01-04
PM on it's way.

---

