---
title: "FlyTV Prime 34 FM PAL"
date: 2008-07-05
forum: Multimedia Software
---

### Post by dkc10 on 2008-07-05
Hi, i'm trying to install FlyTV Prime 34 FM (FlyVideo 3000 FM) TV&FM Tuner. I loaded (sudo modprobe) saa7134 card=2 but i need to know what is the id of my tuner sudo modprobe saa7134 card=2 tuner=??.
I Have the PAL/Secam version of FlyVideo 3000 FM. I searched the forum but there are threads only for the NTSC version. Also i need to know which Frequency Table to use (I'm in Cyprus)

The program i use is TV Time.

---

### Post by cariboo on 2008-07-05
I got a tv card based on the same chip when the modules is loaded with the correct card number the tuner is automatically loaded. here is the pertinent part of dmesg:

```
[12667.856854] tuner-simple 2-004b: creating new instance
[12667.856863] tuner-simple 2-004b: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[12667.866654] saa7133[0]: registered device video0 [v4l2]
[12667.866654] saa7133[0]: registered device vbi0
[12667.889653] saa7134 ALSA driver for DMA sound loaded
[12667.890734] saa7133[0]/alsa: saa7133[0] at 0xfebff800 irq 17 registered as card -2
```

I'm using card number 17, It shows as an Aopen VA1000 even though it an MSI TV@nywhere Plus.

Jim

---

### Post by dkc10 on 2008-07-05
The VendorID of FlyTV is the same with Aopen's one but only using card=2 i'm able to use the tv tuner. I set tuner = 55 (T-*something* 2000MB PAL/SECAM) and with *tvtime-scanner -n secam* i get this
```
Found a channel at 103,75 MHz (103,50 - 103,75 MHz), adding to channel list.
Found a channel at 126,50 MHz (126,25 - 126,50 MHz), adding to channel list.
Found a channel at 216,25 MHz (216,00 - 216,25 MHz), adding to channel list.
...
```
But i can not see TV with any program.
Using PAL i get No Signal. 

The tv system in my country is PAL but the only channels i was able to find are in SECAM.

---

