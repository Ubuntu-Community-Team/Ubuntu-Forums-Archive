---
title: "Mythbuntu 8.10 w/ Hauppauge WinTV Go"
date: 2008-12-14
forum: Multimedia Software
---

### Post by fattmox on 2008-12-14
This article is designed to help those who are setting up Mythbuntu with a Hauppauge WinTV Go card and are having problems getting audio off the card.

Background:
This has not been a smooth road. This is the the fourth mythbuntu box I have built and all but 1 were somewhat difficult.

The latest is a basic 1 Ghz Dell Pentium 3. I stuck in a cheapo Hauppauge WinTV Go and went off installing. Man there are a lot of wires coming out of the back of this thing.

I'm happy to say that I have the machine in an operating state that I am content with. Ideally I wanted this install to operate simalarly to my previous Mythbuntu system that used an ATI TV Wonder with the same brook tree chipset. It is configured to capture both video and audio from the card. I was not able to do this with the WinTV card.

I tried my hardest to get audio from /dev/dsp1 for hours!
I finally gave up and tried for the patch cord method fearing that the audio would be totally out of synch.

In the end, it works and the audio is in synch for live tv and recordings. This is how I did it.

After digging around on google the best thing I could come up with was this:
[http://ubuntuforums.org/showthread.php?t=626282]("http://ubuntuforums.org/showthread.php?t=626282")

It explained patching the line out from the tv card into the mic in on the sound card. So this is how I interpretted it.

First I changed the Capture Card settings in the Mythbuntu back end settings to capture audio from my sound card: /dev/dsp (instead of the tv card - /dev/dsp1).
Then I patched TV card line out to sound card mic in.
I then used gnome-alsamixer (had to apt-get install it) to inspect the sound card settings.
I muted the Mic and checked Rec
A suspicious setting at the far right 'Capture' I also checked Rec
After doing this I got synched audio for live TV and recordings.

I have since played with the settings and unchecking Rec under Mic does not mute the sound of live TV. If I uncheck Rec under 'Capture' then after a few seconds the audio cuts out. This is all very strange and counter intuitive. It seems that the TV card depends on an audio card and appends a 'capture' device to it. I imagine that it is in fact something like a symbolic link that points to the tv card settings from the sound card settings.

Hopefully this helps someone and saves them the whole day it took me to get this baby up and running.

Alright time to sit back and watch some shows with no commercials! woot! :popcorn:

---

### Post by jrjackso on 2009-01-17
My setup:
Dell Dimension 4500 (2.0ghz)
512mb ram
Hauppauge WinTV-Go-Plus
Nvidia fx5500 256mb
SB Live!
Mythbuntu 8.10

Had some trouble getting audio to work initially and if it helps anyone here is what I did:
[LIST=1]
[*]Patch line out of WinTV-Go-Plus to line in of SB Live!
[*]alsamixer -V capture
[*]Leave AC97 at 80
[*]Set Capture to 80
[*]Set Line to CAPTUR (i.e. spacebar)
[*]Quit (q)
[*]alsamixer
[*]Set AC97 to 0
[*]Set Line to mute (m)
[*]Set PCM to 81
[*]Set Master to 81
[/LIST]

```
jrjackso@pvr:~$ dmesg | grep bttv
[   13.011750] bttv: driver version 0.9.17 loaded
[   13.011756] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   13.011865] bttv: Bt8xx card found (0).
[   13.011891] bttv 0000:02:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.011907] bttv0: Bt878 (rev 17) at 0000:02:02.0, irq: 18, latency: 64, mmio: 0xf47fe000
[   13.011930] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   13.011935] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   13.011974] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[   13.014465] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   13.067393] bttv0: Hauppauge eeprom indicates model#44981
[   13.067398] bttv0: tuner type=50
[   13.067403] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   13.405464] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   13.406085] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   13.882388] bttv0: registered device video0
[   13.882452] bttv0: registered device vbi0
[   13.882478] bttv0: PLL: 28636363 => 35468950 .. ok
[   36.378238] bttv0: PLL can sleep, using XTAL (28636363).

```

---

### Post by facethemusic on 2009-01-18
I'm an abject newbie trying to configure a Hauppauge HVR-1800 with MythBuntu 8.10 on my new Intrepid Ibex machine. The v4l drivers are there, the Mythbuntu backend probes successfully for the card, but once in the LiveCD front end, the "test connection" results in failure. I try to start a session and get "No UPnP backends found". So it doesn't seem to be connecting to the hardware. And I have no idea what UPnP is.

I've searched in vain for an intallation troubleshooting article but there just is no comprehensive guidance, and I'm going nuts. Any suggestion would be much appreciated.

---

### Post by appsmanster on 2009-01-22
No UPnP backends found.

This usually refers to an address issue. Make sure the address for the backend is the one that the frontend is looking for.

---

### Post by sjd1980uk on 2009-04-27
Thanks fattmox, I have an old analogue WinTV card (BT848) which required an audio out to be plugged into a sound card, this worked find on the backend and I couldn't figure out why it wasn't sending it through to the frontend........ then I read your post, it really all is in the capture recording switch, i enabled this and now it works great.

Thanks would have taken me hours to work that one out!

---

