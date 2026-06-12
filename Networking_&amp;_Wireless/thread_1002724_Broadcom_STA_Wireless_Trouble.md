---
title: "Broadcom STA Wireless Trouble"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by Arnitak on 2008-12-05
I installed Ubuntu x64 Desktop Edition from an alternate install disk. Shortly after boot the system asks me if I want to use the Broadcom STA Wireless Driver. Obviously I do and I activate the driver. The trouble is that it does not work at all. Uninstalling the network manager, I connect manually, but I cannot set the MODE, always giving me an error. Another annoying issue is that the LED for the wireless is working in reverse, it's off when it's on, and it's on when the LED is off. Can someone help me? I see no one bothers to answer about the shitty support of ubuntu wireless. Please note that my card work fine in 7.10.

---

### Post by superprash2003 on 2008-12-05
in your terminal type iwlist scanning and post outpt

---

### Post by Ayuthia on 2008-12-05
Please also post the results of:
```
lspci -nn
lsmod|grep -e b43 -e ssb -e wl
```

---

### Post by Arnitak on 2008-12-05
Well, I took care of it, thanks!
Problem is solved.

---

### Post by kevdog on 2008-12-05
Thank you for being illustrative in your provided solution -- it will help a lot of people!

---

### Post by Arnitak on 2008-12-06
> **kevdog said:**
> Thank you for being illustrative in your provided solution -- it will help a lot of people!

Well, I uninstalled network manager and installed wicd. That basicly took care of everything EXCEPT encryption.

---

### Post by skunk90 on 2009-05-02
hi i have a lenovo g530 3000 series laptop, i  i'm new to linux and just intalled ubuntu 9 and don't know how to get my wireless card working. i know it's a broadcom 4312 chip and network manager says it's proprietary which means i'm pretty much screwed? if i can't get my wireless card to work i'm gonna have no choice but to put windows back in my machine. can someone please help me?? i have downloaded the broadcom sta driver from the shitty website and it's now on my desktop. i'm really stupid at linux, so step by step instructions would be greatly appreciated.

---

### Post by skunk90 on 2009-05-02
nevermind guys i went to [http://www.linuxwireless.org](http://www.linuxwireless.org) and it helped me fix my wireless problems, but hopefully i won't have to do that on ubuntu 10 *cough hint HINT*  for a second i thought i was doomed to revert to crappy microsoft shite

---

### Post by e-square12 on 2009-08-10
> **skunk90 said:**
> nevermind guys i went to [http://www.linuxwireless.org](http://www.linuxwireless.org) and it helped me fix my wireless problems, but hopefully i won't have to do that on ubuntu 10 *cough hint HINT*  for a second i thought i was doomed to revert to crappy microsoft shite

How did you fix your problem? I have the same issue with the same computer. Thanks.

---

### Post by alibiagent on 2010-02-06
*_[SIZE=4]**The following link instantly solved my problems with my Broadcom WLAN Card using the WTA driver:**[/SIZE]_*

[SIZE=4][http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Before going to broadcom.com I had tried all sorts of "fixes" on this forum, and while they did work, they were long and complicated, while this method is simply a matter of unpacking and then "making" the file :)
[/SIZE]

---

