---
title: "How To : Conexant  or Rockwell Modems"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by alexfish on 2010-01-08
[B]Link To :

[/B]

[http://ubuntuforums.org/showthread.php?t=1375907](http://ubuntuforums.org/showthread.php?t=1375907)

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1308328&page=4](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1308328&page=4)

also

**Conexant/Rockwell modem HOWTO**

**Imran Ghory**

[EMAIL="ImranG@btinternet.com"]ImranG@btinternet.com[/EMAIL]



2001-08-01

[B]Revision History

[/B]Revision 1.32002-03-12Revised by: ig

Updated to deal with new HCF driver.


Revision 1.22002-02-21
Revised by: igUpdated to deal with new HSF driver and release date for HCF driver.

Revision 1.02001-09-09
Revised by: igAdded entries to the FAQ, corrected grammatical errors, and update a URL.

Revision 0.92001-08-01
Revised by: igInitial release.

 A guide to using Conexant and Rockwell chipset based Software modems under Linux. 



**Table of Contents**1. [Introduction]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#INTRODUCTION")
1.1. [Purpose of the howto]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#PURPOSE")
1.2. [About the howto]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#ABOUT")
1.3. [Feedback]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#FEEDBACK")
1.4. [License]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#LICENCE")
1.5. [Acknowledgments]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#ACKNOWLEDGEMENTS")
1.6. [Getting Help]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#GETTING-HELP")

2. [Quick Start guide]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#QUICK-START")
2.1. [Quick Starting with an HCF modem]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#QUICK-START-HCF")

3. [Identifying your modem type]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#GETTING-STARTED")

4. [HCF chipset based modems]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#HCF")
4.1. [History]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#HCF-HISTORY")
4.2. [Miscellaneous information]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#MISC-HCF")

5. [HSF]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#HSF")
5.1. [History]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#HSF-HISTORY")
5.2. [Kernel 2.2.14 - 18]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#KERNEL14-18")
5.3. [Kernel 2.4.*]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#KERNEL4-SERIES")
5.4. [Troubleshooting FAQ]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#FAQ")

A. [License]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#FDL-APP").1. [GNU Free Documentation License]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#FDL")

---

