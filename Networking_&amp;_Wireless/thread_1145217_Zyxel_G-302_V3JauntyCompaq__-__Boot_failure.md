---
title: "Zyxel G-302 V3/Jaunty/Compaq  -  Boot failure"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by Gert-Jan on 2009-05-01
Hi All,

I'm a noob concerning Ubuntu but I did manage to install the 9.04 version without problems :).
However, when I boot my system with my wifi-card plugged Ubuntu fails to boot :confused:

Details:
System: Compaq EVO D510 CMT
             Pentium 4 processor (2400 MHz)

Wifi-card: Zyxel G-302 V3 802.11g PCI adapter
               3.3V 32-bit PCI v2.2
[updat] Chipset: Realtek 8185L

Hope anyone can help me out :(

---

### Post by ranch hand on 2009-05-06
I saw your link over on Jaunty experiences.  Don't know a thing about wireless but I see you have had this up for a while.

Why don't you check over at;

[http://www.linuxquestions.org/](http://www.linuxquestions.org/)

They are sometimes better at hardware questions.  This is my main source but they are #2.  With my son they are #1.

I would also run a net search for your card in relation to Ubuntu.  It may already be out there.

Welcome to Ubuntu, Jaunty and ext4 are great (even if I still use Hardy for my main data -I like LTS).  I am on Jaunty now (trying Stoner Edition :-D).

---

### Post by Gert-Jan on 2009-05-06
Thanks for the tips!

In the mean time I did find that there are people that are using this Zyxel wireless card with Ubuntu (should be working with Ndiswrapper) and I followed the installation process but still: the moment I put the card in the computer Ubuntu fails to boot... :(

The search continues...

---

### Post by ranch hand on 2009-05-06
I would put the card in the box, boot from the LiveCD and configure the driver from there.  This may stop the boot freeze problem.

---

### Post by Gert-Jan on 2009-05-08
Hi ranch hand,
I might try that but I found another solution that works :cool:
Got my hands on a Siemens Gigaset USB 108 card which works with ndiswrapper without any problems. Try the other one some time on a rainy sunday afternoon ;-)

Anyway, thanks again for your effort to help me.

---

### Post by ranch hand on 2009-05-08
I have read about quite a few people with wireless problems.  Seems to me that the thing to do now that the thing is working is let it be.

I may just be too old but the security of wilreless scares me.

---

### Post by Gert-Jan on 2009-05-08
Well, you may be right but I would like to try it for fun. I might be able to help someone else with it...

---

### Post by ranch hand on 2009-05-08
I sure can't argue with that.  i started multi booting to avoid breaking the OS we USE.

I dual booted Hardy/Hardy.  One to play with and one we still use as our "primary".  I actually use Jaunty most of the time.  If there is something we want to keep, business and such, it is still that partition that we use.

One thing you may like to know is that you can copy a partition with gparted.  It will need the /boot/grub/menu.lst edited so that it will boot from where you put it but it works quite well if the partition you are copying is good.  Nice backup if you want to try something that may break things.

---

