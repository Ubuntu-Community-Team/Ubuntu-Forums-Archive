---
title: "HP 2133 Via Chrome9 in Ubuntu 11.10 not recognized"
date: 2012-02-25
forum: Multimedia Software
---

### Post by Gazoda on 2012-02-25
I have been searching rufly 2 days now to get a solution for a clean install on my HP 2133 netbook with VIA CHrome9 chip. I am new to Ubuntu (I suppose in the end everyone gets sick of Micro$hit Windlbows sooner or later) and I have been following quiet a lot of instructions from other forums all over the net without any result.

Honestly I wont be doing anything out of the ordinary with this laptop, but since it is my only laptop I have if I am not on the road @ home i connect it with a 19 inch monitor. Since the clean install of Ubuntu i cant use my external monitor anymore. CHecking in the settings of video it shows that there is no driver assigned to it.

I dont want to go back to the paid version of OS, so there must be a solution for this.......anyone can help me out pointing me in the right direction?

Thanks a bunch......

---

### Post by BicyclerBoy on 2012-02-25
This looks to be the best how-to:
[https://wiki.ubuntu.com/LaptopTestingTeam/HP2133](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133)

but is for 10.04..

Good reading:
[http://en.gentoo-wiki.com/wiki/HP_2133](http://en.gentoo-wiki.com/wiki/HP_2133)

There are multiple via chrome drivers..but VIA have given up on their linux plans.
[http://www.phoronix.com/scan.php?page=news_item&px=OTAzMQ](http://www.phoronix.com/scan.php?page=news_item&px=OTAzMQ)
but did promise to open source the documentation.

So the current situation maybe better (docs) or worse (later *buntu & Xorg).

---

### Post by Gazoda on 2012-02-26
> **BicyclerBoy said:**
> This looks to be the best how-to:
[https://wiki.ubuntu.com/LaptopTestingTeam/HP2133](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133)

but is for 10.04..

Good reading:
[http://en.gentoo-wiki.com/wiki/HP_2133](http://en.gentoo-wiki.com/wiki/HP_2133)

There are multiple via chrome drivers..but VIA have given up on their linux plans.
[http://www.phoronix.com/scan.php?page=news_item&px=OTAzMQ](http://www.phoronix.com/scan.php?page=news_item&px=OTAzMQ)
but did promise to open source the documentation.

So the current situation maybe better (docs) or worse (later *buntu & Xorg).

Thanks BicyclerBoy, I had been looking around some more but most definately I could not find anything. So I decided to do a fresh install of 10.04. And now I did all the things to activate my screen, but guess what, after rebooting, It starts Ubuntu, but I dont get any screen. So it seems that my 3 year old laptop is seriously outdated for the support for Linux, which is a darn shame, the machine itself works just fine. :confused:

---

### Post by BicyclerBoy on 2012-02-26
Are you using the sample xorg.conf from wiki.ubuntu...?

Your 10.04 could be later version &/or did you allow network updates during install ?

There is a note at end of webpage about using grub boot option acpi=off.

Can you switch to console (& login) <ctrl>+<alt>+<F1> ?
If yes then post your 
/var/log/Xorg.0.log   file.

Via seem to have lost their way..They have the 3rd licence to make x86 CPUs & had low power CPU & GPU technology. So they could have owned the x86 netbook nettop market & could then have moved into smartphones etc..

The HP mini 110 atom 845 GME, that came after your model, has a worse screen & is power hungry & has the slowest SSD (pata) ever made.

---

