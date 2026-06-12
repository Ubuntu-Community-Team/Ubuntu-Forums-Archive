---
title: "Unable to set snd-usb-audio as default device"
date: 2008-12-03
forum: Multimedia Software
---

### Post by constchar* on 2008-12-03
Hello, I've recently reinstalled Ubuntu again (it's like having an old friend back!)
and I installed 8.04 and then proceeded to upgrade to 8.10 (all went smooth)
but, as with every version of Ubuntu, I've had audio problems.

First off I have a Logitech USB 960 Headset and an Onboard RealTek AC'97 audio card.
I generally prefer to use my headset over my speakers so I decided that I would
configure my Ubuntu system to use the Headset as the default audio device, well unfortunately it didn't turn out very smooth.

I tried to do it the Ye Olde Way by editing /etc/modprobe.d/alsa-base to
change the snd-usb-audio line to "options snd-usb-audio index=0" but unfortunately
my RealTek card always gets index 0 regardless of how I modify alsa-base, in fact at most the headset will completely disappear depending on where I place the line.

Second I tried to use asoundconf set-default-card, unfortunately this has
absolute no effect and the RealTek card remains the default.

Third I tried padevchooser application to set the default card to the
headset and it somewhat works from what I can tell but every time I
logout/reboot the RealTek card goes back to the default.

One solution I've come across is to disable the RealTek card in the BIOS
but I don't want to since sometimes I'll turn on my speakers when I show
people stuff or I want to listen to music while working around the house, etc..

Any help would be greatly appreciated.

---

### Post by markbuntu on 2008-12-03
You can use the padevchooser Configure local sound server Simultaneous Output tab and click the box. 

This will put a virtual simultaneous output device in the Pulse Audio volume control/Output Devices so you can have both headset and speakers. You can also choose the headset as the default device there by right clicking on it in Output Devices.

You can choose either device or the simultaneous device for any application that plays through pulseaudio by going to the playback tab and right clicking on it and choosing move stream.

The Pulse Audio Volume Control is really the best way to control multiple devices.

---

### Post by psyke83 on 2008-12-03
Yep - PulseAudio ignores the ALSA module indexes. Use PulseAudio Volume Control to set the default playback device.

For more information, see: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by constchar* on 2008-12-04
No luck, I followed all the instructions but padevchooser still does not save my default audio device, it always goes back to the sound card when I logout.

---

### Post by psyke83 on 2008-12-05
> **constchar* said:**
> No luck, I followed all the instructions but padevchooser still does not save my default audio device, it always goes back to the sound card when I logout.

It's probably a bug in PulseAudio. You can "force" your selection, though. See: [http://ubuntuforums.org/showpost.php?p=6277111&postcount=878](http://ubuntuforums.org/showpost.php?p=6277111&postcount=878)

---

