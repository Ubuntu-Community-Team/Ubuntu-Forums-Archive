---
title: "Dell Inspiron 8200 with Broadcom 1180 wireless card"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by pteron on 2006-07-09
I have an Inspiron 8200 laptop, dual-booting Windows XP and Ubuntu. I'm trying to get my wireless card to work. From System > Administration > Networking, the network card could not be activated, and this appears to be due to requiring ndiswrapper, and not having the correct driver for it. I've installed ndiswrapper, and searched for the driver required for a Broadcom 1180 internal wireless card (Ubuntu device ID BCM4303). According to the list of ndiswrapper supported cards in Ubuntu, the BCM4303 is only installed on an HP computer, and the driver must be obtained from that CD (which I wouldn't have). There is a specific entry for the Broadcom internal wireless card for the Inspiron 8200, but installing the driver referenced does not work. Has anyone else had this issue/does anyone have any ideas?

---

### Post by clawrence on 2006-09-11
I am running the same setup and am having similar problems.  I will post specifics tonight when I am at the computer again.  

Everything appears to work on installation, it shows up as eth1, i believe, but will not pickup any signal at all.  I am beginning to get frustrated.  I did the installation via terminal, and later added the graphical to verify everything was ok, which it was.  I used bcmwl5.inf, as i recall.

Like i said, i will post again later with specifics.

---

### Post by Olzen on 2006-09-21
Any solution to this one? Have the same problem on Inspiron 8200.

Regards
O

---

### Post by mgolden on 2006-09-21
I suspect you need the latest version of ndiswrapper.  See the bottom of this post here:

[http://unia.ual.es/socios/pexi//?q=node/8](http://unia.ual.es/socios/pexi//?q=node/8)

I have the card working, but I can't get it to work with WPA.

---

