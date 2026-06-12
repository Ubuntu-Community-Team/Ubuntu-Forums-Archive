---
title: "Solution: WinTV PVR PCI no sound in tvtime"
date: 2006-04-25
forum: Multimedia &amp; Video
---

### Post by _Akira_ on 2006-04-25
Firstly, I'm not a Linux expert, I'm just posting this in the hopes it will help someone else.
Hardware: Regular (original?) Hauppauge WinTV PVR PCI card (not a 150, 250, USB, etc.)
Region: PAL I

Problem: No sound in the program tvtime (and possibly other similar programs). Video working fine.

I checked all volume controls in tvtime, alsa, etc. and cables. All were fine. So I went about checking if it was a software problem. I read up on bttv here [BTTV HowTo]("http://www.tldp.org/HOWTO/BTTV/").

$dmesg | less gave me this:
```
[4294700.365000] bttv0: Bt878 (rev 17) at 0000:00:0d.0, irq: 7, latency: 32, mmio: 0xe2002000
[4294700.365000] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[4294700.365000] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[4294700.365000] bttv0: enabling ETBF (430FX/VP3 compatibilty)
[4294700.365000] bttv0: setting pci timer to 10
[4294700.365000] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[4294700.367000] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[4294700.492000] tveeprom: Hauppauge: model = 45234, rev = D521, serial# = 4235071
[4294700.492000] tveeprom: tuner = Philips FM1216 (idx = 21, type = 5)
[4294700.492000] tveeprom: tuner fmt = PAL(B/G) (eeprom = 0x04, v4l2 = 0x00000007)
[4294700.492000] tveeprom: audio_processor = MSP3415 (type = 6)
[4294700.492000] bttv0: using tuner=5
[4294700.492000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[4294700.495000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4294700.497000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4294700.515000] tvaudio: TV audio decoder + audio/video mux driver
[4294700.515000] tvaudio: known chips: tda9840,tda9873h,tda9874h/a,tda9850,tda9855,tea6300,tea6320,tea6420,tda8425,pic16c54 (PV951),ta8874z
[4294700.564000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[4294700.591000] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[4294700.591000] tuner 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
```

Note the lines:
```
[4294700.365000] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[4294700.365000] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
```
From this, I guessed that it had auto detected my card wrongly. I thought it should mention 'PVR' in the description.

In addition, the lines:
```
[4294700.492000] tveeprom: audio_processor = MSP3415 (type = 6)
[4294700.492000] bttv0: using tuner=5
[4294700.492000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[4294700.495000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4294700.497000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4294700.591000] tuner 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
```
It was saying a lot of 'not found' and also mentioning PAL_BG, with no mention of PAL_I.

Some time has passed since I figured this stuff out, and the writing of this, so I can't remember how, but I came up with two scripts, starttv, and stoptv. 

```
# stoptv - Unload all tv related modules
# sudo  - Execute as super user
# rmmod - Remove a Linux kernel module
# -v    - Verbose output
sudo rmmod -v snd_bt87x
sudo rmmod -v bt878
sudo rmmod -v bttv
sudo rmmod -v tuner
sudo rmmod -v tveeprom
```

```
# starttv - Load all tv modules, with manual specification of card and tuner
# sudo     - Execute as super use
# modprobe - Add a module to Linux kernel
# -v       - Verbose output
sudo modprobe -v bttv card=80 tuner=1
sudo modprobe -v tuner
sudo modprobe -v tveeprom
sudo modprobe -v bt878
sudo modprobe -v snd_bt87x index=1 load_all
```

So basically, I run stoptv, and then starttv. I believe the order is important as regards the unloading and loading of the modules, I think because of some dependencies between them.

Anyway, now at the end of a $dmesg | less, I get:
```
[4302847.875000] bttv0: Bt878 (rev 17) at 0000:00:0d.0, irq: 7, latency: 64, mmio: 0xe2002000
[4302847.875000] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[4302847.875000] bttv0: using: Hauppauge WinTV PVR [card=80,insmod option]
[4302847.875000] bttv0: enabling ETBF (430FX/VP3 compatibilty)
[4302847.875000] bttv0: setting pci timer to 10
[4302847.875000] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[4302848.647000] bttv0: altera firmware upload ok
[4302848.762000] tveeprom: Hauppauge: model = 45234, rev = D521, serial# = 4235071
[4302848.763000] tveeprom: tuner fmt = PAL(B/G) (eeprom = 0x04, v4l2 = 0x00000007)
[4302848.763000] tveeprom: audio_processor = MSP3415 (type = 6)
[4302848.763000] bttv0: using tuner=1
[4302848.763000] bttv0: i2c: checking for MSP34xx @ 0x80... found
[4302848.822000] msp34xx: init: chip=MSP3415D-B3 +nicam +simple mode=simple
[4302848.833000] msp3410: daemon started
[4302848.867000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4302848.869000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4302848.885000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[4302848.914000] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[4302848.914000] tuner 0-0061: type set to 1 (Philips PAL_I (FI1246 and compatibles))
[4302848.947000] bttv0: registered device video0
[4302848.949000] bttv0: registered device vbi0
[4302848.951000] bttv0: registered device radio0
[4302848.963000] bttv0: PLL: 28636363 => 35468950 . ok
[4302849.085000] bt878: AUDIO driver version 0.0.0 loaded
[4302849.087000] bt878: Bt878 AUDIO function found (0).
```

The lines to note here are:
```
[4302847.875000] bttv0: using: Hauppauge WinTV PVR [card=80,insmod option]
...
[4302848.763000] tveeprom: audio_processor = MSP3415 (type = 6)
[4302848.763000] bttv0: using tuner=1
[4302848.763000] bttv0: i2c: checking for MSP34xx @ 0x80... found
...
[4302848.914000] tuner 0-0061: type set to 1 (Philips PAL_I (FI1246 and compatibles))
...
[4302849.085000] bt878: AUDIO driver version 0.0.0 loaded
[4302849.087000] bt878: Bt878 AUDIO function found (0).
```
Here, we can see mention of Hauppauge WinTV PVR as my card, PAL_I as the region (which is correct in my case), and there's 'things' found, and the audio driver loaded which it made no mention of being able to do before. This looked promising, and it was! I now had sound!

Is this stuff useful enough to go into the HowTo section?

---

### Post by TmP on 2006-04-25
I bet you tried this, but I had the same problem.
It turned out I connected the audio cable that should go to the cd, to my tuner. 

I hope it's some help

---

### Post by _Akira_ on 2006-04-26
[QUOTE=TmP]I bet you tried this, but I had the same problem.
It turned out I connected the audio cable that should go to the cd, to my tuner. 

I hope it's some help[/QUOTE]
I apologise if my post was misleading. I was just relaying information on how I solved the problem! Thank you anyway! I've changed to title in an attempt to clarify the situation.

---

