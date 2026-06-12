---
title: "Help Getting TV Card to Work"
date: 2008-06-06
forum: Multimedia Software
---

### Post by Rofl77 on 2008-06-06
Hi,

I've been working on this for about 4 hours and I need some help.  I'm trying to get my TV card to work in Ubuntu 8.  Here's what lspci -vvv  has on this device:
...
00:0b.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (63750ns min, 63750ns max)
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at f7e00000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
...

I've tried many different ways to get this device to work without success:  installed v4l, setup /dev/dvb/, dvb-apps, dvb-utils, tried new firmware, tried scan, read A LOT of tutorials and forum posts, but nothing seems to work.  

The maker (*maybe*) is AITech model WaveWatcher TV-PCI TV Tuner and Video Capture Card.  At least that's what's listed in the software that came with it, but it doesn't look like the WaveWatcher card from AITech.  It comes with Terminator software for Windows: Quick TV and TV7131 Utilities.  It works fine on my Win XP install.  I'm trying to move away from Windows, but I want all my devices to come with me.  Any help getting my TV card working would be most appreciated.

From the physical TV card itself here's some more info.  It has 4 physical ports:  FM Tuner (stereo jack?), TV (coax in), A/V (like s-video with extra pins), Remote (RF).  I just need the coax in and the sound out from the AV port to the line-in on my sound card.  Also, on the card there is a sticky label that reads:
VS-L TV7131RF
Made in Taiwan
05040412466

On the largest chip on the board it reads:
(Philips Logo)  
SAA7131E
CD 9672
TtN05021



Thanks in advance for your help.

---

### Post by fenian on 2008-06-06
Try this first make a modprobe.conf file...

> sudo gedit /etc/modprobe.conf

will open a blank text file add thesse lines...

> 
alias char-major-81 videodev
alias char-major-81-0 saa7134


load the modules with this command...

> sudo modprobe saa7134 i2c_scan=1

If this works you need to make the changes permanent I think you can do that with this command...

> sudo echo "options saa7134 i2c_scan=1" > /etc/modprobe.d/saa7134

---

### Post by Rofl77 on 2008-06-06
Thanks for your help, fenian.  I got through the first couple steps with no problems.  When I entered this command:
> sudo modprobe saa7134 i2c_scan=1 
the result was:
> FATAL: Error inserting saa7134 (/lib/modules/2.6.24-16-generic/ubuntu/media/saa7134/saa7134.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for saa7134
Here's the result from the dmesg command:
> [  681.472701] saa7134: disagrees about version of symbol videobuf_streamoff
[  681.472711] saa7134: Unknown symbol videobuf_streamoff
[  681.472810] saa7134: disagrees about version of symbol videobuf_poll_stream
[  681.472813] saa7134: Unknown symbol videobuf_poll_stream
[  681.473028] saa7134: disagrees about version of symbol videobuf_dma_free
[  681.473031] saa7134: Unknown symbol videobuf_dma_free
[  681.473108] saa7134: disagrees about version of symbol videobuf_reqbufs
[  681.473110] saa7134: Unknown symbol videobuf_reqbufs
[  681.473287] saa7134: disagrees about version of symbol videobuf_waiton
[  681.473289] saa7134: Unknown symbol videobuf_waiton
[  681.473442] saa7134: disagrees about version of symbol videobuf_dqbuf
[  681.473444] saa7134: Unknown symbol videobuf_dqbuf
[  681.473832] saa7134: disagrees about version of symbol videobuf_stop
[  681.473834] saa7134: Unknown symbol videobuf_stop
[  681.474097] saa7134: Unknown symbol videobuf_queue_pci_init
[  681.474130] saa7134: disagrees about version of symbol videobuf_dma_unmap
[  681.474132] saa7134: Unknown symbol videobuf_dma_unmap
[  681.474167] saa7134: disagrees about version of symbol videobuf_read_stream
[  681.474169] saa7134: Unknown symbol videobuf_read_stream
[  681.474219] saa7134: disagrees about version of symbol videobuf_querybuf
[  681.474221] saa7134: Unknown symbol videobuf_querybuf
[  681.474316] saa7134: disagrees about version of symbol video_unregister_device
[  681.474318] saa7134: Unknown symbol video_unregister_device
[  681.474351] saa7134: disagrees about version of symbol videobuf_qbuf
[  681.474353] saa7134: Unknown symbol videobuf_qbuf
[  681.474436] saa7134: disagrees about version of symbol video_device_alloc
[  681.474438] saa7134: Unknown symbol video_device_alloc
[  681.474470] saa7134: disagrees about version of symbol videobuf_read_one
[  681.474472] saa7134: Unknown symbol videobuf_read_one
[  681.474550] saa7134: disagrees about version of symbol video_register_device
[  681.474552] saa7134: Unknown symbol video_register_device
[  681.474782] saa7134: disagrees about version of symbol videobuf_iolock
[  681.474784] saa7134: Unknown symbol videobuf_iolock
[  681.474858] saa7134: disagrees about version of symbol videobuf_streamon
[  681.474860] saa7134: Unknown symbol videobuf_streamon
[  681.475067] saa7134: disagrees about version of symbol video_device_release
[  681.475069] saa7134: Unknown symbol video_device_release
[  681.475100] saa7134: disagrees about version of symbol videobuf_mmap_mapper
[  681.475102] saa7134: Unknown symbol videobuf_mmap_mapper
[  681.475205] saa7134: disagrees about version of symbol videobuf_cgmbuf
[  681.475207] saa7134: Unknown symbol videobuf_cgmbuf
[  681.475328] saa7134: disagrees about version of symbol videobuf_to_dma
[  681.475331] saa7134: Unknown symbol videobuf_to_dma
[  681.475361] saa7134: disagrees about version of symbol videobuf_mmap_free
[  681.475363] saa7134: Unknown symbol videobuf_mmap_free

Should saa7134 be removed and reinstalled somehow?  Thanks again.  Cheers.

---

### Post by cariboo on 2008-06-06
I've got an MSI tv@nyhere card that is based on the saa7134 chipset, in my case I had t o add a file to /etc/modprobe.d I called it saa7134 and it contents are:

```
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=17
```

The way I found the card number was by the brute force method I just kept inserting the module with different card numbers until I could change the inputs in tvtime

To install the module on the commad line type:

```
sudo modprobe saa7134 card=17
```

where 17 is the card number of my particular tv card. To remove the module type:

```
rmmod saa7134
```

there may be a couple of other modules that it depends on, remove them first. they will be automagically install the next time you install the saa7134 module.

Good luck

Jim

---

### Post by vallhaus71 on 2009-02-04
Hi, I've been having the same problem and it seems the chip is quite similar.  My card is an Asus dual card which comes bundled with the P5WD2 m/board. It has a Philips saa7131e chip together with some other numbers; TN05211 and CE4403.
I've been at it on and off for months now, but after many reinstalling still I get nothing. Tvtime is coming up and scanning but not finding anything.

I am using Ubuntu 8.10 x64 bit

For more info this is the output of my;

sudo lspci
01:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d0)

