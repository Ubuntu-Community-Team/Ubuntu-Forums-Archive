---
title: "3com 56k internal fax modem model 5610"
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by biggestchops on 2009-06-30
Afternoon everybody

I've been trying to make this 3com modem work for a little while now. lspci gives the info we see above. long and short is, i'm running 9.04, and the modem does not show up under the network settings app. pppconfig is unable to auto detect which port to use. 

my friend tells me that using a really old version of ubuntu (5.10) he could graphically see the modem and interact with it, and now nothing. 

any suggestions? i've been googling around, and can't find anything helpful. any suggestion would be most helpful

---

### Post by dannyboy79 on 2009-07-12
> **biggestchops said:**
> Afternoon everybody

I've been trying to make this 3com modem work for a little while now. lspci gives the info we see above. long and short is, i'm running 9.04, and the modem does not show up under the network settings app. pppconfig is unable to auto detect which port to use. 

my friend tells me that using a really old version of ubuntu (5.10) he could graphically see the modem and interact with it, and now nothing. 

any suggestions? i've been googling around, and can't find anything helpful. any suggestion would be most helpful
i have the same modem and am trying to get it working in Hardy Heron. I don't think it's supported out of the box but with some help from scanModem program I think I am going to be able to get it working. I'll let you know how it goes. I am attempting to use it with PeoplePC ISP dialup as the guy I have installed Ubuntu for doesn't want to pay for DSL or Broadband Internet. Let me know if you found anything out also. Thanks

---

### Post by hoss2001 on 2009-12-17
I'm running an ISA modem and pppconfig didn't autodetect it either. I found it using wvdialconf. (sudo wvdialconf) Then I went back to pppconfig and used the manual setup option that comes up after autodetect fails. This is where you plug in the port number found by wvdialconf. )ttyS?) Also, since you have a 3com modem, before you exit, open Advanced Options from the main page. The init string shows ATZ with the recommendation that it works with most modems. _Not_ with US Robotics ISA modems and since yours is hardware based, possibly not with yours. The ATZ command tells USR modems to drop the connection after a few seconds. Wvdialconf should have returned an init string, or you can check [www.modemhelp.net](www.modemhelp.net). They also have a page that explains the basic init string commands. The correct init string will start with AT& .... 
Hope this helps.

---

