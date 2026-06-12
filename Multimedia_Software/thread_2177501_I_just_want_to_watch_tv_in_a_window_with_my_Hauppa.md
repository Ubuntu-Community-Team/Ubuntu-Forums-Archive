---
title: "I just want to watch tv in a window with my Hauppauge 1600"
date: 2013-09-29
forum: Multimedia Software
---

### Post by troy7 on 2013-09-29
Maybe this doesn't exist - but I'm looking for an app that will let me watch TV on my computer with my Hauppauge 1600 tv tuner card.  I get digital tv from an antenna.  I was using this in an XP box, but thought I'd try to upgrade.  I've checked out MythTV, tvheadend, XBMC - tvheadend was close, but only work with analog signals.  I don't want to dedicate my computer for this, I just want to watch TV when I'm not using it for NetFlix or movies in VLC.

Any suggestions, posts I missed, etc.  would be greatly appreciated.

---

### Post by deadflowr on 2013-09-29
Is [tvtime]("http://packages.ubuntu.com/search?keywords=tvtime") still available?

Or useful?

---

### Post by troy7 on 2013-09-29
Thanks for the suggestion of tvtime.  I checked into it - the Hauppauge 1600 used the ivtv driver - which is mpeg2 based.  Tvtime doesn't support mpeg2 - so couldn't watch live tv with that.  At least that is how I read it.

---

### Post by deadflowr on 2013-09-29
Don't know if something like me-tv would work.
There's also Kaffeine.

There are a couple of others, which I have forgotten about.

---

### Post by Bucky Ball on 2013-09-29
*Thread moved to **Multimedia & Video**.*

Me-TV. That's it. Has auto-scan so you don't need to set that up. It's in the repos. Install it and try.

(deadflowr ninja-ed me!) ;)

PS: With the dongle plugged in, run this in a terminal:

```
lsusb
```

Please post the result back here.

---

### Post by MartyBuntu on 2013-09-29
Me-TV or Kaffeine.

Both very easy to setup.

---

### Post by MartyBuntu on 2013-09-29
> **Bucky Ball said:**
> 

```
lsusb
```

Please post the result back here.

Should be: **lspci**

The 1600 is a PCI card.

---

### Post by Bucky Ball on 2013-09-29
> **MartyBuntu said:**
> Should be: **lspci**

The 1600 is a PCI card.

All good. My mistake. The result of that, then, please ...

---

### Post by howefield on 2013-09-29
> **troy7 said:**
> ....VLC.

That'll do it.

---

### Post by troy7 on 2013-09-29
Here's my output from lspci:

00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GDH (ICH7R/ICH7DH) SATA Controller [RAID mode] (rev 01)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550]
01:00.1 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550 Series] (Secondary)
05:09.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
3f:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755 Gigabit Ethernet PCI Express (rev 02)

---

### Post by troy7 on 2013-09-29
Something caught my eye on the CX23418 chip - see the ivtv driver download from Ubuntu Software Center - doesn't support that chip - so went to ivtb home page - found a linke for a Beta driver for this chip.  Seems like it should be ok cause the things left to be developed are mostly on the analog side - I'm looking for over the air digital tv.

However, this turned into quite an exercise - I'm stuck at the Beta driver make file want the kernel source - I downloaded the kernel source, but must not have put it in the correct location?  Right now the kernel source in in the Beta driver folder.  Perhaps it should be installed at /usr/src - but not sure how to proceed.

Since this is getting to be more time than I wanted to invest, started searching on what I should get for a tv tuner card that will work with Me TV or TVTime.  TV time lists using a bttv 0.9 driver using the BT878 and BT848 chipset - but not sure how to go about finding such a card.

My goal is to be able to watch over the air (antenna) digital tv [US - NTSC] in a window on my computer.  So, direction on getting the ivtv CX23418 driver going or suggestions on which card I should purchase to work with ME Tv or TVTime is what I'm looking for now.  Thanks.

---

### Post by Bucky Ball on 2013-09-29
This might help:

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

This is what you're looking for:

Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder

Naturally, the Hauppauge card doesn't use a Hauppauge chipset, but a Conexant. ;)

PS: I use an Ezycap. Uses Realtek chipset and works a treat. But I'd stick with this for the moment ... see what else crops up.

