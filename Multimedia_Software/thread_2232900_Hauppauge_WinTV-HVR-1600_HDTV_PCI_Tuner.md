---
title: "Hauppauge WinTV-HVR-1600 HDTV PCI Tuner"
date: 2014-07-04
forum: Multimedia Software
---

### Post by dimitri6 on 2014-07-04
Hi all,

I have a [Hauppauge WinTV-HVR-1600]("http://www.hauppauge.com/site/products/data_hvr1600.html") Internal PCI ATSC digital TV tuner and I can't get it to work with Ubuntu linux 14.04 x64. 

Ubuntu 14.04 is seeing the card in "Additional Drivers" tab as "Conexant Systems, Inc.: CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder" but "This device is not Working" and there aren't any drivers to pick to make it work.

In the past, I was able to watch HD TV with TVTime app under openSUSE  12.3 out of the box with no additional tweaks or drivers. But ever since I switched to Ubuntu I can't get the card to work.  I can also watch TV with it when I dual-boot with Windows 7 x64.

I Googled for solutions, but most solutions are outdated and/or have broken links and none work.

I will appreciate any advice.

Thank you in advance.

---

### Post by xc3RnbFO8P on 2014-07-05
I think that Laptop and Tablets are killing the Tv cards.
Did you check **dmesg** output?

---

### Post by dimitri6 on 2014-07-05
pa1067@linux-main:~$ dmesg | grep cx
[   14.403600] cx18:  Start initialization, version 1.5.1
[   14.403648] cx18-0: Initializing card 0
[   14.403650] cx18-0: Autodetected Hauppauge card
[   14.403783] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   14.413433] cx18-0: cx23418 revision 01010000 (B)
[   14.646442] cx18-0: Autodetected Hauppauge HVR-1600
[   14.646444] cx18-0: Simultaneous Digital and Analog TV capture supported
[   14.776289] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   14.794737] cx18-0: Registered device video1 for encoder MPEG (64 x 32.00 kB)
[   14.794742] DVB: registering new adapter (cx18)
[   14.904301] cx18 0000:11:0c.0: DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   14.904491] cx18-0: DVB Frontend registered
[   14.904494] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
[   14.904536] cx18-0: Registered device video33 for encoder YUV (20 x 101.25 kB)
[   14.904641] cx18-0: Registered device vbi1 for encoder VBI (20 x 51984 bytes)
[   14.904673] cx18-0: Registered device video25 for encoder PCM audio (256 x 4.00 kB)
[   14.904728] cx18-0: Registered device radio1 for encoder radio
[   14.904730] cx18-0: Initialized card: Hauppauge HVR-1600
[   14.904828] cx18:  End initialization
[   14.921271] cx18-alsa: module loading...
[   15.349368] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   15.498715] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   15.504896] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   16.904012] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   16.923836] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
pa1067@linux-main:~$

---

### Post by xc3RnbFO8P on 2014-07-05
Try MeTv

---

### Post by dimitri6 on 2014-07-05
> **Ringi said:**
> Try MeTv

I downloaded "Me TV" from the Software centre and it works!!!  Thank you SO much!

So I assume Me TV is the only TV viewer software that works with Hauppauge cards in Ubuntu.

I have another question. Me TV has a variety of options to chose from. Which is the best "Video Driver" and "Deinterlance type" to pick?
I have an nVidia GeForce 9800 GT GPU with nVidia's proprietary drivers.

Again,

Thank you SO much!  I've been fiddling with this card for more than a year!

---

