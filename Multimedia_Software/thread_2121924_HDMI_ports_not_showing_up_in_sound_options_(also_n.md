---
title: "HDMI ports not showing up in sound options (also no audio)"
date: 2013-03-03
forum: Multimedia Software
---

### Post by SteveWilliams on 2013-03-03
I have a HTPC which runs Ubuntu 12.10 and XBMC and yesterday, the amplifier that I use for it broke, so I got another.

Upon setting up the new amp et all, I found that my sound through HDMI no longer works. I have tested that it's fine with the PlayStation3 that I have, so I can rule out any issues with the amplifier.

I have a Gigabyte H77N-WiFi board (with 2 HDMI outputs) and neither show up in the sound settings panel. When I do 

What's even stranger, is that I need to have both HDMI outputs connected to the amplifier now (or any other device) so that I can get the HDMI output (visual) to work as well.

I've tried literally everything that I can find on Google, and I can also reproduce the problem on 13.04. This wasn't a problem before yesterday, but I also did reboot for updates on the machine yesterday which could be the cause of this.

I'm willing to reinstall tomorrow, but I was hoping somebody could tell me if there is a way to fix this rather than a reinstall also causing the same problems.

List of things I've tried
1) installing pavucontrol and swapping to the correct HDMI output 
2)sintax: sudo nano /etc/modprobe.d/alsa-base.conf (enter) then add this line to the end of the file sintax: options snd-hda-intel model=auto (then use the end page controls to rewrite and save the file, then exit console)  (bad spelling here was a copy and paste)
3) Running the speaker test yields no sound

This is the output of my "aplay -l":
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

This is my "aplay -L":

null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default:CARD=PCH
    HDA Intel PCH, ALC892 Analog
    Default Audio Device
sysdefault:CARD=PCH
    HDA Intel PCH, ALC892 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, HDMI 0
    HDMI Audio Output
hdmi:CARD=PCH,DEV=1
    HDA Intel PCH, HDMI 1
    HDMI Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample mixing device
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample mixing device
dmix:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Hardware device with all software conversions

Thanks in advance!

---

