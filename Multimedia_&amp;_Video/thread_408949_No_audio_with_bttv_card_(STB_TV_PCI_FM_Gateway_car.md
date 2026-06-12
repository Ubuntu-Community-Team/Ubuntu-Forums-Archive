---
title: "No audio with bttv card (STB TV PCI FM Gateway card)"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by hellosiva on 2007-04-14
I have a STB TV FM PCI Gateway card. The card has the following chips on it.

BT878 KHF
Philips FM1236 / F
TDA 7432D
TEA 6420
TDA 9850

I tried tvtime & xawtv, I am not getting any audio.  Video works OK.  It looks like the volume is muted in the tuner card itself. 
The card has a audio output jack on it that can be patched to the sound card, I am not getting  audio on this jack. The sound card is working, I tried directly connecting the cd audio patch cable instead of the tv audio and I get the cd audio.  
  
Here the dmesg output. There is an error message about bt878 audio probe failure. 

[   35.922148] bttv: driver version 0.9.16 loaded
[   35.922156] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   35.922238] bttv: Bt8xx card found (0).
[   35.922270] bttv0: Bt878 (rev 2) at 0000:00:0b.0, irq: 10, latency: 32, mmio: 0xef000000
[   35.922284] bttv0: detected: STB TV PCI FM, Gateway P/N 6000704 [card=40], PCI subsystem ID is 10b4:2636
[   35.922290] bttv0: using: STB TV PCI FM, Gateway P/N 6000704 (bt878), 3Dfx VoodooTV 100 [card=40,autodetected]
[   35.922331] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   35.922824] bttv0: using tuner=2
[   35.922831] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   35.923552] bttv0: i2c: checking for TDA7432 @ 0x8a... found
[   35.970442] tda7432 1-0045: chip found @ 0x8a (bt878 #0 [sw])
[   35.985545] tvaudio 1-004c: tea6420 found @ 0x98 (bt878 #0 [sw])
[   35.987966] tvaudio 1-005b: tda9850 found @ 0xb6 (bt878 #0 [sw])
[   35.990969] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   36.011189] tuner 1-0063: chip found @ 0xc6 (bt878 #0 [sw])
[   36.011252] tuner 1-0063: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   36.011258] tuner 1-0063: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   36.020092] bttv0: registered device video0
[   36.020135] bttv0: registered device vbi0
[   36.020179] bttv0: registered device radio0
[   36.021779] bttv0: PLL: 28636363 => 35468950 .. ok
[   36.198621] bt878: AUDIO driver version 0.0.0 loaded
[   36.198686] bt878: Bt878 AUDIO function found (0).
[   36.198707] bt878_probe: card id=[0x263610b4], Unknown card.
[   36.198709] Exiting..
[   36.198719] bt878: probe of 0000:00:0b.1 failed with error -22


Thanks
Siva

---

### Post by billstei on 2007-04-30
One way to get the card unmuted (it has it's own internal mixer which can, and does, get muted) is to use gnomeradio which has a both a mute button, and also a prefs setting to "mute on exit", which you can uncheck.

I can't get xawtv to run at all (X issues), but tvtime works ok.  I am feeding audio with the Audio Out connector on the STB card to a AUX-IN on my sound card.

I am getting really bad distortion on the sound, though, and I think this is either an ALSA problem (my ALSA mixer settings are <90% so that is not the problem), or that the internal mixer of the STB tuner is set too high (assuming it is variable).  Anyone know if it is possible to control the internal mixer of the card?

Bill

---

### Post by orzechowskid on 2007-11-20
was this ever resolved?  I'm running Ubuntu Gutsy with a Gateway/STB tv card (bt878 chipset) and am getting the exact same dmesg output, right down to the unknown card ID and the bt878_probe error code...

thanks in advance for any help!

---

### Post by h2gofast on 2008-03-19
Same card with same issues,  No resolution.

---

### Post by cknight725 on 2008-04-07
Same here -- crap TV card, no sound -- TV and TV recording work great ... :(

---

### Post by tabias on 2008-04-11
I have the same chipset (a hauppauge bt878) and use an external cable to connect the audio to the line-in of the soundcard. 

Ten I installed the chipset with the right card number (but apparantly it was already installed) and then tvtime. This gave me a picture but no audio.

after some fracking around in the audio mixer ( double click on the speaker) I found the following to work:

First go to you bt878 mixer and show all things, then cross on the tuner boost and tv tuner and unmute it. ( this is done in the two tabs). 
THen go to your default mixer and add the capture feedback. unmute this and unmute the line-in and set the analog input to line-in.

After some more random (un)checking/(un)muting the sound apparantly worked and has worked eversince. 

So I advice to do this and to frack around a bit in the mixer :)
system: 
ubuntu gutsy gibbon 7.10
athlon 64-bit 3500+
1gb ddr dual channel
msi k8n sli amd platinum (nforce 4 onboard audio enabled being an audigy ls or sound blaster 24bit)
msi 6600gt

---

### Post by xc3RnbFO8P on 2008-04-11
Here is some useful informations:
[http://gentoo-wiki.com/HARDWARE_saa7134]("http://gentoo-wiki.com/HARDWARE_saa7134")

---

