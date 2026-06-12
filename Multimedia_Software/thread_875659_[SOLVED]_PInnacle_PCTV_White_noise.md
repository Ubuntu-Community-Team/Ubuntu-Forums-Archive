---
title: "[SOLVED] PInnacle PCTV White noise|"
date: 2008-07-31
forum: Multimedia Software
---

### Post by spacetree on 2008-07-31
Hi there:

I'm using the PInnacle PCTV TV tuner (not pro, not rave, just plain PCTV) And I can clearly watch TV, but the sound coming out the tv card is just white noise. I have been looking in the google and tried changing the bttv module parameters, with no success on getting good audio. I dont know if i should change my tuner type or what. I hope someone can help me. Here is some info about my system, and dmesg.

with /etc/modules.d/options set to "options bttv card=39 tuner=33" which is the default (just typed the options to get sure about autodetection, and actually got same results)

saeioul@saeioul-desktop:~$ dmesg | grep bttv
[   39.466400] bttv: driver version 0.9.17 loaded
[   39.466412] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   39.466789] bttv: Bt8xx card found (0).
[   39.466873] bttv0: Bt878 (rev 17) at 0000:01:0b.0, irq: 11, latency: 66, mmio: 0x40100000
[   39.466909] bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
[   39.466916] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,insmod option]
[   39.466961] bttv0: gpio: en=00000000, out=00000000 in=00ffefff [init]
[   39.467419] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   39.468078] bttv0: pinnacle/mt: id=5 info="NTSC / mono" radio=no
[   39.468084] bttv0: tuner type=33
[   39.468092] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   39.468690] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   39.469300] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   40.051963] bttv0: registered device video0
[   40.052020] bttv0: registered device vbi0
[   40.052071] bttv0: PLL: 28636363 => 35468950 .. ok
[  144.425013] bttv0: PLL can sleep, using XTAL (28636363).

lspci -v -nn

01:0b.0 Multimedia video controller [0400]: Brooktree Corporation Bt878 Video Capture [109e:036e] (rev 11)
	Subsystem: Pinnacle Systems Inc. PCTV pro (TV + FM stereo receiver) [11bd:0012]
	Flags: bus master, medium devsel, latency 66, IRQ 11
	Memory at 40100000 (32-bit, prefetchable) [size=4K]
	Capabilities: [44] Vital Product Data
	Capabilities: [4c] Power Management version 2

01:0b.1 Multimedia controller [0480]: Brooktree Corporation Bt878 Audio Capture [109e:0878] (rev 11)
	Subsystem: Pinnacle Systems Inc. PCTV pro (TV + FM stereo receiver, audio section) [11bd:0012]
	Flags: medium devsel, IRQ 11
	Memory at 40200000 (32-bit, prefetchable) [size=4K]
	Capabilities: [44] Vital Product Data
	Capabilities: [4c] Power Management version 2

Thanks in advance

---

### Post by spacetree on 2008-07-31
Solved.

Misteriously , I got rid of the problem unloading and loading the driver module (??) . I even made some script for rc.local and voila. Anyway it stills get a little picky (if the signal is not fairly good, it mutes the sound and sometimes you can get sound only after unplug-plugging the cable to the audio jack)

sudo mousepad /etc/init.d/fixTv.sh 

Put this in the script:

rmmod bt878
rmmod bttv
modprobe bttv


make it executable ( chmod +x )

and then

sudo update-rc.d fixTv.sh defaults

---

### Post by vatsok on 2008-10-22
**Thank you so much** spacetree! You are great. This worked fine after rebooting.
:)

---

### Post by Fitch on 2010-01-21
Sorry to be a bore, I too have a Pinnacle PCTV card (but it's a Rave)
It too uses card=39 and tuner=33, and I too get white noise.

I tried the method you used, to no avail.

I don't suppose you have any ideas?
The thing seems to default to PAL B/G, at 5.5MHz, which is a shame as the UK PAL is "I" at 6.0MHz.

---

### Post by spacetree on 2010-01-22
> **Fitch said:**
> Sorry to be a bore, I too have a Pinnacle PCTV card (but it's a Rave)
It too uses card=39 and tuner=33, and I too get white noise.

I tried the method you used, to no avail.

I don't suppose you have any ideas?
The thing seems to default to PAL B/G, at 5.5MHz, which is a shame as the UK PAL is "I" at 6.0MHz.
Sorry, Fitch. 

In fact I have no idea of how could we solve your problem. Maybe trying other settings in the module settings?

Maybe there is documentation showing the correct settings for each card.

---

