---
title: "vodafone prepaid 9.10 not working"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by carpman on 2009-11-13
Hello, am trying to get this working and have followed guides but can't get it to dial out?

lsusb
```

Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem

```

Have installed usbmodeswitch, vodafone-mobile-connect ozerocdoff.

the modem is found when i plug it by both VMC and network manager, i have set it up network manager and VMC 

APN=pp.vodafone.co.uk
User=wap
Pass=wap

also tried 

APN=pp.internet


In network manger i cannot even try and connect as no option to, in VMC i can click on connect but it does not?

Works fine on windows.

any ideas?

cheers

---

### Post by pdc on 2009-11-13
so you are using VMC (vodafone mobile connect) to run a Vodafone modem

recommend you join their support forum; it is very good software;

(contains both ozercdoff and usbmodeswitch)

and there is very good support from the guys writing the software;

from following the forum, Ubuntu 9.10 is not playing well with VMC:

many folks (in retrospect) would have been much better off staying with 9.04 that worked; let others enter the minefield of new software; and install several months later when the bugs get ironed;

here is the betavine forum

[http://www.betavine.net/bvportal/forums/index.html?forumId=320](http://www.betavine.net/bvportal/forums/index.html?forumId=320)

and here is a posting from that forum describing problems

[http://www.betavine.net/bvportal/forums/index.html?threadId=ff80808124e7d7c70124edde89ed6fea&postId=ff80808124e7d7c70124edde89f16feb#ff80808124e7d7c70124edde89f16feb](http://www.betavine.net/bvportal/forums/index.html?threadId=ff80808124e7d7c70124edde89ed6fea&postId=ff80808124e7d7c70124edde89f16feb#ff80808124e7d7c70124edde89f16feb)

I guess folks must be asking themselves: why, if their software worked before, did they "upgrade" to new software?

---

### Post by John Read on 2009-11-16
Assuming you have installed your Vodaphone (Australia) wireless broadband modem via the Network Manager and are able to get it to "connect" but are still unable to actually connect to any Web sites, etc. then chances are you still have one small step to go. Right-click the Network Manager icon, choose Edit Connections, click the Mobile Broadband tab, click your Vodaphone service (e.g. Vodafone Postpaid), click the Edit button on the right, leave Number set to *99#, set the Username to vodafone, set the password to vodafone, leave APN set to vfinternet, and click the Apply button. You will be asked if it's OK to store some keys on a keyring, choose "At any time" (or somesuch), then you're set.

I find the connection speed I can achieve in Ubuntu 9.10 is several times faster than I could achieve in Ubuntu 9.04 which is just great.

The only hassle I have is that Ubuntu boots so fast that the modem does not have time to find the Vodafone connection and then it won't appear in the Network Manager list. You then have to cold boot again and hope for better luck next time.

Hope this helps.

Regards,

John

---

