---
title: "wireless &quot;N&quot; connects at &quot;G&quot; speeds."
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by kainalu on 2010-12-07
Hello,

I just bought a new E2000 router with N tech. After setting up, I have it set to MAC filtering, no security, hidden SSID. 

All the Windows boxen connect at 150MBPs (40MHz channel width wireless G) or 300MBPs (N). All my Ubuntu boxen (even with N cards) are stubbornly locked in at 54MBPs.

When I attempt to make the router require N, the windows boxen with the n cards keep on kicking, the Ubuntu's refuse to connect at all.

Ubuntu boxen : 
Dell Inspiron 6400  G card and Ubuntu 10.10. Uses the wl driver.
ASUS EEEPC 901 with N card and ubuntu 10.04.

---

### Post by grahammechanical on 2010-12-08
I have just googled ubuntu n wireless. There are some interesting links found in answer.

Regards.

Please search for a post called iwlan won't do wireless N. It is a similar problem to your problem. It may not give you the answer. It will put you in the right direction. I cannot put a link to this thread as I do not know how to do that. I suggest that you think about identifying the wireless card in the computer and working out if the driver allows it to work at n speeds. And also how to set up the driver to use an n speed wireless adapter/card.

---

### Post by kainalu on 2010-12-08
I did find that thread before I posted, however the driver my computer uses is the wl driver, and a similar file does not exist in the /etc/modprobe.d/  for that driver. As my laptop came with this card, and my OS with this driver, I really don't know how to switch drivers. Is that the best way to diag this??

dell 6400 : 

0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01) on the wl driver 

EEEPC 901 : 

01:00.0 Network controller: Ralink RT2860 on the rt2860 driver

---

### Post by kainalu on 2010-12-08
I think I got it partially working correctly on the EEE by following this : 

[http://ubuntuforums.org/showthread.php?t=1246960](http://ubuntuforums.org/showthread.php?t=1246960)

It now connects at 135Mb/s (no 300 possible??)

I still don't know what to do about the dell

Thanks for helping me, community!

---

### Post by kainalu on 2011-01-03
I'm not really sure I should mark the thread "solved", but I solved it for me. 

I just decided to run Cat5e cable under the house and install wall jacks in every room of the house and a gigabit switch. gigabit speed, low latency. No wireless usage, no wireless problems! :p

---

### Post by supershin on 2011-01-03
LOL, great out-of-the-box thinking there! Wired connections are actually more reliable and considered better, though wireless has its place.

---

### Post by add1kt on 2011-12-26
As with anything linux related you should verify your hardware is compatible.  Wireless N is definitely capable through linux.  I am able to get 7MB/s xfr speed to an nfs HDD using ASUS USB N-13 and the rt3070 driver.  I made sure the device was compatible before purchasing.

---

