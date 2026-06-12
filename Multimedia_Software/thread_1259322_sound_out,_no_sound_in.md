---
title: "sound out, no sound in"
date: 2009-09-06
forum: Multimedia Software
---

### Post by pdc124 on 2009-09-06
hardware etc 

00:0c.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: Micro-Star International Co., Ltd. Device 5900
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at e800 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: C-Media PCI
	Kernel modules: snd-cmipci

 i get no sound recording with skype  and nothing with gnome-sound-recorder. In fact i get this 

paul@zimmy-desktop:~$ gnome-sound-recorder

(gnome-sound-recorder:4490): GStreamer-CRITICAL **: gst_implements_interface_cast: assertion `gst_element_implements_interface (GST_ELEMENT (from), iface_type)' failed
/tmp/gsr-record-Untitled-4490.9AF3ZUpaul@zimmy-desktop:~$ 

 ive tried using pulseaudio for everything and ALSA for everything, but I get no sound recording ( playback is fine) 


anything Im missing ?

---

### Post by pdc124 on 2009-09-08
so is there any way of updating just gstremer before the next big upgrade , so that I can see if i can get this working  ?

---

### Post by pdc124 on 2009-09-12
so I have spent a couple of days with google and tried a number of things. I think its something tyo do with skype and virtual sound devices. i installed skype-oss and now have  no sound out from skype and this 
aul@zimmy-desktop:~$ skype -v 
Skype 2.0.0.72-oss
Copyright (c) 2004-2007, Skype Limited
paul@zimmy-desktop:~$ skype 

RtApiOss: OSS playback device (/dev/dsp) is busy.


RtApiOss: OSS playback device (/dev/dsp) is busy.


RtApiOss: OSS playback device (/dev/dsp) is busy.


 grhhhhhhh

almost enough to make me use windows

---

### Post by BubbaBlues on 2009-09-16
I hear ya. I'm trying to get it also.:confused:

---

