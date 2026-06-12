---
title: "[SOLVED] Pixelview PlayTv Mpeg2 M4900 TV Tuner Card Help"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by psavva on 2007-10-21
I've got the Pixelview PlayTv Mpeg2 M4900 TV Tuner Card and can't seem to get it working properly.
The problem is that the card is found, i can use tvtime to scan for channels, i've used tvtime-scanner to try scan for channels, but no channels come up.

This is the output of my dmesg.
```

[ 2879.663394] bttv: driver version 0.9.17 loaded
[ 2879.663413] bttv: using 8 buffers with 2080k (520 pages) each for capture
[ 2879.663485] bttv: Bt8xx card found (0).
[ 2879.663501] bttv0: Bt878 (rev 17) at 0000:02:01.0, irq: 21, latency: 32, mmio: 0xdc7fe000
[ 2879.663516] bttv0: detected: Prolink Pixelview PV-BT [card=72], PCI subsystem ID is 1554:4011
[ 2879.663522] bttv0: using: Prolink Pixelview PV-BT878P+9B (PlayTV Pro rev.9B FM+NICAM) [card=72,insmod option]
[ 2879.663554] bttv0: gpio: en=00000000, out=00000000 in=006fd8ff [init]
[ 2879.669661] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[ 2879.670716] tuner 0-0063: chip found @ 0xc6 (bt878 #0 [sw])
[ 2879.677377] bttv0: using tuner=5
[ 2879.677390] tuner 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[ 2879.677398] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[ 2879.701868] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[ 2879.710471] bttv0: registered device video0
[ 2879.710504] bttv0: registered device vbi0
[ 2879.710531] bttv0: registered device radio0
[ 2879.710557] bttv0: PLL: 28636363 => 35468950 . ok
[ 2879.724188] input: bttv IR (card=72) as /class/input/input9


```

Any Help will be greatly appreciated

---

### Post by psavva on 2007-10-21
After so long trying and testing the problem. 
I finally got the problem.
The tuner must be set to 69 for this model, the card must be set to 139, radio must be set to 1
here's the steps i took to solve this problem

Clear the device status so you can see what you're doing...

remove the bt878 driver which is used by bttv
 ```
sudo rmmod bt878 
```
remove the bttv driver
 ```
sudo rmmod bttv 
```
probe the device with these options.
```
modprobe bttv card=139 tuner=69 radio=1 
```
```
tvtime-scanner
```
set the frequecy table to custom in tvtime and voila :D

---

### Post by Mauriciobc on 2007-10-22
Okay, i knew that!

But how do we make these changes permanent?

---

### Post by psavva on 2007-10-23
To make these changes permanent you need to add this to your options file in modprobe.d
you can do this by following these steps
```

sudo gedit /etc/modprobe.d/options

```
Add this line to it
```

options bttv card=139 tuner=69 radio=1

```

Then reload the modules bttv
that can be done by following the steps mention on the first post

---

