---
title: "Trouble with AMD Radeon HD 8670M hybrid system"
date: 2013-12-25
forum: Multimedia Software
---

### Post by Azrael84 on 2013-12-25
I have a hybrid graphics system with a discrete AMD Radeon HD 8670M card and in built Intel HD. 
I seem to be experiencing a number of problems that I think may be due to these cards, and the fglrx drivers.

I don't need high performance graphics and I think the Intel card alone would suffice for my needs, is it
possible to just disable the Radeon and use the intel HD solely with the i915 driver?
If I just purged fglrx will that kill my system or  will it gracefully revert to just the intel driver?

I don't think the open source Radeon drivers support this card, so there
is no option other than the proprietary fglrx (although maybe I'm wrong?).
The fglrx 13.10.10 experimental driver was installed by jockey, when I installed
Ubuntu 12.04.3 a few days ago.

I used the AMD Catalyst control centre to disable the "High performance card"
and switch to the "Low performance battery saving card",  and it got rid of one of
my problems (an occasional blue screen flicker), but still leaves me with quite a few:
mostly crashes, and system freezes...such as when I logout, or when I leave the laptop
unattended and the screen dims etc.

I can post some logs with the fglrx related errors if anyone thinks it will help...

many thanks

---

### Post by Bashing-om on 2013-12-26
Azrael84; Hi !

This huge thread devoted to your situation.
[http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics](http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics)

Sure to find some guidance therein or from.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by Azrael84 on 2013-12-26
Thanks. Yes, I had come across that thread on my quest...It is a very interesting read, but I'm not sure if it helps me too much.

For my card (Radeon HD 8670M +Intel iGPU), I don't believe the open source drivers are available (happy to be corrected), and during installation of Ubuntu, jockey already installed the fglrx drivers and AMD Catalyst control centre (amdccc). I used this to flip from the discrete GPU to the intel GPU, and indeed it seems to have fixed a couple of problems (blue flash line) but left some still (freezing occasionally, and odd error messages in syslog).

What I'm confused about is: if the intel card is driven by the i915 driver (as stated by lshw -C video), why do I even need the proprietary fglrx or open source driver for the AMD card? Can't I just get rid of both, and use the Intel card alone with just the i915 driver? (or is the fglrx still required for some reason?)

---

### Post by johnnyis on 2014-03-03
Both the 13.12 and 14.2 beta Catalyst Display Drivers list supporting the HD 8000M series. [http://support.amd.com/en-us/download/desktop?os=Linux%20x86_64](http://support.amd.com/en-us/download/desktop?os=Linux%20x86_64)

I haven't tried them yet, still working through a few other issues getting a system with an AMD A10-5750M + HD 8670M set up dual booting and past the "low graphics mode" hangup. Most of the info I find seems only to be for Intel/AMD hybrids, not AMD + AMD switchable graphics systems. 

I'll try to remember to post back here if I have any luck with the Catalyst drivers and the 8670M

---

### Post by aris2 on 2014-05-25
@johnnyis

My system also is AMD A10-5750M + HD 8670M, so I was wondering if there is a good thread where I can learn how to setup the graphics. Reason is, I read somewhere about overheating issues. Don't know if it applies to mine as well but better safe than sorry

---

