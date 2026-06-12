---
title: "WIFI Problem, Dell Latitude E5400 /still not working/"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by hato_CORP on 2010-03-26
Problem with WIFI, Dell Latitude E5400
Hi;

I have a problem with my WIFI card. Is anybody able to help? I have a Dell Latitude E5400 /Made in Ireland/. Week ago I switched to the newest Ubuntu /I am new user/. The System is great - everything is working perfect besides WIFI card.

System &#8594; Administration &#8594; Hardware Drivers /recognize TWO drivers/
* Broadcom B43 Wireless Driver /tested by Ubuntu Developers - Free/
* Broadcom STA Wireless Driver /tested by Ubuntu Developers – Proprietary/

First driver is not working.
I am not able to install the second one. There is some faulty information inside a log.
Would anybody help? Which driver will suit my WIFI card?

J.
  	
 1 Week Ago	   #2
bkratz
Dark Roasted Ubuntu

 
Join Date: Apr 2009
Beans: 1,105
Re: Problem with WIFI, Dell Latitude E5400
Quote:
Originally Posted by hato_CORP  
Hi;

I have a problem with my WIFI card. Is anybody able to help? I have a Dell Latitude E5400 /Made in Ireland/. Week ago I switched to the newest Ubuntu /I am new user/. The System is great - everything is working perfect besides WIFI card.

System &#8594; Administration &#8594; Hardware Drivers /recognize TWO drivers/
* Broadcom B43 Wireless Driver /tested by Ubuntu Developers - Free/
* Broadcom STA Wireless Driver /tested by Ubuntu Developers – Proprietary/

First driver is not working.
I am not able to install the second one. There is some faulty information inside a log.
Would anybody help? Which driver will suit my WIFI card?

J.
The first thing needed is the version of the wifi card you have.
Please go to the terminal "Applications>>Accessories>>Terminal (in Ubuntu)" and enter

lspci | grep Wireless

(That is LSPCI in lowercase, W in uppercase)
if you get nothing returned just try

lspci -nn

and look through the long listing and find the network contoller and post the contents back here. It probably will say something "like BCM43xx".
  	
 1 Week Ago	   #3
hato_CORP
First Cup of Ubuntu

 
Join Date: Mar 2010
Beans: 3
Re: Problem with WIFI, Dell Latitude E5400
Thx;

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
  	
 1 Week Ago	   #4
bkratz
Dark Roasted Ubuntu

 
Join Date: Apr 2009
Beans: 1,105
Re: Problem with WIFI, Dell Latitude E5400
Quote:
Originally Posted by hato_CORP  
Thx;

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
I know it says Dell mini, but these directions seem to be pretty straightforward and work for most people.

[http://www.ubuntumini.com/2009/11/br...in-karmic.html](http://www.ubuntumini.com/2009/11/br...in-karmic.html)
  	
 1 Hour Ago	   #5
hato_CORP
First Cup of Ubuntu

 
Join Date: Mar 2010
Beans: 3
Re: Problem with WIFI, Dell Latitude E5400
Hmm...

I followed the process.
STA driver installed, but WIFI still not working.

Also WIFI light indicator it is not on.

J.

---

### Post by bkratz on 2010-03-26
From Chili555's guidance

"There is an issue with the implementation of dell-laptop and its ability to properly relate the meaning of key presses to the kernel; it may actually be an issue with dell-ami vs. dell-laptop. When I hear that someones wireless mysteriously doesn't work, and they talk about their light or LED and then mention Dell, I get suspicious. Often, but not always, unloading dell-laptop works wonders. Please try the following and see if it clears up."

sudo rmmod -f dell-laptop

Worth a try at least.

---

