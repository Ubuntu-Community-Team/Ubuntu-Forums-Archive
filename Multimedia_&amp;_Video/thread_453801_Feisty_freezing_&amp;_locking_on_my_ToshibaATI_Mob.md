---
title: "Feisty freezing &amp; locking on my Toshiba/ATI Mobility Radeon 9000 IGP"
date: 2007-05-24
forum: Multimedia &amp; Video
---

### Post by seedainvisible737 on 2007-05-24
hey, I have a Toshiba Satellite a75-s231 and I dual boot using GRUB Fiesty. It works fine untill after about 20 mins. the sytem freezes and doesn't respond. Ihave to press an dhold my pwr button to get it to shut down then reboot. as you can imagine this is very frustrating. I tried fiesty on a IBM T22, and it works great, minus the desktop graphics becuase it can't handle it. the Ibm only has an 8MB video card. but the my issue is with my Toshiba satellite, it has an ATI Mobility Radeon 9000 IGP(64MB) video card on it. the beryl and desktop graphics look very good. how ever. the system keeps. I've also noticed that when it crashes I can still move the mouse. when i move th emouse the hourglass only rotates on the mouse when i move the mouse. normally, the hour hourglass rotates no matter what. Is my graphics card the issue or what?
Toshiba Satellite A75-s231
intel P4 3.333GHZ (it's real)
HD = 100GB
RAM = 768MB
ATI Mobility Radeon 9000 IGP(64MB)

Does any one have any idea why the system does this or why this happens. One further note, I did also try an earlier version of Ubuntu 6.06 & I don't have this problem. it only happens with the Ubuntu 7.04.

thanks a bunch,

---

### Post by U-Toto on 2007-05-25
Hi, I'm new 2 the U comm. Just installed Feisty on my Tosh A75-S125 carrying a P4 3.2Ghz 533Data BUS Speed with 1.5 Gigs pc2700 333Mhz RAM and the same ATI Radeon 9000 series graphics card. I did a dual-boot to my XP 100gb HDD in 4 seperate parts (WinXP Pro Sp2, Storage, Feisty Fawn 7.04, Swap). Grub works fine, but, when i get into Feisty it locks up/freezes. I do the same thing, hold down POW 2 shut off, and yes, I 2 have continuous mouse capabilities throughout. I only feel slightly better that I'm not the only one having this trouble, but, not much. Is yours a single boot machine or a dually as well? Ubuntu did download updates just after installing, 13 I believe. perhaps that could help. Yet, I don't know how to access them yet to remove. :?

---

### Post by matt_tee on 2007-05-28
Hi, 

I have a Toshiba p30-135 with ATI Mobility Radeon 9700 - AGP 8x, same problem, runs for about 5 minutes, then freezes. have to power off, then power back on. any ideas?

---

### Post by matt_tee on 2007-05-31
I am going to try linux mint tommorow, maybe that might solve the problem...

Or maybe K.D.E

---

### Post by se2131 on 2007-06-04
Try this (I have a Toshiba A75): [http://ubuntuforums.org/showpost.php?p=2528532&postcount=10](http://ubuntuforums.org/showpost.php?p=2528532&postcount=10)

---

### Post by seedainvisible737 on 2007-06-05
Hi, that does sound familiar.  I do notice that whe the GRUB starts to boot the fiesty that the bios gives an error when it boots.  it will try the link a later. 
---------
on another note:

          I will say that as a test, I did a completely new installation of the 6.06 and  upgraded all the way up to the Feisty(7.04),  And took notice that the freezing was not there. still had the bios error after all upgrades.  never looked while on the older kernels.  So basically, if I start from old and upgrade to new, I'm fine.  But, If I use a live cd, it freezes/Lock.   (Very Frustrating).  and Yet even after all the updates, I have an old IBM T22 thinkpad that to this day ha snot failed running Feisty.  I think it might be the bios or something from Toshiba(Hardware).  on my IBM, I first installed Dsl to the hard drive.(30G)  then did the installation from the live cd. since then no issues. the only time i had issues was when i did something wrong.  

I just thought i would note that to see if it will be helpful. I know it's the long route, but it's a try.

what i would recommend if you're unsure or new is to upgrade from 6.06>>>>>>7.04(Feisty),  If you have no issue with a million kernels installed on your system you are good. Other wise try the link from earlier about the Bios Timing error.:p

---

### Post by seedainvisible737 on 2007-06-05
just answer the other questions, Yes it is a Dual system on my Toshiba. Not on my IBM T22 that is running Feisty, it's on the entire hard drive.

---

### Post by seedainvisible737 on 2007-06-05
when you execute this add on, do you restart. the system?  judging from the page it doesn't seem perminent.  will i need to edit the the file and restart or only one time is good.

thanks, 
:?

---

### Post by se2131 on 2007-06-05
You'll have to restart after editing the GRUB menu file for it to be effective (and it'll be permanent).  You can check if the changes stuck by pressing the 'e' button when you have your kernel highlighted in GRUB, and make sure that noapic is listed in the parameters

---

