---
title: "Struggle with WinTV-GO Plus Card"
date: 2007-05-19
forum: Multimedia &amp; Video
---

### Post by Princey on 2007-05-19
One of the things I try to avoid is buying hardware that doesn't have out of the box support under Linux. After doing some research, I found out that the Hauppauge WinTV-Go Plus had out of the box support under Linux and was recommended by some as the way to go. Originally, I wanted the renowned PV-300 that I'm told has excellent support but couldn't find one in my area to buy.

Anyhow, cutting to the chase, since I purchased it over 2 months ago, I've had nothing but trouble trying to get it to work. I've searched Google, the forums here and elsewhere, tried everything short of compiling my own kernel (I know that's it not necessary) to get this working. My aim is to get MythTV set up and running but if I can't get it to supply any form of video in neither VLC, XawTV,KDETV among others, I doubt my luck will extent to MythTV. Tried it as a last resort but nothing. Here's what I keep getting:
> QCM USB Camera: Invalid Arguement
Cannot open capture device /dev/Video0

First, I thought it was a matter of permissions, so I added myself to the group that could use it. Nothing. Here's my system specs first of all:

ACER ASPIRE
AMD 64 X2 3800+
2 GB DDR 400 PC3200 RAM
2 x 250GB SATA Drives (runs Kubuntu Fiesty Fawn [7.04])
80 GB SATA (Runs Windows so I can still record while I sort this out)
X600 PCIE ATI Express 256MB 
Hauppauge WinTV-Go Plus Capture Card (NTSC 44981 LF REV E1B2)

I've read that the WinTV uses the bttv 878 chipset however, some readings do suggest a Conexant chipset. So, I pried open the computer and found the following chipset: > Conexant
FUSION 878 A
25878-13Z
0650Y1YC
0649 Taiwan

```
dmesg
``` yields (edited just to reveal the salient parts) : > [   64.881372] bttv0: Bt878 (rev 17) at 0000:03:08.0, irq: 17, latency: 32, mmio: 0xfdcff000
[   64.881383] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   64.881386] bttv0: using: Hauppauge (bt878 ) [card=10,insmod option]
[   64.881411] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[   64.883915] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   64.915627] tveeprom 2-0050: Encountered bad packet header [ff]. Corrupt or not a Hauppauge eeprom.
[   64.915630] bttv0: Hauppauge eeprom indicates model#44981
[   64.915633] bttv0: using tuner=0
[   64.915672] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   64.916360] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   64.917045] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   64.937022] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   64.943260] videodev: "QCM USB Camera" has no release callback. Please fix your driver for proper sysfs support, see [http://lwn.net/Articles/36850/](http://lwn.net/Articles/36850/)
[   64.943266] drivers/media/video/usbvideo/usbvideo.c: QCM on /dev/video0: canvas=320x240 videosize=320x240
[   64.943333] input: QCM button as /class/input/input6
[   64.943388] usbcore: registered new interface driver QCM
[   64.943399] usbcore: registered new interface driver usblp
[   64.943402] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   64.958931] tuner 2-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   64.958965] tuner 2-0061: type set to 0 (Temic PAL (4002 FH5))
[   64.958969] tuner 2-0061: type set to 0 (Temic PAL (4002 FH5))
[   65.032376] bttv0: registered device video1
[   65.032407] bttv0: registered device vbi0
[   65.032431] bttv0: PLL: 28636363 => 35468950 .. ok


```
lspci -v
``` gives > 03:08.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
        Subsystem: Hauppauge computer works Inc. WinTV Series
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at fdcff000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>

03:08.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
        Subsystem: Hauppauge computer works Inc. WinTV Series
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at fdcfe000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>
 (yeah, I know to get the access denied I need to add 'sudo' in front. If you need that info, let me know)


Any advise as to what to do, if any, will be greatly appreciated. I need to boot less into Windows :(

Thanks in advance.

---

### Post by Princey on 2007-05-20
**_UPDATE_** 

After much digging around and searching, I saw references for ivtv so I installed that. Not sure if you'd call that progress but I can now get radio stations when I search for tv channels. Note, under Windows, although I live outside of the US, we use the NTSC settings with US Cable as we have cable tv down here. What I want is at least to get something more than just radio stations via my tv tuner card.

---

### Post by lupin492 on 2007-05-28
Go through these two links, one of them will give you an idea of how to set a couple of parameters linux needs you to tell it, and the other will tell you wich values these parameters have depending on your chipset and tuner.
Hope it will help you!  
Regards!

[http://www.mythtv.org/wiki/index.php/Bttv]("http://www.mythtv.org/wiki/index.php/Bttv")

[http://www.linuxtv.org/v4lwiki/index.php/Cardlist.BTTV]("http://www.linuxtv.org/v4lwiki/index.php/Cardlist.BTTV")

---

### Post by Princey on 2007-05-29
> **lupin492 said:**
> Go through these two links, one of them will give you an idea of how to set a couple of parameters linux needs you to tell it, and the other will tell you wich values these parameters have depending on your chipset and tuner.
Hope it will help you!  
Regards!

[http://www.mythtv.org/wiki/index.php/Bttv]("http://www.mythtv.org/wiki/index.php/Bttv")

[http://www.linuxtv.org/v4lwiki/index.php/Cardlist.BTTV]("http://www.linuxtv.org/v4lwiki/index.php/Cardlist.BTTV")

Hey, thanks for answering but I've gone through that tutorial. Thing is dmesg doesn't list the tuner type save for "0" and there's something in the dmesg that suggests that when the driver probes for the tuner information, it fails to get that info. > [ 64.881383] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[ 64.881386] bttv0: using: Hauppauge (bt878 ) [card=10,insmod option]
[ 64.881411] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[ 64.883915] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[ 64.915627] tveeprom 2-0050: Encountered bad packet header [ff]. Corrupt or not a Hauppauge eeprom.
[ 64.915630] bttv0: Hauppauge eeprom indicates model#44981
[ 64.915633] bttv0: using tuner=0

---

