---
title: "Unable to record sound on eeePC 1001PX since Ubuntu 12"
date: 2013-01-14
forum: Multimedia Software
---

### Post by PatrickM31 on 2013-01-14
Hello,

I own 2 eeePC 1001PX under Ubuntu 12.04 LTS and 12.10.
The first one  has been directly installed under 12.04 and then upgraded to 12.10.
The second one has been updated from 11.10 to 12.04.
On the second one the sound recording worked perfectly under 11.10 (I use Skype) but not anymore since 12.04!
I have no sound reading problem (music, videos).

I run gnome-sound-recorder (or Audacity) and the leval bar moves when I speak but I can't ear the sound recorded:
"This file contains no playable streams."

patrick@patrick-1001PX:~$  gnome-sound-recorder
** (gnome-sound-recorder:2597): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-CQaHJZPbHv: Connection refused
/tmp/gsr-record-2013-01-15-040638-2597.E5L2QW/tmp/gsr-record-2013-01-15-040638-2597.E5L2QWERROR: This file contains no playable streams.
DEBUG MESSAGE: qtdemux.c(527): gst_qtdemux_post_no_playable_stream_error (): /GstPlayBin:playbin/GstDecodeBin:decodebin1/GstQTDemux:qtdemux0:
no known streams found
ERROR: This file contains no playable streams.
DEBUG MESSAGE: qtdemux.c(527): gst_qtdemux_post_no_playable_stream_error (): /GstPlayBin:playbin/GstDecodeBin:decodebin1/GstQTDemux:qtdemux0:
no known streams found


Sound settings: input: internal microphone I have set volume to the max level.

It doesn't work anymore with Audacity.

Under Alsamixer I select the only card available (internal) and all the levels are at the max:
Card: HDA Intel
Chip: Realtek ALC269

Can you help me?

Thanking you in advance


patrick@patrick-1001PX:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
patrick@patrick-1001PX:~$ lspci
00:00.0 Host bridge: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR2427 802.11bg Wireless Network Adapter (PCI-Express) (rev 01)
patrick@patrick-1001PX:~$ 

patrick@patrick-1001PX:~$ sudo modprobe snd-
[sudo] password for patrick: 
FATAL: Module snd_ not found.
patrick@patrick-1001PX:~$ 


PS: I have asked for help on the french forum, with several screenshots, but it didn't succeeded to repair.
[http://forum.ubuntu-fr.org/viewtopic.php?id=1124401](http://forum.ubuntu-fr.org/viewtopic.php?id=1124401)

---

### Post by PatrickM31 on 2013-01-17
...

---

### Post by PatrickM31 on 2013-01-18
Could someone indifcate me the configuration files involved in sound recording?

How should they be?

If I modify them manually, it should work or show me where is the problem.

Nobody owns an eeePC 1001PX running Ubuntu 12?

Thanking you in advance.

---

### Post by xc3RnbFO8P on 2013-01-18
Check the permissions in .dbus/session-bus/*

---

### Post by PatrickM31 on 2013-01-20
patrick@patrick-1001PX:~$ ll .dbus/session-bus/*
-rw-rw-r-- 1 patrick patrick 463 Jan 20 06:58 .dbus/session-bus/472c865e84bddabee37aaa540000000b-0
patrick@patrick-1001PX:~$

---

### Post by PatrickM31 on 2013-01-25
These rights seem OK.

Is there a document which explains how work sound recording, with its configuration files.

Thanks.

---

### Post by PatrickM31 on 2013-02-03
Any help about configuration files ?

---

### Post by PatrickM31 on 2013-02-08
Sound recording works fine on Ubuntu 11 (11.10) but not on Ubuntu 12 (12.04LTS or 12.10).

I have tested it again with à live USB key.

I have downgrade my Ubuntu (12.10 => 11.10) and sound recording is OK now.

But this solution is not satisfactory.
I don't want to be blocked to Ubuntu 11.

What has change on sound recording between 11.10 and 12.04?

Thanks.

---

### Post by fredcarru on 2013-02-12
Same for me on acer aspire one model ZG5.
Not only skype but also under sound, sound settings, input there is no signal indicated when I tap the microphone. It works fine with an external mic.

---

