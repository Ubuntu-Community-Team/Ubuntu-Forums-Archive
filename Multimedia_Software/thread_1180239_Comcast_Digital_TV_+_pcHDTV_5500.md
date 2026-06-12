---
title: "Comcast Digital TV + pcHDTV 5500"
date: 2009-06-06
forum: Multimedia Software
---

### Post by kihjin on 2009-06-06
I just recently purchased a pcHDTV 5500. Before I got this I was using a leadtek card to watch TV in tvtime. I have a direct digital line from comcast which hooks into the cable box, and then to my computer. I upgraded so I could see a better picture.

After installing the card and booting up my system, I tried it out with tvtime. Picture comes in better than the leadtek card, but it is obviously not high definition. Comparing what shows up on my computer and what shows up on a direct (from the cable box) to my lcd tv supports this. Obviously the signal I am getting in tvtime is analog.

The pcHDTV 5500 card also has a digital interface which shows up under /dev/dvb. Prior to this card, I have no experience with digital streams in linux so I'm finding myself rather frustrated with this process. I just want to view the high definition stream coming from my cable box. I don't even need to change the channel as I will use my remote for that.

Before posting this I of course tried to accomplish this myself. My research indicated that I needed to have 'dvb-apps' installed, perform a channel scan to generate a channels.conf (I only really need 1 channel). After that I can use mplayer, xine or gnutv to watch the stream. In performing the scan I need some initial tuning file which I have no idea what this is or which I need to use.

I tried my best to guess at what ones might work, but each scan iteration I performed yield no usable channels.conf. In each case when it scans a frequency I get a "tuning failed," error.

The rest of this post contains hopefully relevant system information you may be able to use to help guide me to getting this working. I'm not yet interested in trying to receive over the air broadcasts, for now I just want to watch my cable. 

```
$ lspci 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
03:06.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
03:06.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
03:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:07.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
03:07.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
03:07.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
```

```

$ ls -lR /dev/dvb/
/dev/dvb/:
total 0
drwxr-xr-x 2 root root 120 2009-06-06 10:03 adapter0

/dev/dvb/adapter0:
total 0
crw-rw----+ 1 root video 212, 4 2009-06-06 10:03 demux0
crw-rw----+ 1 root video 212, 5 2009-06-06 10:03 dvr0
crw-rw----+ 1 root video 212, 3 2009-06-06 10:03 frontend0
crw-rw----+ 1 root video 212, 7 2009-06-06 10:03 net0
```

```
$ dmesg | grep 5500
[   11.167436] cx88[0]: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47,autodetected], frontend(s): 1
[   11.443693] cx88[0]/2: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47]
```

```
$ dmesg | grep dvb
[   11.443688] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   11.443691] cx88/2: registering cx8802 driver, type: dvb access: shared
```

```
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
```

```
$ lsmod | grep dvb
cx88_dvb               32772  0 
cx88_vp3054_i2c        11264  1 cx88_dvb
cx8802                 27012  1 cx88_dvb
cx88xx                 88104  4 cx88_dvb,cx88_alsa,cx8802,cx8800
videobuf_dvb           16516  3 cx88_dvb,cx8802,cx88xx
dvb_core              106924  3 lgdt330x,cx88_dvb,videobuf_dvb
videobuf_dma_sg        22660  5 cx88_dvb,cx88_alsa,cx8802,cx8800,cx88xx
videobuf_core          29828  5 cx8802,cx8800,cx88xx,videobuf_dvb,videobuf_dma_sg
```

Hopefully that's a sufficient amount of system information. Thanks for your help.

---

### Post by kihjin on 2009-06-07
bump

---

### Post by xc3RnbFO8P on 2009-06-07
Did you try Kaffeine or Me-TV?

---

### Post by kihjin on 2009-06-07
Ringi, thanks for the response.

Both Kaffeine and Me-TV use xine, which I have installed. xine requires a channels.conf which up to this point I have had trouble generating. 

Currently I am pursuing a set of instructions found on this page

[http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_(For_ATSC/QAM_Tuner_Cards_--_USA/Canada](http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_(For_ATSC/QAM_Tuner_Cards_--_USA/Canada))

I should know the result hopefully soon, though the site warns that it can take some time. Getting lots of "(tuning failed)" errors though.

---

### Post by xc3RnbFO8P on 2009-06-07
> I have a direct digital line from comcast which hooks into the cable box, and then to my computer.
Do you know the output format of your cable box?

---

### Post by kihjin on 2009-06-07
I'm not sure. I do I know that I can plug from my cable box to my LCD HDTV and get a digital reception on channel 3 without any configuration. 

This setup means I can't change the channel with my TV's remote, I must use Comcast's remote- I am fine with that of course. 

I suspect it is VHF? I tried to tune to 61.25 MHz without any success...

---

### Post by kihjin on 2009-06-07
I have a DCH70 Motorola "Standard Defintion All-Digital Cable Receiver"

According to manual:

"RF Out - Ch 3/4 modulated audio/video (SDTV) to TV or VCR"

This may be a problem...

[edit]

However, when I watch on-demand it comes in very crisp and clear.

---

### Post by xc3RnbFO8P on 2009-06-07
> However, when I watch on-demand it comes in very crisp and clear.
Yes if you convert digital to analog (in Europe 720x576 to 320x280)

---

