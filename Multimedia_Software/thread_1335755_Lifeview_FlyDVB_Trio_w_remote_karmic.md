---
title: "Lifeview FlyDVB Trio \w remote karmic"
date: 2009-11-23
forum: Multimedia Software
---

### Post by nuclear216 on 2009-11-23
Hello!

I have a [Flydvb Trio]("http://www.lifeview.com.tw/html/products/internal_tv/flydvb_trio.htm"), a tv card with DVB-T, DVB-S, Radio FM, S-Video, Composite and a remote control.
It's an old card with still great functions and fully supported under linux, except for some "glitches" that requires tweaking the system.

The purpose of this thread is to collect available information on this card from other users too so to write an extensive tutorial, I have collected a lot of information about it and done tweaking but It still don't work as I want to. 
From what I see by searching the internet for this card it seems a lot of people own it and a lot of discussion has gone around, spread over the years across mailing list and forums.

All the pieces are there so with some a little effort it can all be patched together.

**_The glitches: _**
1) the remote doesn't work out of the box, it needs a kernel patch
2) DVB-T and DVB-S can't be used at the same time, they have to be selected manually with modprobe, need a bash script mapped to the remote. 
3) It seems DVB-S need to be tweaked to work, as I have no satellite dish (yet) this is low priority for me but I'll have to look into that.

**_What works:_**
with a modern kernel the card is autodetected out of the box, sound works (need cable connection to the sound card), devices are created, DVB-T works, radio FM works.

```

uname -r
2.6.31-14-generic

``````

lspci | grep Decoder
0a:09.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

``````
dmesg (before remote kernel patch)

[   10.908629] saa7130/34: v4l2 driver version 0.2.15 loaded
[   10.908868]   alloc irq_desc for 29 on node 0
[   10.908872]   alloc kstat_irqs on node 0
[   10.908881] saa7134 0000:0a:09.0: PCI INT A -> GSI 29 (level, low) -> IRQ 29
[   10.908887] saa7133[0]: found at 0000:0a:09.0, rev: 209, irq: 29, latency: 181, mmio: 0xc0100000
[   10.908893] saa7133[0]: subsystem: 5168:0319, board: LifeView FlyDVB Trio [card=84,autodetected]
[   10.908952] saa7133[0]: board init: gpio is 211400
[   10.908964] IRQ 29/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   11.100016] saa7133[0]: i2c eeprom 00: 68 51 19 03 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   11.100023] saa7133[0]: i2c eeprom 10: 00 00 60 0a ff 20 ff ff ff ff ff ff ff ff ff ff
[   11.100030] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 01 01 03 08 ff 01 f9 ff ff ff ff
[   11.100036] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.100042] saa7133[0]: i2c eeprom 40: ff 00 10 c0 96 12 08 00 c2 96 c6 1c 16 3a 15 ff
[   11.100048] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.100054] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.100060] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.100066] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.100072] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.100078] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.100084] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.100090] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.100096] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.100102] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.100108] saa7133[0]: i2c eeprom f0: 00 0c 45 00 cf a0 ff ff ff ff ff ff ff ff ff ff
[   11.120013] saa7133[0]: i2c scan: found device @ 0x10  [???]
[   11.140015] saa7133[0]: i2c scan: found device @ 0x12  [???]
[   11.160018] saa7133[0]: i2c scan: found device @ 0x1c  [???]
[   11.190019] saa7133[0]: i2c scan: found device @ 0x96  [???]
[   11.210015] saa7133[0]: i2c scan: found device @ 0xa0  [eeprom]
[   11.216532] i2c-adapter i2c-2: Invalid 7-bit address 0x7a
[   11.520148] tuner 2-004b: chip found @ 0x96 (saa7133[0])
[   11.680021] tda829x 2-004b: setting tuner address to 61
[   11.830021] tda829x 2-004b: type set to tda8290+75a
[   16.830350] saa7133[0]: dsp access error
[   16.830359] saa7133[0]: dsp access error
[   16.960095] saa7133[0]: registered device video1 [v4l2]
[   16.960117] saa7133[0]: registered device vbi0
[   16.960139] saa7133[0]: registered device radio0
[   17.178991] saa7134 ALSA driver for DMA sound loaded
[   17.179009] IRQ 29/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   17.179034] saa7133[0]/alsa: saa7133[0] at 0xc0100000 irq 29 registered as card -2
[   17.262754] dvb_init() allocating 1 frontend
[   17.383885] DVB: registering new adapter (saa7133[0])
[   17.383894] DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)...

```[B][U]The remote:
[/U][/B]
The remote does not work out of the box with any kernel.
There exist two patches (both attached here): the first for old kernel made by a guy [back in 2006]("http://threebit.net/mail-archive/video4linux/msg06239.html") which doesn't apply anymore to jaunty nor karmic kernel source.
Another guy upgraded it for 2.6.28 kernels [not so long ago]("http://www.linuxtv.org/pipermail/linux-dvb/2009-April/032055.html"), this version applies succesfully to jaunty latest source 2.6.28-16.57, but not to karmic.
[U]
[SIZE=3]So I am gonna make it crystal clear here:
If any good soul out there upgrade the patch to karmic 2.6.31 me LOOOT of kudos to you \\:D/[/SIZE][/U] 

