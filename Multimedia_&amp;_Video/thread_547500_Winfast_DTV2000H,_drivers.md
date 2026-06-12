---
title: "Winfast DTV2000H, drivers??"
date: 2007-09-10
forum: Multimedia &amp; Video
---

### Post by rockyd on 2007-09-10
Hi there,
Just wondering if anyone has found any info or howto on getting the analogue TV and FM Radio going with this card. I have the DTV part going ok, with the Mercurial drivers and Kaffeine, but everytime I try to search for info and getting the analogue and FM going I hit a deadend.

---

### Post by nikoPSK on 2007-09-26
I'll look into it. But I have a winfast TV200 Xp series and don't know what to use for watching the tv on (program) and drivers.:(

---

### Post by JDahl on 2007-11-06
I have the same card, and it seems to be detected correctly by the kernel.

I only have analog TV via cable (TDC in Denmark),  and in WinXP it doesn't 
matter if I use the ANTENNA or CABLE input,  both works.  Under Linux I have
never been able to detect any channels neither with tvtime or mythtv.

Any confirmations that the analog tuner part of the card actually works in
Linux?  Also, what would the correct input be and is it possible to choose
between them in Linux?  

- joachim

```
joachim@joachim-pc:~$ dmesg | grep cx
[   60.468479] cx2388x v4l2 driver version 0.0.6 loaded
[   60.468584] CORE cx88[0]: subsystem: 107d:665e, board: WinFast DTV2000 H [card=51,autodetected]
[   60.502427] cx2388x cx88-mpeg Driver Manager version 0.0.6 loaded
[   60.614822] input: cx88 IR (WinFast DTV2000 H) as /class/input/input2
[   60.614857] cx88[0]/0: found at 0000:02:01.0, rev: 5, irq: 20, latency: 64, mmio: 0xfb000000
[   60.867250] tuner 1-0061: chip found @ 0xc2 (cx88[0])
[   60.873068] tuner 1-0063: chip found @ 0xc6 (cx88[0])
[   60.873240] cx2388x alsa driver version 0.0.6 loaded
[   60.952606] cx88[0]/0: registered device video0 [v4l2]
[   60.952648] cx88[0]/0: registered device vbi0
[   60.953443] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   60.953718] cx88[0]/2: cx2388x 8802 Driver Manager
[   60.953748] cx88[0]/2: found at 0000:02:01.2, rev: 5, irq: 20, latency: 64, mmio: 0xf9000000
[   61.005761] cx2388x dvb driver version 0.0.6 loaded
[   61.005765] cx8802_register_driver() ->registering driver type=dvb access=shared
[   61.005769] CORE cx88[0]: subsystem: 107d:665e, board: WinFast DTV2000 H [card=51]
[   61.005772] cx88[0]/2: cx2388x based dvb card
[   61.043962] DVB: registering new adapter (cx88[0]).
```

---

### Post by nikoPSK on 2007-11-06
nvm I got mine working.... n record option though in the program Im using...:(

---

### Post by beefbowel on 2007-11-11
what did you do to get it to work?

---