sudo lspci -v
01:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
	Subsystem: ASUSTeK Computer Inc. Device 818c
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at e7edb800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [40] Power Management version 2
	Kernel driver in use: saa7134
	Kernel modules: saa7134

I have been through a lot of threads here and tried everything suggested by some people, I have the firmware files in /lib/firmware and /lib/firmware/`uname -r` folders.  I installed the latest mercurial software.  Edited /etc/modprobe.d/options and also created the file /etc/modprobe.conf
This is the output of my
dmesg|grep saa
[   13.686940] saa7130/34: v4l2 driver version 0.2.14 loaded
[   13.687202] saa7134 0000:01:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.687213] saa7133[0]: found at 0000:01:01.0, rev: 208, irq: 22, latency: 64, mmio: 0xe7edb800
[   13.687224] saa7133[0]: subsystem: 1043:818c, board: ASUSTeK P7131 Dual [card=78,insmod option]
[   13.687243] saa7133[0]: board init: gpio is 0
[   13.687413] input: saa7134 IR (ASUSTeK P7131 Dual) as /devices/pci0000:00/0000:00:1e.0/0000:01:01.0/input/input7
[   13.922789] saa7133[0]: i2c eeprom 00: 43 10 8c 81 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   13.922812] saa7133[0]: i2c eeprom 10: 00 01 22 00 ff 20 ff ff ff ff ff ff ff ff ff ff
[   13.922834] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 01 01 03 08 ff 00 3c ff ff ff ff
[   13.922854] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.922875] saa7133[0]: i2c eeprom 40: ff 22 00 c2 96 ff 02 30 15 ff ff ff ff ff ff ff
[   13.922897] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.922918] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.922938] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.922958] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.922978] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.922997] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.923015] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.923033] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.923050] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.923070] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.923092] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.132677] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[   18.156533] saa7133[0]: registered device video0 [v4l2]
[   18.156636] saa7133[0]: registered device vbi0
[   18.156727] saa7133[0]: registered device radio0
[   18.248056] saa7134 ALSA driver for DMA sound loaded
[   18.248115] saa7133[0]/alsa: saa7133[0] at 0xe7edb800 irq 22 registered as card -2
[  986.988377] saa7134 ALSA driver for DMA sound unloaded
[ 1003.214324] saa7130/34: v4l2 driver version 0.2.14 loaded
[ 1003.216708] saa7133[0]: found at 0000:01:01.0, rev: 208, irq: 22, latency: 64, mmio: 0xe7edb800
[ 1003.216727] saa7133[0]: subsystem: 1043:818c, board: ASUSTeK P7131 Dual [card=78,insmod option]
[ 1003.216746] saa7133[0]: board init: gpio is 0
[ 1003.222738] input: saa7134 IR (ASUSTeK P7131 Dual) as /devices/pci0000:00/0000:00:1e.0/0000:01:01.0/input/input9
[ 1003.429393] saa7133[0]: i2c eeprom 00: 43 10 8c 81 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[ 1003.429428] saa7133[0]: i2c eeprom 10: 00 01 22 00 ff 20 ff ff ff ff ff ff ff ff ff ff
[ 1003.429450] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 01 01 03 08 ff 00 3c ff ff ff ff
[ 1003.429472] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1003.429494] saa7133[0]: i2c eeprom 40: ff 22 00 c2 96 ff 02 30 15 ff ff ff ff ff ff ff
[ 1003.429515] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1003.429537] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1003.429559] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1003.429581] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1003.429603] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1003.429625] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1003.429646] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1003.429668] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1003.429690] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1003.429712] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1003.429733] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1003.484524] saa7133[0]: i2c scan: found device @ 0x96  [???]
[ 1003.492520] saa7133[0]: i2c scan: found device @ 0xa0  [eeprom]
[ 1003.556684] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[ 1007.543255] saa7133[0]: registered device video0 [v4l2]
[ 1007.549061] saa7133[0]: registered device vbi0
[ 1007.549634] saa7133[0]: registered device radio0
[ 1007.637972] saa7134 ALSA driver for DMA sound loaded
[ 1007.638046] saa7133[0]/alsa: saa7133[0] at 0xe7edb800 irq 22 registered as card -2

