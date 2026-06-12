---
title: "TV card troubles"
date: 2008-10-20
forum: Multimedia Software
---

### Post by 4t0m1c_w07f on 2008-10-20
I have a random Yodata Tv card that I recently bought.. lspci shows that it is: ```
05:00.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
```

and dmesg says:
```
dmesg | grep saa7130
[   61.497737] saa7130/34: v4l2 driver version 0.2.14 loaded
[   61.497924] saa7130[0]: found at 0000:05:00.0, rev: 1, irq: 21, latency: 32, mmio: 0xfa100000
[   61.503768] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   61.513250] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   61.513308] saa7130[0]: board init: gpio is c04000
[   61.614442] saa7130[0]: Huh, no eeprom present (err=-5)?
[   61.614545] saa7130[0]: registered device video0 [v4l2]
[   61.614608] saa7130[0]: registered device vbi0
[   62.648966] saa7130[0]/alsa: saa7130[0] at 0xfa100000 irq 21 registered as card -2

```

I can't do anything with it...
MythTv doesnt work and no other program picks anything up..

Please can anyone help me through this problem?

---

### Post by Afkpuz on 2008-10-20
If there is a v4l driver for your card (which it looks like it), vlc should work.

---

### Post by 4t0m1c_w07f on 2008-10-21
> **Afkpuz said:**
> If there is a v4l driver for your card (which it looks like it), vlc should work.

How do I tell vlc to use the tv card?

---

### Post by wolfen69 on 2008-10-21
open vlc, file>open capture device>video4linux>ok

you can also try file>open capture device>pvr>ok

someone else will have to tell you how to change channels though.

---

### Post by 4t0m1c_w07f on 2008-10-21
> **wolfen69 said:**
> open vlc, file>open capture device>video4linux>ok

you can also try file>open capture device>pvr>ok

someone else will have to tell you how to change channels though.

It does nothing... :(

---

### Post by wolfen69 on 2008-10-21
i know this won't help you now, but did you do any research into the linux compatibility of the card before you bought it? this is important to remember. if you can not get it going, and can still return it, i would do so.

---

### Post by Afkpuz on 2008-10-21
Make sure you get the video device name correct in vlc.  Your tuner might be /dev/video0 or /dev/video1

I use a haupauge pvr500-mce mythtv works great with it.  Generally, any haupauge card will work very well with linux.

---

### Post by 4t0m1c_w07f on 2008-10-22
Finally the card is working and the only problem to still solve is that when i scan i get no signal... I live in south africa and my frequency table is set to southafrica.. My tv picks up signal but not my tv card...

---

### Post by 4t0m1c_w07f on 2008-10-22
After I launch the tvtime-scanner it searches for any signal from frequencies 44.00 MHz to 958.00 MHz and when its done, still no signal...

---

### Post by 4t0m1c_w07f on 2008-10-23
Please Help

---

### Post by cariboo on 2008-10-23
You have to create a file with the following contents:

```
options saa7134 card=42 tuner=17 
```

Call the file whatever you want then copy the file to /etc/modprobe.d then you have remove the saa7134 module and reinsert it:

```
sudo rmmod saa-7124
```

to remove

```
sudo modprobe saa-7134
```

to insert. If you see no output in either case then the command worked.

I use TvTime to watch TV, but the latest version of vlc works just as well. TvTime has more configuration by right-clicking anywhere on the screen.

Jim

---

### Post by 4t0m1c_w07f on 2008-10-23
Your settings didn't even pick up the card but these did: 

> In Terminal type:

```
sudo gedit /etc/modprobe.d/options
```

Enter your password.

Then add the following line to the bottom of the file:
```

options saa7134 card=81 tuner=54
```

Restart the computer. Then in Terminal type:

```
tvtime-scanner
```

You should be able to tune channels.

I just cant pick up signal on any of the frequencies even though the tv cable works perfectly in a tv.

---

