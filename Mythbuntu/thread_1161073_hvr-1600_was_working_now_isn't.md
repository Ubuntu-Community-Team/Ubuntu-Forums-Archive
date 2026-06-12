---
title: "hvr-1600 was working now isn't"
date: 2009-05-16
forum: Mythbuntu
---

### Post by don_engtech on 2009-05-16
Had my hvr-1600 working well under mythbunu 8.04.  About two weeks ago it stopped working and shows up as "unavailable". Tried going back through the setup guide [http://www.mythtv.org/wiki/Hauppauge_HVR-1600]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600"), Stopping mythtv-backend and mythtv-status first. When I get to ```
sudo modprobe cx18
``` I get ```
FATAL: Module cx18 not found.
``` 

```
:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0c.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
00:0d.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
00:0e.0 Multimedia video controller: Conexant CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)

```

```
:~$ dmesg |grep cx18
``` returns nothing...

```
:~$ dmesg |grep ivtv
[   32.452603] ivtv:  Start initialization, version 1.1.0
[   32.452810] ivtv0: Initializing card #0
[   32.452815] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   32.479133] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   32.568299] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   32.924739] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   32.927744] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   33.142904] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   33.292075] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   33.370748] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   33.370764] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   33.370780] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   33.370799] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   33.370814] ivtv0: Registered device radio0 for encoder radio
[   33.370817] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   33.370843] ivtv:  End initialization
[   51.523033] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   51.720208] ivtv0: Encoder revision: 0x02060039

```

As you can see I also have a PVR150 and it is working fine.
ivtv seems to auto detect the hvr-1600 as well...
 
 I am not sure if I am just forgetting a step in the setup so any ideas would be appreciated, Thanks.
Don

---

### Post by klc5555 on 2009-05-16
> **don_engtech said:**
> Had my hvr-1600 working well under mythbunu 8.04.  About two weeks ago it stopped working and shows up as "unavailable". Tried going back through the setup guide [http://www.mythtv.org/wiki/Hauppauge_HVR-1600]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600"), Stopping mythtv-backend and mythtv-status first. When I get to ```
sudo modprobe cx18
``` I get ```
FATAL: Module cx18 not found.
``` 

```
:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0c.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
00:0d.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
00:0e.0 Multimedia video controller: Conexant CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)

```

```
:~$ dmesg |grep cx18
``` returns nothing...

```
:~$ dmesg |grep ivtv
[   32.452603] ivtv:  Start initialization, version 1.1.0
[   32.452810] ivtv0: Initializing card #0
[   32.452815] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   32.479133] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   32.568299] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   32.924739] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   32.927744] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   33.142904] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   33.292075] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   33.370748] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   33.370764] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   33.370780] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   33.370799] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   33.370814] ivtv0: Registered device radio0 for encoder radio
[   33.370817] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   33.370843] ivtv:  End initialization
[   51.523033] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   51.720208] ivtv0: Encoder revision: 0x02060039

```

As you can see I also have a PVR150 and it is working fine.
ivtv seems to auto detect the hvr-1600 as well...
 
 I am not sure if I am just forgetting a step in the setup so any ideas would be appreciated, Thanks.
Don

Was there a kernel/module update package recently for 8.04, say, two weeks ago?  I'd say trust your modprobe: you likely don't have a cx18 module. cx18 support didn't get added to the kernel tree until 2.6.26, while I think 8.04 still runs 2.6.24-something. So if your kernel/modules for 2.6.24 were updated, you may have to compile the cx18 from v4l source as you most likely did when you first installed the card.

---

### Post by don_engtech on 2009-05-16
Yes, I do think it was an update that broke it...

```
:~$ uname -r
2.6.24-24-generic
```

I have as I said gone back through the install instructions:
```
1a. Download the latest

 sudo apt-get install mercurial linux-headers-$KERNEL_VERSION build-essential
 hg clone http://linuxtv.org/hg/v4l-dvb

1b. Compile and add the module to your kernel:

 cd v4l-dvb
 make
 sudo make install
 sudo make unload
 sudo modprobe cx18

```

That last line ```
sudo modprobe cx18
``` is where I get the "FATAL: Module cx18 not found."

Do you know if 9.04 has cx18 support built in? If so I may just do a fresh install...

---

### Post by klc5555 on 2009-05-17
The kernel tree => 2.6.26 includes cx18. So 9.04 should have it, as should 8.10 (when updated).

What I don't know is whether the current stock kernel with these versions include a cx18 built from v4l source post-January 4th, when the first-analog-capture-corruption bug mentioned in the wiki was fixed. Can't easily test it myself, because my own 1600 is stuck in a Slackware backend with a custom kernel rather than in one of my Ubuntu machines.

But the point is that current 8.10 and 9.04 should have some form of cx18 out-of-the box.

---

### Post by don_engtech on 2009-05-17
I started clean install of Mythbuntu 9.04 this morning and system sees and uses hvr-1600 with no intervention other than backend setup, it was automagic! Now I just need a better antenna, I am 40mi from xmitter. HD channels are not staying locked, SDs are good though.

Thanks for your input,
Don

---

