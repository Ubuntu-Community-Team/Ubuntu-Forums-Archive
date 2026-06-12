---
title: "broadcom STA proprietary wireless driver problem"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by DCU Coey on 2011-01-02
i have a problem with the broadcom STA proprietary wireless driver... When i try to activate it from 'Additional Drivers' a message appears saying the following; 

SystemError: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb) Could not resolve 'gb.archive.ubuntu.com'

before this error occurred i had activated 'Broadcom B43 wireless driver' next thing i know my internet connection switched off. So  I then tried to activate 'Broadcom STA proprietary wireless driver' and saw the error message above.

---

### Post by PatchesTheCaveman on 2011-01-02
You need an Internet connection to download the driver.  Plug your computer into a wired Ethernet connection just long enough to download the driver and you should be good.

---

### Post by Bucky Ball on 2011-01-02
+1. You should get a message there is firmware available for your card. ;)

---

### Post by DCU Coey on 2011-01-02
ok, thanks, i'll see if i can (i'm only 16)

---

### Post by PatchesTheCaveman on 2011-01-02
Last time I checked, wired Internet was legal for you guys.  In some countries you can even go to bars!  :-D

---

### Post by DCU Coey on 2011-01-02
i meant if my parents will let me, lol

---

### Post by PatchesTheCaveman on 2011-01-02
I figured as much, I was just giving you hard time.  :-)

I'm 21, and I've been stuck at my parents for three weeks now, so I know how you feel.  It's even worse when you're used to freedom.

---

### Post by Bucky Ball on 2011-01-03
Just grab a cable and do it. If they don't know how they prob won't know what you're doing anyhow. If they do, tell 'em what you want to do and get one of them to do it. It will log on straight away, you only need to be on for updates and to get the drivers and firmware, prob 10 minutes tops. ;)

---

### Post by DCU Coey on 2011-01-03
Thanks for the replies but i haven't got a wired connection, only wireless. 

What shall i do now? i don't want to keep using the PS3, lol

---

### Post by bkratz on 2011-01-03
> **DCU Coey said:**
> Thanks for the replies but i haven't got a wired connection, only wireless. 

What shall i do now? i don't want to keep using the PS3, lol

Well, you could download it from this link on another computer and transfer via thumbdrive, but if a beginner you should look at the readme first and determine if you want to even try.  If so, there will be plenty of help here if stuck.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by Bucky Ball on 2011-01-03
You could borrow a cable from a friend or buy one. Or as the last poster suggested, but that will be tricky for a learner. Still, you'll definitely learn while you're trying and nothing wrong with that!

---

### Post by bkratz on 2011-01-03
Another way would be to go to the section of the following thread labeled

[COLOR="Red"]STA - No Internet access[/COLOR]

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Bucky Ball on 2011-01-03
If you can pull that off you'll have learned plenty, grasshopper!

BUT, bkratz and others, note well. You need access to a computer with internet access to download files (see step two in 'b43 - no internet').

Great suggestion though if OP is game to give it a try and has internet access on another box. ;)

We can help to guide you through it. Main thing; identify your card and work out if you need STA or b43.

---

### Post by bkratz on 2011-01-03
> **Bucky Ball said:**
> If you can pull that off you'll have learned plenty, grasshopper!

BUT, bkratz and others, note well. You need access to a computer with internet access to download files (see step two in 'b43 - no internet').

Great suggestion though if OP is game to give it a try and has internet access on another box. ;)

We can help to guide you through it. Main thing; identify your card and work out if you need STA or b43.

@Bucky those directions, referenced in the last post, show how to achieve the goal from the installation disk--no internet access required.

---

### Post by Bucky Ball on 2011-01-03
Right for STA, wrong for b43. Step 2 from 'b43 - no internet access':

> **Step 2.** 
On a computer with Internet access, download the required firmware files from [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
Consequently, if b43 is a appropriate for OPs card they are going to need internet access. It is generally not a choice of one or the other; generally one works and the other doesn't (or not very well) for a specific card.

:)

---

### Post by DCU Coey on 2011-01-03
ok, i found an internet cable among a bunch of other cables, i plugged it in boom! i have internet connection. i had to set up VPN though.

i then downloaded Broadcom 802.11 Linux STA Wireless driver source from the Ubuntu Software Center, restarted my computer (without the internet cable) and the wireless internet connection is back.

Thanks for the help!

---

### Post by Bucky Ball on 2011-01-03
Rockin'! A pleasure.

Enjoy your new OS, the learning curve, and please mark thread as solved using 'thread tools'.

Post any other probs in a new thread. Good luck with it all. ;)

---

### Post by bkratz on 2011-01-03
Congratulations, glad to see you got it going!

---

