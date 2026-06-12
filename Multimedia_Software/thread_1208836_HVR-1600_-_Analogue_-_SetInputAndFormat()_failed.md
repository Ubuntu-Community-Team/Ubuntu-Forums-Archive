---
title: "HVR-1600 - Analogue - SetInputAndFormat() failed"
date: 2009-07-09
forum: Multimedia Software
---

### Post by nautilus on 2009-07-09
Hey all.  I'm running Intrepid with MythTV 0.21.0+fixes18722-0ubuntu1

I can't change channels with my HVR-1600..  I mean, it works in that when I select Live TV it will start-up and play whatever my starting channel is, and from there if I use dov4l to change the channel in a terminal it indeed changes (without error), but when I try to change the channel in MythTV by either channel up/down or directly it craps out by freezing for 5 seconds or so, then dumping me back into the menu with an apology screen.

In any case, it won't record scheduled programs either.  It states something similar for LiveTV as well:

```
009-07-09 02:24:29.660 TVRec(8): ASK_RECORDING 8 29 0 0
2009-07-09 02:25:02.008 TVRec(8): Changing from None to RecordingOnly
2009-07-09 02:25:02.210 TVRec(8): HW Tuner: 8->8
2009-07-09 02:25:02.284 Channel(/dev/video0): SetInputAndFormat() failed
2009-07-09 02:25:02.286 TVRec(8) Error: Failed to set channel to 27. Reverting to kState_None
2009-07-09 02:25:02.288 TVRec(8): Changing from RecordingOnly to None

```

Being that it's an HVR-1600, I have it setup as an MPEG-2 card.  And again, when I select Live TV initially, it works, I can see channel 2 (which isn't very exciting where I live).  Video and audio both work, picture is clear, and my setchan.pl script which sorts out which channel is which frequency and runs dov4l to set the channel can successfully change channels on this card, I've verified that.

So, what's failing, is this a bug?

---

### Post by JMack89427 on 2009-07-09
I have the same card in my Ubuntu 9.04 machine and used [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600) to get it up and running.  I still have a few lingering problems with it but over all it's working ok with MythTV.

---

### Post by CDN MILLWRIGHT32 on 2009-07-11
I have the same card. Tvtime will not run from the menu "cannot open capture device invalid argument"
If I run from terminal the following results 
"Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/neil/.tvtime/tvtime.xml
videoinput: Card failed to allocate capture buffers: Invalid argument"

Any thoughts?

dmesg results

[   12.253289] cx18:  Start initialization, version 1.0.1
[   12.253329] cx18-0: Initializing card #0
[   12.253332] cx18-0: Autodetected Hauppauge card
[   12.265271] cx18 0000:05:08.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   12.265278] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   12.267737] cx18-0: cx23418 revision 01010000 (B)
[   12.476924] cx18-0: Autodetected Hauppauge HVR-1600
[   12.476925] cx18-0: VBI is not yet supported
[   12.573103] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   12.573144] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   12.608636] cx18-0: Disabled encoder IDX device
[   12.608701] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   12.608704] DVB: registering new adapter (cx18
[   12.694761] cx18-0: DVB Frontend registered
[   12.694805] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   12.694844] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   12.694846] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   12.710857] cx18:  End initialization
[   21.732026] cx18 0000:05:08.0: firmware: requesting v4l-cx23418-apu.fw
[   21.981286] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   22.480026] cx18 0000:05:08.0: firmware: requesting v4l-cx23418-cpu.fw
[   22.710222] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   22.716535] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   22.912024] cx18 0000:05:08.0: firmware: requesting v4l-cx23418-apu.fw
[   23.496024] cx18 0000:05:08.0: firmware: requesting v4l-cx23418-cpu.fw
[   23.788039] cx18 0000:05:08.0: firmware: requesting v4l-cx23418-dig.fw
[   23.981885] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)

---

### Post by saedelaere on 2009-07-13
> **CDN MILLWRIGHT32 said:**
> I have the same card. Tvtime will not run from the menu "cannot open capture device invalid argument"
If I run from terminal the following results 
"Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/neil/.tvtime/tvtime.xml
videoinput: Card failed to allocate capture buffers: Invalid argument"

Any thoughts?

dmesg results

[   12.253289] cx18:  Start initialization, version 1.0.1
[   12.253329] cx18-0: Initializing card #0
[   12.253332] cx18-0: Autodetected Hauppauge card
[   12.265271] cx18 0000:05:08.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   12.265278] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   12.267737] cx18-0: cx23418 revision 01010000 (B)
[   12.476924] cx18-0: Autodetected Hauppauge HVR-1600
[   12.476925] cx18-0: VBI is not yet supported
[   12.573103] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   12.573144] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   12.608636] cx18-0: Disabled encoder IDX device
[   12.608701] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   12.608704] DVB: registering new adapter (cx18
[   12.694761] cx18-0: DVB Frontend registered
[   12.694805] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   12.694844] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   12.694846] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   12.710857] cx18:  End initialization
[   21.732026] cx18 0000:05:08.0: firmware: requesting v4l-cx23418-apu.fw
[   21.981286] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   22.480026] cx18 0000:05:08.0: firmware: requesting v4l-cx23418-cpu.fw
[   22.710222] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   22.716535] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   22.912024] cx18 0000:05:08.0: firmware: requesting v4l-cx23418-apu.fw
[   23.496024] cx18 0000:05:08.0: firmware: requesting v4l-cx23418-cpu.fw
[   23.788039] cx18 0000:05:08.0: firmware: requesting v4l-cx23418-dig.fw
[   23.981885] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)

tvtime is not working with this kind of hardware. For analog TV you may use [TV-Viewer]("http://home.arcor.de/saedelaere/index_eng.html"). Be sure to install the latest development snapshot. It offers much more than 0.7.7 and is quite stable. If you have any questions you can reach us on irc.freenode.net #tv-viewer

Regards

---

