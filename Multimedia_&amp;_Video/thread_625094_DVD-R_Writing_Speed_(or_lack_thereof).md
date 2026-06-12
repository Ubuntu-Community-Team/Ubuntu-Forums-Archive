---
title: "DVD-R Writing Speed (or lack thereof)"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by Blairboy on 2007-11-27
I know this has been brought up before, but I haven't seen a solution to it as of yet.  I have a lg 16x dvd-r drive which is limited to 4x write speed in ubuntu.  I have dma enabled so that is not the issue.  I have tried it in multiple writing software, including nero linux, so I know its an os problem.  Does anybody have a solution to this mess?

---

### Post by Blairboy on 2007-11-27
Bump.

---

### Post by mc4man on 2007-11-27
What app are you using to burn and are you still using drake?

---

### Post by Blairboy on 2007-11-27
Checked it under k3b, gnome writing tools, nero linux, and I'm running gutsy.

---

### Post by WiFi Ed on 2007-11-27
My dvd/cd burner reports 4x as maximum in Nero at first, but when I place a blank disc in the burner it reports the correct speed of 48x. I don't know if you're experiencing the same phenomena, but could be...

---

### Post by mc4man on 2007-12-01
Don't know if this is still an issue for you, myself I always use ImgBurn (in wine). i think it's the best burner and certainly won't limit your burn speed. (burning at max is usually not the best idea)

edit: assuming dvd burning

---

### Post by bthoward on 2007-12-02
I only have had an issue with a certain spindle of Sony DVD-R's that I can't burn.  It just fails to ever even start.  But then I can take that same disk and burn it just fine in my wife's laptop (under windows).  But I bought another spindle of Memorex discs and I have no troubles with those.

---

### Post by Mcavity on 2007-12-02
I have a similar problem. 
I can burn cd's at full speed no problem but dvd media burns quite slowly [20 min to burn a 3 gig disk] however if I boot XP [I'm dual boot] I can but the same files media in about 6-8 min. 
this happens even if I tell the software to burn at full speed.

---

### Post by zepski on 2008-04-14
I also am having this problem.  I've tried Brasero, K3B, nero and all 3 will burn a cd at max speed but when i try to burn a dvd it maxes out at 4.0x.

I know that its not a setting because i have tried setting the burn speed at everything from 4x to 18x and have tried 3 different brand cds.  If i boot to windows i can burn at any speed i select no problems.

I've not tried another distro on the machine but from what i can tell it seems to be an ubuntu thing.


DMA is set properly 
```

hdparm -i /dev/hdc

/dev/hdc:

 Model=TSSTcorpCD/DVDW SH-S182M, FwRev=SB05, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no

 * signifies the current active mode

```

---

