---
title: "Avermedia a180 issues"
date: 2009-03-05
forum: Mythbuntu
---

### Post by znice on 2009-03-05
Hey all, I am new to this forum.  I am running Mythbuntu 8.10 32 bit on a PC with an AMD 4850e.  I have a pvr-150 and an Avermedia a180 installed.  The pvr-150 worked out of the box (remote and all) but my Avermedia a180 is giving me a bit of trouble.  I followed the directions at [http://www.jnewcastle.com/blog/2006/10/06/install-avermedia-a180-on-ubuntu](http://www.jnewcastle.com/blog/2006/10/06/install-avermedia-a180-on-ubuntu) (these are pretty much the same as the directions on the MythTV wiki).  When I "modprobe saa7134-dvb" from the terminal, I don't get any errors but I also don't get the "/dev/dvb/adapter**" directory structure that it seems I am supposed to (there is no "dvb" subdirectory in my "/dev").  
"dmesg | grep saa" gives me: ```
[   10.176878] saa7130/34: v4l2 driver version 0.2.14 loaded
[   10.177347] saa7134 0000:01:07.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
[   10.177353] saa7130[0]: found at 0000:01:07.0, rev: 1, irq: 18, latency: 64, mmio: 0xdffffc00
[   10.177359] saa7130[0]: subsystem: 1461:1044, board: UNKNOWN/GENERIC [card=0,autodetected]
[   10.177369] saa7130[0]: board init: gpio is 10400
[   10.328016] saa7130[0]: i2c eeprom 00: 61 14 44 10 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   10.328025] saa7130[0]: i2c eeprom 10: 00 ff 86 0f ff 20 00 00 00 00 00 00 00 00 00 00
[   10.328032] saa7130[0]: i2c eeprom 20: 01 40 01 02 02 ff 01 03 06 ff 00 10 00 00 00 00
[   10.328040] saa7130[0]: i2c eeprom 30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   10.328047] saa7130[0]: i2c eeprom 40: ff 64 00 c2 14 16 ff ff 00 00 00 00 00 00 00 00
[   10.328054] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328061] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328068] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328076] saa7130[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328083] saa7130[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328090] saa7130[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328098] saa7130[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328105] saa7130[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328112] saa7130[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328120] saa7130[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328127] saa7130[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328530] saa7130[0]: registered device video1 [v4l2]
[   10.328791] saa7130[0]: registered device vbi1
[   10.339556] saa7134 ALSA driver for DMA sound loaded
[   10.339583] saa7130[0]/alsa: saa7130[0] at 0xdffffc00 irq 18 registered as card -2

```

"lspci | grep saa" shows me
```
saa7134_dvb            27532  0 
saa7134_alsa           20000  0 
saa7134               147796  2 saa7134_dvb,saa7134_alsa
ir_common              48900  3 cx88xx,bttv,saa7134
videobuf_dma_sg        20612  6 cx8800,cx88xx,bttv,saa7134_dvb,saa7134_alsa,saa7134
videobuf_dvb           12932  1 saa7134_dvb
videobuf_core          26628  6 cx8800,cx88xx,bttv,saa7134,videobuf_dma_sg,videobuf_dvb
dvb_core               86272  2 saa7134_dvb,videobuf_dvb
snd_pcm                83204  3 saa7134_alsa,snd_hda_intel,snd_pcm_oss
videodev               41344  6 cx8800,cx88xx,bttv,saa7134,tuner,ivtv
compat_ioctl32          9344  4 cx8800,bttv,saa7134,ivtv
v4l2_common            19840  8 cx8800,bttv,saa7134,wm8775,cx25840,tuner,ivtv,cx2341x
tveeprom               20228  4 cx88xx,bttv,saa7134,ivtv
i2c_core               31892  14 cx88xx,bttv,lirc_i2c,nvidia,saa7134_dvb,saa7134,tuner_simple,wm8775,cx25840,tuner,ivtv,i2c_algo_bit,v4l2_common,tveeprom
snd                    63268  12 saa7134_alsa,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

```

I have made sure to blacklist saa7134, so I am not sure why it looks like this module is being loaded at boot.  I've really looked everywhere (checked out Cresho's tutorial) and none of the things I have found have worked.
cheers
-Nick Z

---

### Post by newlinux on 2009-03-06
A couple of things,

1. In following those instructions, did you download the modules from the latest kernel, or did you use the kernel those instructions refer to? Probably best to get the firmware from the latest kernel.

2. Did you buy this Avermedia A180 recently? I've seen that they've changed the chip on some of them - they can be made to work, but they take more effort.

what does:

```

lspci -nn 

```
return

You should see something similar to:

```

01:0a.0 Multimedia controller [0480]: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)

```
in the output

---

