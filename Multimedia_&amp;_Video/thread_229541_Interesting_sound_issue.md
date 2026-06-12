---
title: "Interesting sound issue"
date: 2006-08-04
forum: Multimedia &amp; Video
---

### Post by zygmore on 2006-08-04
Okay, I did a fresh install of 6.06, and then updated the system.  After I restarted, the sound sounded like a broken record.  Not sure exactly what the problem could be.  If anyone could help me it would be greatly appreciated.

---

### Post by tedwardo2 on 2006-08-04
I think I have the same problem.  Did your sound work before you updated?  My sound was fine ever since I installed 6.06 a couple of month ago.  One of the updates in the last week or two made my audio really distorted (it may have been the kernel update).  It sounds like all my audio is being played through some really crappy speakers that can't handle lows.  And it sounds like this from my laptop speakers or when I plug nice headphones in.

Does anyone have any suggestions?  I tried reinstalling ALSA like the "Comprehensive Sound Problems" thread suggested and that didn't work.

---

### Post by tedwardo2 on 2006-08-04
Woops!  I feel like an idiot.  The only problem was that my PCM volume was at 100%.  So I just turned it down to 80% or so in the Alsa mixer and everything sounds great now!  I hope that was your problem, too, zygmore.

---

### Post by zygmore on 2006-08-05
Unfortunately that is not my problem...  What it does is sound like a broken record playing a couple milliseconds worth of music over and over again and slowly making it's way to the end of the sound byte it is having to play.

---

### Post by philhinz on 2006-08-06
I have this same problem.  The sound works with the 6.06 Live CD but not with  my installed version.  It seems to have broken in the last couple weeks during one of the updates.

Do you have a VIA 8237 device, or is it something else?

---

### Post by jstingray on 2006-08-06
I had all my sound working fine until the last set of updates, now my sound card isn't even detected! I've been thru all the steps in the comprehensive sound posting, but to no avail. I resorted to going back seceral kernals in GRUB un til I found one that sees my sound card. I'm running an AMD athlon 74 bit with Sound Blaster Live! 24 bit sound card. Any body have any ideas?

---

### Post by philhinz on 2006-08-06
I went back and checked which kernel broke the sound.  The sound works fine for 2.6.15-25-386.  When I upgraded to 2.6.15-26-386 the "record skipping" sounds started.  I guess for the moment I can just use the older kernel.

---

### Post by zygmore on 2006-08-07
It is a VIA chipset... not sure which chipset exactly at the moment...  But I'll have to try downgrading the kernel...  Hopefully that will work.

---

### Post by zygmore on 2006-08-07
Downgrading worked... Thank you for the tip philhinz.

---

### Post by rck_hitokiri on 2006-08-07
how did you downgrade?

---

### Post by zygmore on 2006-08-07
I just uninstalled the newer kernel so it would revert to the older one installed on the machine...  not sure if it was the correct way to downgrade, but it worked for me.

---

### Post by philhinz on 2006-08-15
It can be even easier.  During bootup there is a point where grub loads the latest kernel.  If you interrupt the process at this point you can just choose the previous kernel.  Or by editing /boot/grub/menu.lst to change the default loaded kernel you can make it automatically choose a previous kernel during bootup.

---

