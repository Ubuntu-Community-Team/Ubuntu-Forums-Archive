---
title: "Acer Aspire One Wireless"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by entrope on 2009-01-21
Hello all,

I have an Acer Aspire One 110, which I have been running Ubuntu on without problems for about a month. Recently, I reinstalled Ubuntu, and haven't been able to make my wireless work since. I followed the same steps as last time (and the same steps described in the numerous tutorials) yet my wireless card is not working. It is not listed in the output of lspci, nor is an ath0 or wifi0 listed in the output of iwlist or ifconfig. All I see is an eth0 (which is working), a pan0, and lo. Initially, I thought I must have done something in the wrong order after my reinstall, so I removed and reinstalled the madwifi driver as per the madwifi website. When this didn't work, I decided I would reinstall Ubuntu yet again, after which I was very careful to follow the instructions which initially worked. Still, my wireless card is apparently not detected. Have I missed something, and is there a way to find out if this is a hardware problem? Thanks in advance.

---

### Post by danni-la on 2009-01-21
Hi there.. I had no luck with the madwifi drivers on my aao but with the ath5k driver from the backports not sure if it will help but might be worth a try?

---

### Post by TheBiles on 2009-01-21
I'm having this same problem. I installed it, it worked perfectly, but after rebooting it won't work at all.  Can you post a link to the other drivers?

---

### Post by danni-la on 2009-01-21
I installed the following

sudo aptitude install linux-backports-modules-intrepid-generic

then under hardware drivers there are two drivers, disable the one that says support for Atheros 802.11 wireless lan cards.

---

### Post by TheBiles on 2009-01-21
> **danni-la said:**
> I installed the following

sudo aptitude install linux-backports-modules-intrepid-generic

then under hardware drivers there are two drivers, disable the one that says support for Atheros 802.11 wireless lan cards.

I only see one driver that says "support for 5xxx series of Atheros 802.11 wireless LAN cards."

---

### Post by danni-la on 2009-01-22
> **TheBiles said:**
> I only see one driver that says "support for 5xxx series of Atheros 802.11 wireless LAN cards."

That is the active one on my machine and it is working perfectly. If that is not working maybe there is something else wrong? sorry I couldn't help more!

---

### Post by entrope on 2009-01-23
Well, I've been at it for quite some time now, but I'm happy to say that my wireless is working. I'm not quite sure why it didn't work using the madwifi drivers. Neither the generic atheros nor the ath5k drivers worked. Neither did the madwifi when I followed previously working instructions meticulously. Eventually, I stumbled across this website:

[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

This worked, but was horribly slow. In the comments, someone mentioned they had the same problem, but that using the Hardy method (ndiswrapper) worked well. For those of you having the same problem, the ndiswrapper method:

[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

So I guess the solution was in the forums after all =\

---