### Post by klc5555 on 2009-03-06
There are two things with the A180. The first thing (which appears to be your problem) is that it uses a flavor of the Philipps "stupid tuner" that doesn't identify itself properly to modprobe. Unless you tell modprobe what flavor of saa7134 you need, usually the module will load, but the card will be useless. If this is a real honest-to-goodness AverMedia A180, then your card=75 and your tuner=68

You can test this: after "sudo rmmod saa7134-dvb" and "sudo rmmod saa7134" (it has to be done in this order) do a "sudo modprobe saa7134-dvb card=75 tuner=68 "  Mythbackend should now detect the card as a dvb card (Air2PC or some such nonsense); the card should scan (because of card=75); it should get locks (because of tuner=68). But it may or may not find tables.  

If it doesn't find tables, it indicates the firmware file is absent or not loading properly. "dmesg | grep nxt" should tell you what's up with the firmware file. If it's absent, install it as described in the tutorial you mentioned. Or here:

[http://www.mythtv.org/wiki/AVerTV_HD_A180](http://www.mythtv.org/wiki/AVerTV_HD_A180)

If the firmware is present, but refuses to load and times out, this is supposed to be caused by I2c support in your particular kernel being compiled into the kernel --the nxt2004 firmware can only handle it when I2c support is done as a module. (Took me a month to find the answer to that particular one...)

When your card works, you will need to put the options saa7134-dvb card=75 tuner=68 into your options file under /etc/modprobe.d   

But once the card is working properly, it's a great card! Just a bit of a head-scratcher.

Good luck!

---

### Post by newlinux on 2009-03-06
I just looked at your dmesg output, and from that I'm betting your lspci -nn output will be:

01:0a.0 Multimedia controller [0480]: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder [COLOR="Red"][1131:7130][/COLOR] (rev d1)

Which means you have the 7130 chip (this is the cut down version of the card with no analog A/V inputs). The older ones have 7133 chip.

[http://www.avsforum.com/avs-vb/showthread.php?p=15481514#post15481514](http://www.avsforum.com/avs-vb/showthread.php?p=15481514#post15481514)

Read the rest of this thread, and it will give you info on how to set this particular one up. I recommend you read from this post till the card is working so you know what you need to do.

Or you can return it and try and get the other version which will work without these edits.

---

### Post by newlinux on 2009-03-06
> **klc5555 said:**
> There are two things with the A180. The first thing (which appears to be your problem) is that it uses a flavor of the Philipps "stupid tuner" that doesn't identify itself properly to modprobe. Unless you tell modprobe what flavor of saa7134 you need, usually the module will load, but the card will be useless. If this is a real honest-to-goodness AverMedia A180, then your card=75 and your tuner=68

You can test this: after "sudo rmmod saa7134-dvb" and "sudo rmmod saa7134" (it has to be done in this order) do a "sudo modprobe saa7134-dvb card=75 tuner=68 "  Mythbackend should now detect the card as a dvb card (Air2PC or some such nonsense); the card should scan (because of card=75); it should get locks (because of tuner=68). But it may or may not find tables.  

If it doesn't find tables, it indicates the firmware file is absent or not loading properly. "dmesg | grep nxt" should tell you what's up with the firmware file. If it's absent, install it as described in the tutorial you mentioned. Or here:

[http://www.mythtv.org/wiki/AVerTV_HD_A180](http://www.mythtv.org/wiki/AVerTV_HD_A180)

If the firmware is present, but refuses to load and times out, this is supposed to be caused by I2c support in your particular kernel being compiled into the kernel --the nxt2004 firmware can only handle it when I2c support is done as a module. (Took me a month to find the answer to that particular one...)

When your card works, you will need to put the options saa7134-dvb card=75 tuner=68 into your options file under /etc/modprobe.d   

But once the card is working properly, it's a great card! Just a bit of a head-scratcher.

Good luck!

If  this card is using a different chip (7130 instead of 7133) you will definitely want to remove or comment out "saa7134-dvb card=75 tuner=68" from your /etc/modprobe.d options and let the card be autodetected before proceeding with patching the driver to make this card work. In later versions of the saa7134-dvb driver, even if it is the old 7133 chip autodetection should work - you shouldn't need module options (I haven't needed them with mine for a while).

---

### Post by klc5555 on 2009-03-06
> **newlinux said:**
> I just looked at your dmesg output, and from that I'm betting your lspci -nn output will be:

01:0a.0 Multimedia controller [0480]: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder [COLOR="Red"][1131:7130][/COLOR] (rev d1)

Which means you have the 7130 chip (this is the cut down version of the card with no analog A/V inputs). The older ones have 7133 chip.

[http://www.avsforum.com/avs-vb/showthread.php?p=15481514#post15481514](http://www.avsforum.com/avs-vb/showthread.php?p=15481514#post15481514)

Read the rest of this thread, and it will give you info on how to set this particular one up. I recommend you read from this post till the card is working so you know what you need to do.

Or you can return it and try and get the other version which will work without these edits.

Mine's a new-style 7130 card without analog. modprobe autodetection wouldn't work on a 2.6.27.7 kernel; i2c scan option wouldn't work either; I had to specify the card/tuner at modprobe. But the parameters listed in connection with the saa7134 driver on the Gentoo wiki are still correct: card=75 tuner=68 work.

Cheers!

---

### Post by newlinux on 2009-03-06
> **klc5555 said:**
> Mine's a new-style 7130 card without analog. modprobe autodetection wouldn't work on a 2.6.27.7 kernel; i2c scan option wouldn't work either; I had to specify the card/tuner at modprobe. But the parameters listed in connection with the saa7134 driver on the Gentoo wiki are still correct: card=75 tuner=68 work.

Cheers!

Ahhh! Maybe they've incorporated some of the driver changes already into that kernel, making only module options necessary (in addition to the firmware of course)... Didn't used to work for the 7130 (as detailed in the above thread). My only point is if you go with the method in the above thread, don't use any module options... This is according to one of the maintainers of the driver.

Hopefully your options will work... much easier!

---

### Post by klc5555 on 2009-03-06
> **newlinux said:**
> Ahhh! Maybe they've incorporated some of the driver changes already into that kernel, making only module options necessary (in addition to the firmware of course)... Didn't used to work for the 7130 (as detailed in the above thread). My only point is if you go with the method in the above thread, don't use any module options... This is according to one of the maintainers of the driver.

Hopefully your options will work... much easier!

I just now read that thread you cited. Gack! Thank goodness I didn't run across the discussion when I first bought my card --I'd probably have just given up straightaway and sent the thing back! The I2c bus module thing was annoying enough. No wonder Newegg was selling the card at the time for about $40! 

All the best! :D

---

### Post by znice on 2009-03-06
Thanks all.  newlinux is correct, the card is of the variety without analog.  I bought it for about 50 bucks on newegg.  I'm starting to think that I will soon sell it for the same (or nearly) on ebay and get a better supported card.  I checked out the avs forum discussion: pretty discouraging stuff but I'll give it all one last go when I have some free time this evening.
As predicted, lspci -nn gives me:
```
01:07.0 Multimedia controller [0480]: Philips Semiconductors SAA7130 Video Broadcast Decoder [1131:7130] (rev 01)

```

---

### Post by newlinux on 2009-03-06
> **znice said:**
> Thanks all.  newlinux is correct, the card is of the variety without analog.  I bought it for about 50 bucks on newegg.  I'm starting to think that I will soon sell it for the same (or nearly) on ebay and get a better supported card.  I checked out the avs forum discussion: pretty discouraging stuff but I'll give it all one last go when I have some free time this evening.
As predicted, lspci -nn gives me:
```
01:07.0 Multimedia controller [0480]: Philips Semiconductors SAA7130 Video Broadcast Decoder [1131:7130] (rev 01)

```

which kernel are your running (uname -r)? Give klc5555's method a shot. He has the same card. Make sure you've copied over the firmware.

---

### Post by znice on 2009-03-07
I tried KLC5555's method and got the following:
```
nick@nick-desktop:~$ sudo rmmod saa7134-dvb
[sudo] password for nick: 
nick@nick-desktop:~$ sudo rmmod saa7134
ERROR: Module saa7134 is in use by saa7134_alsa
nick@nick-desktop:~$ sudo rmmod saa7134_alsa
nick@nick-desktop:~$ sudo rmmod saa7134
nick@nick-desktop:~$ sudo modprobe saa7134-dvb card=75 tuner=68
FATAL: Error inserting saa7134_dvb (/lib/modules/2.6.27-11-generic/kernel/drivers/media/video/saa7134/saa7134-dvb.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
the relevant dmesg output:
```
[  316.396299] saa7134_dvb: Unknown parameter `card'

```

Now, when I run "dmesg | grep nxt", I get nothing, so I guess that means the firmware never loaded, but I judge that is simply because saa7134-dvb couldn't load.  I am running Kernel 2.6.27-11.  I have dropped the nxt2004 firmware file in both my "/lib/firmware" and my "/lib/firmware/2.6.27-11-generic" directories (Cresho's tutorial said to have the file in /lib/firmware/[kernel] whereas every other just says to drop it in /lib/firmware).  Any thoughts?

---

### Post by klc5555 on 2009-03-07
> **znice said:**
> I tried KLC5555's method and got the following:
```
nick@nick-desktop:~$ sudo rmmod saa7134-dvb
[sudo] password for nick: 
nick@nick-desktop:~$ sudo rmmod saa7134
ERROR: Module saa7134 is in use by saa7134_alsa
nick@nick-desktop:~$ sudo rmmod saa7134_alsa
nick@nick-desktop:~$ sudo rmmod saa7134
nick@nick-desktop:~$ sudo modprobe saa7134-dvb card=75 tuner=68
FATAL: Error inserting saa7134_dvb (/lib/modules/2.6.27-11-generic/kernel/drivers/media/video/saa7134/saa7134-dvb.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
the relevant dmesg output:
```
[  316.396299] saa7134_dvb: Unknown parameter `card'

```

Now, when I run "dmesg | grep nxt", I get nothing, so I guess that means the firmware never loaded, but I judge that is simply because saa7134-dvb couldn't load.  I am running Kernel 2.6.27-11.  I have dropped the nxt2004 firmware file in both my "/lib/firmware" and my "/lib/firmware/2.6.27-11-generic" directories (Cresho's tutorial said to have the file in /lib/firmware/[kernel] whereas every other just says to drop it in /lib/firmware).  Any thoughts?

I'm at home today, typing from the same machine that I use the 7130 chip new-style AverMedia A180 in. Its lspci -nn output:

05:03.0 Multimedia controller [0480]: Philips Semiconductors SAA7130 Video Broadcast Decoder [1131:7130] (rev 01)


But checking the modprobe command that I have loading the driver for it at bootup, I find that I mis-quoted it from memory yesterday. It's actually:

modprobe saa7134 card=75 tuner=68 disable_ir=1

Rather than invoking saa7134_dvb directly, I modprobed saa7134 with the parameters, and it invokes saa7134_dvb on its own. Give this variation of the command a try. 

Apologies for my faulty memory yesterday from at work.

---

### Post by CharlieHorse1967 on 2009-04-19
I'm having a similar problem to znice.  I try klc's suggestion of:
> modprobe saa7134 card=75 tuner=68 disable_ir=1 
No joy! :(
I went to [http://www.mythtv.org/wiki/AVerTV_HD_A180](http://www.mythtv.org/wiki/AVerTV_HD_A180) and tried their suggestions and when I get to 
> modprobe saa7134-dvb

which will create /dev/dvb/adapter#/ and its associated files. 
there is not /dvb directory in my /dev directory.  What do I need to do to get this card working?

My lspci -nn results are:
> 00:00.0 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0754] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge [10de:075c] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP78S [GeForce 8200] SMBus [10de:0752] (rev a1)
00:01.2 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0751] (rev a1)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP78S [GeForce 8200] Co-Processor [10de:0753] (rev a2)
00:01.4 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0568] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077b] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077c] (rev a1)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077d] (rev a1)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077e] (rev a1)
00:06.0 IDE interface [0101]: nVidia Corporation MCP78S [GeForce 8200] IDE [10de:0759] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec [10de:0774] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:075a] (rev a1)
00:09.0 SATA controller [0106]: nVidia Corporation Device [10de:0584] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:0569] (rev a1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:0778] (rev a1)
00:12.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:075b] (rev a1)
00:13.0 PCI bridge [0604]: nVidia Corporation Device [10de:077a] (rev a1)
00:14.0 PCI bridge [0604]: nVidia Corporation Device [10de:077a] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control [1022:1204]
01:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
02:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8200 [10de:0849] (rev a2)
05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 14)


