---
title: "Help Configuring TVTime"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by karishbhr on 2007-03-01
I have the Winfast tv2000 xp tuner on my system.  Device manager recognizes it as a bt878 video and audio capture card.  I installed TVTime from synaptic and run it it says no signal.  I have no clue what I am doing here, how do I even know if tvtime is using the right card?  Total newb so please

---

### Post by Jose Catre-Vandis on 2007-03-01
This link takes you to the common problems area for tvtime.

[http://tvtime.sourceforge.net/problems.html#undetected](http://tvtime.sourceforge.net/problems.html#undetected)

try out what is says there, quite possibly your setup is not loading the right driver?

Also, did you wait for all the channels to be scanned (on my Pc @ 140, and nothing happened until 89!)

---

### Post by karishbhr on 2007-03-01
I dont even understand how to check which drive tvtime is pulling up.

---

### Post by Jose Catre-Vandis on 2007-03-02
Let's start at the beginning.

Where are you in the world?

What Tv format does your region have?

When you run tvtime, do you get a blue screen and channel numbers?

Open a terminal, type:
```
 dmesg > dmesg.txt
```

Either open this text file (in your home directory) and copy and paste here, or simply attach file to post.

The Deluxe version of your card for NTSC is tuner=2, so you might be that, or 3 if PAL/Secam

---

### Post by laffys on 2007-03-06
Well I have the same problem, and here are my results;

[17179588.412000] bttv0: Bt878 (rev 17) at 0000:00:0b.0, irq: 217, latency: 32, mmio: 0xea025000
[17179588.412000] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
[17179588.412000] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
[17179588.412000] bttv0: gpio: en=00000000, out=00000000 in=003ff502 [init]
[17179588.412000] bttv0: using tuner=5
[17179588.412000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179588.412000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179588.412000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179588.412000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179588.456000] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[17179588.456000] tuner 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[17179588.464000] bttv0: registered device video0
[17179588.468000] bttv0: registered device vbi0
[17179588.468000] bttv0: registered device radio0
[17179588.468000] bttv0: PLL: 28636363 => 35468950 .. ok
[17179588.500000] input: bttv IR (card=34) as /class/input/input2

Any help to get tvtime to work would be much appreciated, too.


Actually just got it to work , the video that is but no sound :((

---

### Post by Jose Catre-Vandis on 2007-03-06
laffys

what tv system are you using?

For sound, you might need a cable from the card to the motherboard, or check you sound settings for devices and adjust the settings in there

---

### Post by laffys on 2007-03-06
got the video part working but no sound. i'll try the direct cable hook up to see if i get sopund.

---

