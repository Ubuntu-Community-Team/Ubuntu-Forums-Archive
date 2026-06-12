---
title: "No sound with HDMI output on a AT3N7A-I"
date: 2010-10-12
forum: Multimedia Software
---

### Post by Bjarne J on 2010-10-12
Hi
 
I'm a rookie
 
Have started to build a mediecenter with XBMC, but have stoped, because there are no sound after i installed Ubuntu 10.10, using HDMI output, and have also tried all other sound output with no success 
 
MB: ASUS AT3N7A-I 
Ubuntu 10.10
 
Some more info:
 
xbmc@xbmc:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
 
xbmc@xbmc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
Subdevices: 2/2
Subdevice #0: subdevice #0
Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708S Digital [VT1708S Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0
 
xbmc@xbmc:~$ aplay -L
pulse
Playback/recording through the PulseAudio sound server
front:CARD=NVidia,DEV=0
HDA NVidia, VT1708S Analog
Front speakers
surround40:CARD=NVidia,DEV=0
HDA NVidia, VT1708S Analog
4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
HDA NVidia, VT1708S Analog
4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
HDA NVidia, VT1708S Analog
5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
HDA NVidia, VT1708S Analog
5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
HDA NVidia, VT1708S Analog
7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
HDA NVidia, VT1708S Digital
IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
HDA NVidia, NVIDIA HDMI
HDMI Audio Output
 
Any there have some ideas or solution to my problem.

---

### Post by avnibu on 2010-10-12
I have the same problem. HP dv4-1040ei with Nvidia drivers on maverick 10.10 don't have any sound from HDMI. I can select the HDMI sound from sound preferences and everything goes silent afterwards.

Funny thing is everything used to work fine at 10.04.

---

### Post by Bjarne J on 2010-10-12
Found the solution installed GNOME ALSA Mixer and all was set to MUTE, and now i have sound :popcorn:

---

### Post by talleddy on 2010-12-22
How do you get video to play on the HDMI output. I am a newbie and I can't figure it out.I hooked up my HDMI cable in hopes that it would just automatically detect it and then install whatever it needed to make it work. But nothing happened. so then I went into system --> prefrences --> monitors and selected detect monitors but it only showed the laptop screen. I want to be able to hook my computer up to my TV and watch hulu and things like that. If you guys have any help that would be greatful. please PM me if you can help.

Thanks

---