PPS: Have you got v4l-utils installed? You may need to install the v4l stuff. You can have a search on that is a clue. Try that and restart. (You're might need to restart to get it working whatever you try.)

---

### Post by troy7 on 2013-09-29
Made a good step tonight  - thanks.

To document what I did, I followed the link in the previous post - going down to the Installation guide section, followed link [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers) where I followed the basic approach as outlined on that page.  When done with Hot to Obtain, Build, and Install V4l-DVB, went back to original page [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600) and jumped down to Firmware.  Did a reboot and then a dmesg | grep cs18 and see:

[   12.765295] cx18:  Start initialization, version 1.5.1
[   12.765331] cx18-0: Initializing card 0
[   12.765334] cx18-0: Autodetected Hauppauge card
[   12.765377] cx18 0000:05:09.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.765386] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   12.778190] cx18-0: cx23418 revision 01010000 (B)
[   12.998710] cx18-0: Autodetected Hauppauge HVR-1600
[   12.998713] cx18-0: Simultaneous Digital and Analog TV capture supported
[   13.174946] cs5345 5-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   13.264102] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
[   13.264107] DVB: registering new adapter (cx18)
[   13.356599] cx18 0000:05:09.0: DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   13.356866] cx18-0: DVB Frontend registered
[   13.356869] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
[   13.356967] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
[   13.357051] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   13.357779] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
[   13.357783] cx18-0: Initialized card: Hauppauge HVR-1600
[   13.358055] cx18:  End initialization
[   13.382830] cx18-alsa: module loading...
[   13.487693] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   13.618902] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   13.625746] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   14.476107] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   14.495804] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)

So, looks like all 3 firmware files loaded.

My only plan for getting TV going is to use the instructions at [http://tvremote.sourceforge.net/documentation.php#video](http://tvremote.sourceforge.net/documentation.php#video) - my drawback is this documentation request installation of ivtv-utils, which I'm not sure will work with what I just did.  I see I can open VLC and try to stream - but my attempts there - selecting a device and hitting stream so far - haven't gone far.

VLC suggestions would be appreciated - that's where I plan to start reading/searching tomorrow.

---

### Post by troy7 on 2013-09-30
I may be getting close.

I'm using Me TV - got channels to scan and have audio and video.  At first, it was really choppy - but then the sun when down and now it's not too bad.  I have a whole housle antenna amplifier - but i've read other posts that say the Hauppauge 1600 doesn't have the strongest over the air receiver.  I'm going to order a signal amplifier to use just to go to this card - see if I get it usable.

---

### Post by Bucky Ball on 2013-10-01
External antannae (on the roof) is best. Connect computer directly to the antennae cable, NOT daisy-chained through another device, e.g. antennae to PVR then PVR out to computer. 

In my case, I have antennae cable to two-way splitter with one side going to computer in studio and the other to PVR/TV setup in lounge. Perfect. 

If you're watching digital TV the internal antennaes are usually not great. Choppy and artifacts. Good luck and glad you've got something happening. I'd say it's now just a matter of getting the antennae and connections right because all is good at the computer end (and Me-TV rocks!). ;)

---

### Post by MartyBuntu on 2013-10-01
> **troy7 said:**
> I'm going to order a signal amplifier...

Amplifiers are mostly garbage. They amplify noise as well as signal generally.

You just need a good, quality antenna.

---

### Post by troy7 on 2013-10-04
I agree on the antenna - I have a $120 roof mount antenna.  I also have an antenna rotator so I can tune in the stations I'm watching.  [www.tvfool.com](www.tvfool.com) and [www.rabbitears.info](www.rabbitears.info) help a lot with that.

Anyway, I'm doing to declare this post closed cause I now have a signal I'm happy with.  I'm using Me-TV from [https://answers.launchpad.net/me-tv/](https://answers.launchpad.net/me-tv/) and had to adjust the buffers by doing:

The easiest way to increase the buffer size is to write these 3 lines to ~/.me-tv/xine.config (if it does not exist create a new file),
 video.output.xv_deinterlace_method=linearblend
engine.buffers.audio_num_buffers:500
engine.buffers.video_num_buffers:1000

I did have to create this file.  

Another thing worth mentioning is Xubuntu 12.04 already has the drivers needed for Hauppauge 1600 ATSC.  I discovered this by restoring my base install (always do this with CloneZilla) and did a dmesg | grep cx8.  This process would of been a whole lot easier if I knew where to go - hopefully this post helps the next guy.

---

### Post by Bucky Ball on 2013-10-05
The Me-TV in the repos didn't work? Anyhow, glad you've got something running you're happy with and thanks for marking as solved. That WILL help the next person. ;)

---