---

### Post by klc5555 on 2009-04-20
I'm a bit reluctant to comment further on this card here, since the particular backend I run it on is not one of my Ubuntu machines, but is rather a Slackware backend.

But looking at your lspci -nn output, unless I'm missing something, it appears that your initial problem is hardware. Your system seems to be unaware of any multimedia controller (whether "Unknown" or correctly identified as the "Philips Semiconductors SAA7130 Video Broadcast Decoder") having been plugged into a PCI slot and given an IRQ assignment. 

You may wish to check whether the card is seated properly in its slot, and whether your bios is setup properly to automatically handle IRQs and PCI assignments. Also, not all PCI slots are equal, and some cards on some motherboards boards will not function unless they occupy the highest-priority slot, i.e. the one closest to the slot where a video card would go.

---

### Post by CharlieHorse1967 on 2009-04-30
Thank you very much kcl.  Stupid me spent a couple of weeks and I didn't have the darned card inserted.:oops:
Now everything works like I expect!

---

### Post by klc5555 on 2009-05-01
> **CharlieHorse1967 said:**
> Thank you very much kcl.  Stupid me spent a couple of weeks and I didn't have the darned card inserted.:oops:
Now everything works like I expect!

Glad it works! :D 

Especially because I really like these inexpensive AverMedia cards, even though they're a bit tricky to get going the first time.

Cheers!

---