even better would be, but I think this is hard, to make it work with any future version of the kernel; btw is this even possible?

after applying the second patch, compiling and installing the kernel dmesg will show the lifeview remote 

```

dmesg (after kernel remote patch)
[   13.560860] saa7130/34: v4l2 driver version 0.2.14 loaded
[   13.560929] saa7134 0000:0a:09.0: PCI INT A -> GSI 29 (level, low) -> IRQ 29
[   13.560935] saa7133[0]: found at 0000:0a:09.0, rev: 209, irq: 29, latency: 181, mmio: 0xc0100000
[   13.560941] saa7133[0]: subsystem: 5168:0319, board: LifeView FlyDVB Trio [card=84,autodetected]
[   13.561007] saa7133[0]: board init: gpio is 211400
[   13.714185] saa7133[0]: i2c eeprom 00: 68 51 19 03 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   13.714193] saa7133[0]: i2c eeprom 10: 00 00 60 0a ff 20 ff ff ff ff ff ff ff ff ff ff
[   13.714198] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 01 01 03 08 ff 01 f9 ff ff ff ff
[   13.714204] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.714209] saa7133[0]: i2c eeprom 40: ff 00 10 c0 96 12 08 00 c2 96 c6 1c 16 3a 15 ff
[   13.714215] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.714220] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.714225] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.714231] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.714236] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.714241] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.714247] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.714252] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.714257] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.714263] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.714268] saa7133[0]: i2c eeprom f0: 00 0c 45 00 cf a0 ff ff ff ff ff ff ff ff ff ff
[   13.724196] saa7133[0]: i2c scan: found device @ 0x10  [???]
[   13.730849] saa7133[0]: i2c scan: found device @ 0x12  [???]
[   13.740849] saa7133[0]: i2c scan: found device @ 0x1c  [???]
[   13.753365] saa7133[0]: i2c scan: found device @ 0x96  [???]
[   13.760031] saa7133[0]: i2c scan: found device @ 0xa0  [eeprom]
[   13.908042] tuner' 2-004b: chip found @ 0x96 (saa7133[0])
[   13.994208] tda829x 2-004b: setting tuner address to 61
[   14.080853] tda829x 2-004b: type set to tda8290+75a
[   17.988143] input: Lifeview as /devices/virtual/input/input5
[   18.041368] ir-kbd-i2c: Lifeview detected at i2c-2/2-000b/ir0 [saa7133[0]]
[   18.041641] saa7133[0]: registered device video1 [v4l2]
[   18.041664] saa7133[0]: registered device vbi0
[   18.041688] saa7133[0]: registered device radio0
[   18.189562] saa7134 ALSA driver for DMA sound loaded
[   18.189604] saa7133[0]/alsa: saa7133[0] at 0xc0100000 irq 29 registered as card -2
[   18.366403] dvb_init() allocating 1 frontend
[   19.060027] DVB: registering new adapter (saa7133[0])
[   19.060034] DVB: registering adapter 0 frontend 0 (Philips TDA10086 DVB-S)...

``````

lsmod | grep saa
saa7134_dvb            24332  0 
videobuf_dvb            8516  1 saa7134_dvb
saa7134_alsa           14048  0 
dvb_core               97260  2 saa7134_dvb,videobuf_dvb
saa7134               168732  2 saa7134_dvb,saa7134_alsa
ir_common              48004  2 ir_kbd_i2c,saa7134
v4l2_common            15104  2 tuner,saa7134
videobuf_dma_sg        14532  3 saa7134_dvb,saa7134_alsa,saa7134
videobuf_core          21380  3 videobuf_dvb,saa7134,videobuf_dma_sg
snd_pcm                88840  5 saa7134_alsa,snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
tveeprom               14852  1 saa7134
snd                    69256  13 saa7134_alsa,snd_usb_audio,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
compat_ioctl32         10240  2 saa7134,gspca_main
videodev               37568  4 tuner,saa7134,gspca_main,compat_ioctl32

```ir_common takes care of gnome volume so volume+/-/mute and input works

