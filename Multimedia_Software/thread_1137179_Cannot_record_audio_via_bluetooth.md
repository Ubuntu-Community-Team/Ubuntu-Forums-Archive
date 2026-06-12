---
title: "Cannot record audio via bluetooth"
date: 2009-04-25
forum: Multimedia Software
---

### Post by yankeeDDL on 2009-04-25
Hello,
I have a bluetooth headset (Jabra BT8040) connected to my PC via Bluetooth dongle.
I can pair the device and I can listen to audio on my headset, but I cannot record anything.
The headset works (I have a laptop with Windows and I can use the headset with Skype) so it has to be something wrong with my configuration.

I have read several threads and a few (LONG!) launchpad bugs but I found no solutions.

Here's some info:
OS: Ubuntu 8.10 x64

============================================================
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

============================================================
arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: U0x46d0x8d7 [USB Device 0x46d:0x8d7], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

============================================================
more .asoundrc
pcm.bluetooth {
        type bluetooth
        device 00:1A:45:BA:F7:74
        profile “auto”
}

============================================================
hciconfig
hci0:	Type: USB
	BD Address: 00:11:E0:03:35:12 ACL MTU: 384:8 SCO MTU: 64:8
	UP RUNNING PSCAN ISCAN 
	RX bytes:22262 acl:196 sco:0 events:2369 errors:0
	TX bytes:1626227 acl:5723 sco:0 commands:79 errors:0

====================================================

sudo hcitool scan
Scanning ...
	00:1A:45:BA:F7:74	Jabra BT8040
====================================================


I think this is all the relevant info.
I notice in one thread that in the "Bluetooth preferences" application, supposedly, there's a "service" tab. I don't have it: only see pc-0 and General.

Thanks in advance ...

---

### Post by yankeeDDL on 2009-04-26
Bump ... anybody?

---

### Post by yankeeDDL on 2009-04-27
Re-bump ... please?

---

### Post by yankeeDDL on 2009-04-28
After 2 more days of attempts ... I managed to fix it. Proud of me!
This page was crucial to get to a resolution: the "default" solution did not work for me (that's the solution indicated in most threads/websites", but then I notice the "catch" related to Skype 2.0 "bug" ...
[http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices)

I still cannot record/play through aplay/arecord, but it doesn't matter since Skype works well now.

Hope this helps somebody else too.

---

