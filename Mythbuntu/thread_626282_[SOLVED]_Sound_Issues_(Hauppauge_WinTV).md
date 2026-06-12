---
title: "[SOLVED] Sound Issues (Hauppauge WinTV)"
date: 2007-11-28
forum: Mythbuntu
---

### Post by spinlock99 on 2007-11-28
I'm trying to run the sound out from my capture card (Haupauge WinTV bt878/9) into my input on the mother board.  I'm getting poor results (i.e. very low volume sound when I watch TV).  

Any hints, tips, or tricks would be greatly appreciated.

Here's the interesting parts of dmesg:

[   46.103224] Linux video capture interface: v2.00
[   46.691204] input: PC Speaker as /class/input/input2
[   46.794009] bttv: driver version 0.9.17 loaded
[   46.794014] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   46.794079] bttv: Bt8xx card found (0).
[   46.794104] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.794118] bttv0: Bt878 (rev 17) at 0000:00:08.0, irq: 16, latency: 32, mmio: 0xf6011000
[   46.794128] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   46.794131] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   46.794167] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[   46.796648] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   46.824666] tveeprom 1-0050: Hauppauge model 44981, rev E199, serial# 8239512
[   46.824670] tveeprom 1-0050: tuner model is TCL 2002N 5H (idx 99, type 50)
[   46.824673] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   46.824676] tveeprom 1-0050: audio processor is None (idx 0)
[   46.824679] tveeprom 1-0050: decoder processor is BT878 (idx 14)
[   46.824681] tveeprom 1-0050: has no radio, has IR receiver, has IR transmitter
[   46.824684] bttv0: Hauppauge eeprom indicates model#44981
[   46.824686] bttv0: using tuner=50
[   46.824689] bttv0: i2c: checking for MSP34xx @ 0x80... <6>usbcore: registered new interface driver hiddev

[   47.765342] bt878: AUDIO driver version 0.0.0 loaded

---

### Post by spinlock99 on 2007-11-29
Progress: I have followed the instructions on the MythTV wiki below:

[http://mythtv.org/wiki/index.php/Hauppauge_WinTV-Go](http://mythtv.org/wiki/index.php/Hauppauge_WinTV-Go)

I am currently using option #1 (running the audio out from the TV capture card to the motherboard on the pc).  This led to low volume sound but I did install gnome-alsamixer and I uped some of the levels.  Now, the volume works well and I can watch TV OK.

There is option #3 which is to not use the cable from the capture card to the motherboard but to use the bttv driver for video and snd-bt87x driver for ALSA sound.  I have not had any success with this option.  At the end of the wiki it does say that my card might not have the sound hardware which pretty much leaves me up a creek.  However, when I open gnome-alsamixer it does reccognize a device that looks like my TV capture card.

Should be interesting to get to the bottom of this one.

---

### Post by spinlock99 on 2007-11-30
I was playing around with this last night to try to get the capture card to record sound and I managed to hose my setup.  I can't get sound to bridge from the capture card to the motherboard anymore.  I guess I know what I'm doing this weekend.

---

### Post by spinlock99 on 2007-11-30
OK, I reinstalled because I was getting no where tweeking things more and more.  I still have the patch cable running from the output on the capture card into the mic port on the motherboard.  

I've got sound on but it plays all the time and doesn't sunc with Watch TV on MythTV.  I can't figure out alsamixer so I'm using gnome-alsamixer.  I've got the sound configured so that Master and Mic are unmuted and Mic is set to record.  I've also got Mic Boost (*20dB) enabled (this actually helps a lot). 

Any ideas on how to sound to record and not just be on all the time?

---

### Post by spinlock99 on 2007-12-03
Sound is now working very well.  I still have the patch cable running from the lineout of the capture card (Hauppauge WinTV Go) into the MIC input on the mother board.  In order to get sound to work correctly, I had to:
[LIST]
[*]Unmute PCM
[*]Mute and Record MIC
[/LIST] 
That got sound to sync up with the picture, but the sound was awful (tinny and metalic).  [The manual has a fix for this which is to capture sound at 48000 rather than 36000.]("https://help.ubuntu.com/community/MythTV/Install/Feisty/Troubleshooting#head-573fcd94c0ad9fea7e32ad6e7532e88bdfba11d3")  I followed those instructions and now sound is clear and in sync with the video.

I still haven't figured out how to record sound directly from my Hauppauge WinTV card.  I've been reading on the interweb that sound capture directly from the card will be metalic and not up to par.  I'd like to verify this independantly because it sounds like the same problem I was having with the sampling at 36000 instead of 48000.  We'll see if I have the energy to play with this once I have the IR Blaster working.

Thanks,
Andrew

---