I haven't got so far to configure lirc to map the remote to software but I plan to do that.
I'll let you know the outcome.
[U][B]
The Multiple front-end[/B][/U]

This card has two front-end: DVB-T and DVB-S (which can't be used at the same time), since [2.6.20]("http://kernel.org/pub/linux/kernel/v2.6/testing/v2.6.20/ChangeLog-2.6.20-rc1") there is a modprobe options to do that.
You may have noticed that in the two dmesg I posted above the registered frontend shifts from DVB-T to DVB-S
those are dmesg from two different kernel, when I rebooted I switched use_frontend=0 to use_frontend=1. I can't go further thatn that as I have no dish so I don't know if DVB-S is really working.

this is my /etc/modprobe.d/options

```

options saa7134 i2c_scan=1 alsa=1 ir_debug=1
options saa7134_dvb use_frontend=1

```Thanks to:

[I]Author: Nico Sabbi <nsabbi@XXXXXXX>
Date:   Wed Nov 15 22:06:56 2006 -0300

    V4L/DVB (4836): Added support for both DVB frontends of the Lifeview Trio

    This card (like some others) supports both, DVB-T and a DVB-S.
    The patch adds an insmod option to select the frontend:
    use_frontend=0 -> DVB-T
    use_frontend=1 -> DVB-S

[/I]       As the remote bundled with the card has a button labelled "source" i think it would be convenient to map it to a scripts that checks whatever the state of the modules is and rmmod/modprobe use_frontend appropriately.
How do I do that?

I thought I can make a scripts that checks what it did last time but this isn't clever, I am not a bash guru (i don't know any programming/scripting at all) but I figure there may be a program that checks the state of the loaded modules, right?
maybe in /proc? 
I don't know where to look for that, please help me as I am stuck here.

_Moreover on this topic:_
If I'd like to schedule a recording from satellite and/or DVB-T I am gonna have a hard time configuring the front-end.
The easier way to take care of that is to make the recording software switch to the needed front-end so I am not covering this here. 

As I don't have the necessary skills to upgrade a patch against a new kernel version and I need help to create a bash script I can only do the work of a self trained monkey and patch together info from other sources.
If someone who can actually do what is needed here would help me I'll write an extensive tutorial.

Anyway, finally:
[U][B]
How to get the remote working under karmic[/B][/U]:

I am not confident on telling anyone how to compile their kernel so take the following instructions with no guarantee.

1) Download and extract somewhere the patch [dvbtrioremote_jaunty.diff.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=137368&stc=1&d=1259023094")
[I]
2) [/I]checkout "A virtual home" [kernel compile instructions for jaunty]("http://blog.avirtualhome.com/2009/09/08/how-to-compile-a-kernel-for-ubuntu-jaunty-revised/") on how to download, compile and install ubuntu kernel source, *Please note that I am linking the instructions on how to compile a kernel for jaunty even if you are supposed to do this under karmic, this is intended as you are compiling the jaunty kernel version.*
Right after having committed the changes with this command

```

git add .
git commit [COLOR=#660033]-a[/COLOR] [COLOR=#660033]-m[/COLOR] [COLOR=#ff0000]"yourflavourname modifications"[/COLOR]

```

you should do the following and apply the patch you downloaded before 

```
patch -p1 < /path/to/downloaded/diff
```

3) carry on with the actual compilation following the tutorial where you left and enjoy your remote.

---

### Post by nuclear216 on 2009-11-25
Bump

---

### Post by segalion on 2010-02-22
Hello.
I have a Lifeview Trio Carbus (similar or same as pci version), and recently I upgrade to Karmic.
(See my veryoldpost
[http://ubuntuforums.org/showthread.php?t=458963](http://ubuntuforums.org/showthread.php?t=458963) )

I have seen that dvb tuner suport are broken from kernel 2.6.26 to 2.6.32 (b.i.)

I have tried kernel 2.6.33(rc6) over karmic and works fine!!! (another problem for me is tvout ati radeon support).

Until this kernel (and from hardy 2.24.x), I get very bad signal in dvb-t dvb-sat and analog tv.

Seems that it is supposed to have remote control support (Iam not using it)

Another good help can be modprobe saa7134 options  (see 'modinfo saa7134').

---