however running;
sudo dmesg i get this
[ 1003.556684] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[ 1003.636017] tda829x 0-004b: setting tuner address to 61
[ 1003.700514] tda829x 0-004b: type set to tda8290+75a
[ 1007.543255] saa7133[0]: registered device video0 [v4l2]
[ 1007.549061] saa7133[0]: registered device vbi0
[ 1007.549634] saa7133[0]: registered device radio0
[ 1007.620712] dvb_init() allocating 1 frontend
[ 1007.637972] saa7134 ALSA driver for DMA sound loaded
[ 1007.638046] saa7133[0]/alsa: saa7133[0] at 0xe7edb800 irq 22 registered as card -2
[ 1007.682492] tda10046: chip is not answering. Giving up.

Is there anyone who can lend a hand, this is the only thing that is keeping me hooked up to XP, as soon as I sort this I'll be an ubuntu follower.  many thanks

---

### Post by wolfen69 on 2009-02-04
see [this]("http://www.linuxtv.org/wiki/index.php/Saa713x_devices") page for more info.

---

### Post by buntunub on 2009-02-04
I wrote a guide recently for that chipset type. Give [this]("http://ubuntuforums.org/showthread.php?t=884438") a try. On first glance this -

> [ 1003.636017] tda829x 0-004b: setting tuner address to 61
[ 1003.700514] tda829x 0-004b: type set to tda8290+75a

looks like your issue. You have to find the right card/tuner for what you have, and that is something you will have to find on your own, for the most part. I have linked the Gentoo wiki on this that goes into some details on that, and the list of cards and tuners. For me, setting tuner=56 in my /etc/modprobe.d/options did the trick along with setting the correct card number as well (card=59). For sound, you will have a new set of struggles, but nothing too difficult if you follow the guide(s) out there.

---

### Post by vallhaus71 on 2009-02-04
thanks wolfen and buntunub, I'll go through and check.
Do you have an idea how many tuners are there available (i.e.) 1 - ????

Also to set new tuner settings do I need to reboot all the time or may I simply use the rmmod command before modprobe?

many thanks

---

### Post by Maheriano on 2009-02-04
Coming back later to read this.

---

### Post by vallhaus71 on 2009-02-05
Going through the bttv gallery I found out that actually my card is named Asus Wifi Tv and not dual. It's the one with Marvell chip.  I'm trying something new like different card numbers but still no joy.  I think the major problem is with the firmware because I cannot get a /dev/dvb folder.  In the linuxtv wiki it says the firmware might not be loaded, I put the .fw files in /lib/firmware and /lib/firmware/`uname -r` (just to make sure).  Apart from modprobe, is there a particular command I need to know about to load it.
If anyone has any ideas I'll be very grateful for your help. tks

---

### Post by vallhaus71 on 2009-02-05
will start a new thread on this

---

