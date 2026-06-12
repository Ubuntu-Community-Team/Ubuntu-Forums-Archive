---
title: "ASUS AT3IONT-I HDMI audio"
date: 2010-06-09
forum: Multimedia Software
---

### Post by praetorian20 on 2010-06-09
Hi,
I recently built an HTPC with an ASUS AT3IONT-I motherboard and have been able to get everything functioning except for HDMI audio. I've been googling this issue and found [this]("http://ubuntuforums.org/showthread.php?t=1476915") posting. I followed the instructions in the link posted in there but no joy. I also found [another]("http://forum.linuxmce.org/index.php?action=printpage;topic=9637.0") post that said only alsa 1.0.22.1 would work so I removed .23 and installed .22; no difference. Since I'd been mucking with the sound settings after reading various suggestions I decided to do a clean install of lucid and start fresh; which is where I'm at right now.

So has anybody had any luck with this mobo and HDMI? I'm a Linux n00b so a little detail with the help instructions will be greatly appreciated :-).

I've tried setting System -> Preferences -> Sound -> Hardware to HDMI and IEC958. I've also run alsamixer and unmuted everything including SPDIF; also all sliders are set to 100%.

This is the current (clean 10.04 install) output from aplay -l:
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Thanks in advance for any help!

---

### Post by lidex on 2010-06-10
Have a look here:
[http://forum.xbmc.org/showthread.php?t=59877]("http://forum.xbmc.org/showthread.php?t=59877")

More:
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240")
[http://ubuntuforums.org/showthread.php?t=1466111]("http://ubuntuforums.org/showthread.php?t=1466111")

---

### Post by praetorian20 on 2010-06-14
Thanks for replying, I tried out the suggestions on all those links this weekend but nothing fixes the problem! The first link with the alsa upgrade to .23 has a problem, well, not the script itself but the alsa source download. It fails to compile and when I googled it, someone had suggested getting the latest snapshot using -snap, but I have no idea how to do that. 

The other suggestions involved modifying /etc/modprobe.d/alsa-base.conf by adding 
```

options snd-hda-intel ...

```I tried out a bunch of different suggestions, with enable_msi and without, with probe_mask and without etc. but it seems as soon as I add this line to the configuration file the soundcard disappears. aplay -l returns an error about no soundcards being installed (or something similar to that effect).

I also tried installing xbmc in the hope that maybe it ships with audio drivers but I can't get sound through it either.

Also, Application -> Sound & Video -> Gnome Alsa Mixer does not show any SPDIF outputs although alsamixer does (and I have these unmuted). I checked Edit -> Sound Card Properties to see whether these were simply hidden but they're absent in that list too. I remember reading somewhere that SPDIF needs to be unmuted in that GUI too.

What should I try next? Should I attempt to upgrade to alsa .23? If so, could you please tell me how to get a snapshot?

Thanks again for your help!

---

### Post by praetorian20 on 2010-06-15
Anybody? Please help!

---

### Post by praetorian20 on 2010-07-26
> **praetorian20 said:**
> Hi,
I recently built an HTPC with an ASUS AT3IONT-I motherboard and have been able to get everything functioning except for HDMI audio. I've been googling this issue and found [this]("http://ubuntuforums.org/showthread.php?t=1476915") posting. I followed the instructions in the link posted in there but no joy. I also found [another]("http://forum.linuxmce.org/index.php?action=printpage;topic=9637.0") post that said only alsa 1.0.22.1 would work so I removed .23 and installed .22; no difference. Since I'd been mucking with the sound settings after reading various suggestions I decided to do a clean install of lucid and start fresh; which is where I'm at right now.

So has anybody had any luck with this mobo and HDMI? I'm a Linux n00b so a little detail with the help instructions will be greatly appreciated :-).

I've tried setting System -> Preferences -> Sound -> Hardware to HDMI and IEC958. I've also run alsamixer and unmuted everything including SPDIF; also all sliders are set to 100%.

This is the current (clean 10.04 install) output from aplay -l:
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Thanks in advance for any help!


I found the fix! It didn't have anything to do with Ubuntu or Alsa, it  was my TV. I have this PC hooked to a Samsung plasma, and the TV gives  you the option of naming each of the HDMI hookups (game, blu-ray etc.). I  know it does things differently based on the name because the first  time I hooked it up the picture was crappy until I scrolled down the  list of names and got to "DVI PC". Turns out that option was the cause  of all this trouble. I needed to pick "PC" instead and now there's  sound.

I still had to unmute SPDIF in alsamixer and change the sound output to HDMI manually but that was it.

---

### Post by lidex on 2010-07-26
Good News! Would you please mark the thread as solved using "Thread Tools' up top?

---

### Post by bolojo on 2010-09-03
> **lidex said:**
> Good News! Would you please mark the thread as solved using "Thread Tools' up top?
 
Hi all, i know that the thread was tagged as solved but i want to know if there will be a patch or something like this for sound through HDMI (which is not working in my case) in a newer kernel than 2.6.32-24-generic which i am using. The rest of the system is ubuntu 10.04 64 bits and a LG M2762D tv. Thanks in advance and excuse me if this is not the right place for my post because this is my first one in here!

---

