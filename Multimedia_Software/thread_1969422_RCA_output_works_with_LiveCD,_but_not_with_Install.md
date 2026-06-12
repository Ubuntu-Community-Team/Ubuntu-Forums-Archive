---
title: "RCA output works with LiveCD, but not with Installation"
date: 2012-04-30
forum: Multimedia Software
---

### Post by register4everything on 2012-04-30
I have two monitors... one is a TV hooked up through HDMI from my Nvidia 9800 GTX+, and another monitor is hooked up to the VGA output.

I have an RCA cable from the onboard RealTek audio device going to the inputs for HDMI1 in the back of my television.

When I put in a LiveCD for 10.04, and try without install... I get audio to my television.

But after installation, I noticed I no longer get audio through my RCA connection...


$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.4 LTS
Release:	10.04
Codename:	lucid

$ uname -a
Linux 2.6.32-41-generic-pae #88-Ubuntu SMP Thu Mar 29 14:24:36 UTC 2012 i686 GNU/Linux

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audio [Plantronics Wireless Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC889A Digital
    IEC958 (S/PDIF) Digital Audio Output
front:CARD=Audio,DEV=0
    Plantronics Wireless Audio, USB Audio
    Front speakers
surround40:CARD=Audio,DEV=0
    Plantronics Wireless Audio, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Audio,DEV=0
    Plantronics Wireless Audio, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Audio,DEV=0
    Plantronics Wireless Audio, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Audio,DEV=0
    Plantronics Wireless Audio, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Audio,DEV=0
    Plantronics Wireless Audio, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Audio,DEV=0
    Plantronics Wireless Audio, USB Audio
    IEC958 (S/PDIF) Digital Audio Output



I'm confused. I've tried different tricks to get it to work and, he last one I tried was installing gnome-alsamixer, but somehow that disconnected the second hdmi connected monitor to come on.

For now, I'm just going to boot off the CD and enjoy sound through my TV.

TIA.

---

### Post by register4everything on 2012-04-30
liveCD

ubuntu@ubuntu:~$ aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC889A Digital
    IEC958 (S/PDIF) Digital Audio Output
front:CARD=Audio,DEV=0
    Plantronics Wireless Audio, USB Audio
    Front speakers
surround40:CARD=Audio,DEV=0
    Plantronics Wireless Audio, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Audio,DEV=0
    Plantronics Wireless Audio, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Audio,DEV=0
    Plantronics Wireless Audio, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Audio,DEV=0
    Plantronics Wireless Audio, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Audio,DEV=0
    Plantronics Wireless Audio, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Audio,DEV=0
    Plantronics Wireless Audio, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
ubuntu@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audio [Plantronics Wireless Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by register4everything on 2012-05-10
I hoped someone would've known why :(

---

