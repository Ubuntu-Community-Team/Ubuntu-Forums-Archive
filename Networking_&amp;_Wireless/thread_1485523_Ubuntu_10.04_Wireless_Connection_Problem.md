---
title: "Ubuntu 10.04 Wireless Connection Problem"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by agusdon on 2010-05-16
Hello--
I'm pretty new to Ubuntu and there's probably a simble answer to this, but I just installed Ubuntu 10.04 and I can't seem to get the wireless connection to function. Ubuntu either says that the card is turned off or if I toggle the wireless switch on my keyboard it then says 'device not ready.' I'm using a Dell Wireless 1397 WLAN Mini-Card, and it works fine when I boot in Windows 7. 
 
Any help would be greatly appreciated. 
 
Thanks, 
 
Aaron

---

### Post by NUboon2Age on 2010-05-16
Well I'm not sure if there's an easy answer... Okay so let's start with the info requested in [HOWTO post a Wireless issue (ticket)]("http://ubuntuforums.org/showthread.php?p=6183681")

---

### Post by grandpa_rich on 2010-05-18
Have you checked your BIOS settings?  With previous versions of Ubuntu this has not seemed to matter, but it does now.  Wireless on my EEE 901 would not work until it was switched on in the BIOS.

---

### Post by Omnimental on 2010-06-07
Yeahuup. Have the same problem. Installed Ubuntu to begin learning Linux, but can't use it because I cannot get programs, updates, etc. from...my wireless internet...

I tried installing the bcmwl-kernel-source from the CD by using the Synaptic Package Manager. The Manager found the correct package but there was an error whilst installing. As a result, a little explosion with an exclamation point showed up next to my wireless signal icon on the upper right of the screen, which said (after I clicked it) something like "Broadcom Driver Package did not install correctly...blah, blah, blah...". 

This friggin' figures. The only driver that I cannot use is the absolutely most crucial one. You would think that this bug would be figured out, since, like, Broadcom is not exactly a Mom-n-Pop operation. I mean, what kind of market share do they have in the wireless card market, like 75%?? You would think that the internet (on just about any new 64bit Dell Laptop) would work just by installing the f__king OS...but nooooooooo. That would be too easy. The Read Me file in the Driver Package itself is wrong, so installing the drivers manually seems to be not an option.

Can anyone help, so users of Dell computers are not held captive by Windows 7, the biggest piece of trash since the Death Ray? :confused:

BTW: Checked my BIOS. The Wireless LAN Utility has been enabled. Wireless works fine in Windows 7, apparently its one redeeming quality. Yeah, in fact, why would it be the BIOS? If it was the BIOS, the wireless card would not fire up in Windows either. It would simply be shut off on the motherboard, "behaving" as if it didn't exist.

---

### Post by mayankkapoor on 2010-06-18
Had the same problem when I installed Ubuntu 10.04. Dell Studio 1535. Here's what I did to fix the problem:
1. Connected it to a wired network connection.
2. Downloaded all the updates.
Ubuntu restricted hardware manager found my broadcom card, and asked me to install the Broadcom STA wireless driver. 
3. I installed the driver, and wireless has worked since then.

A minor annoyance: Ubuntu 10.04 is fast in booting up, that it boots up in 5 seconds. But after the desktop is ready, the wireless icon starts searching for wlan connections, and takes about 6 seconds more to connect. A bit annoying.

---

### Post by robteh on 2010-06-18
seems that this is a common problem with Dell computers. Mine is a dell 1737 studio and I have failed to get its wireless to work. It's quite annoying but I won't give up. And of course solving issues like this is part of the fun in using Ubuntu. 

How does one get to the Ubuntu restricted hardware manager? Because my computer is up to date but my wireless still doesn't work

---

### Post by Boompoet on 2010-06-18
If you don't have access to a wired network? 

I just installed Ubuntu 10.4 on my dell e1705 and am having the same issue. Is there a place to download the updates in a package?

---

### Post by jpwuta on 2010-07-24
I

---

### Post by croonneck on 2010-07-30
> **mayankkapoor said:**
> Had the same problem when I installed Ubuntu 10.04. Dell Studio 1535. Here's what I did to fix the problem:
1. Connected it to a wired network connection.
2. Downloaded all the updates.
Ubuntu restricted hardware manager found my broadcom card, and asked me to install the Broadcom STA wireless driver. 
3. I installed the driver, and wireless has worked since then.



+1

I was having the same problems on 10.04 since today morning since i installed it, before I used a wired Internet connection to download the updates for the hardware drivers. the broadcom STA driver then had to be activated, and i can now  access the wireless

---

