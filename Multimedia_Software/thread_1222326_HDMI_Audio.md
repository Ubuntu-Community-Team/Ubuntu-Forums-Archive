---
title: "HDMI Audio"
date: 2009-07-24
forum: Multimedia Software
---

### Post by Moth Dust on 2009-07-24
Hello, This is my first post, sorry it's already been discussed so much :sad:. Basically I've been lurking around these forums and other forums and websites for an answer for about 3 days now, putting in maybe 6 hours of work each day and I can't figure this out. I have an HP notebook dv9700 and have video out for HDMI but audio from laptop speakers, would like audio out HDMI to TV.

I am going with ALSA since that seemed to be what everyone else was doing, this disables my ability to adjust volume with the touchpad on my laptop, but beggers can't be choosers. All I'm saying is if pulse would be easier than feel free to let me know since I can't really claim to know the differences between them.

aplay -l gives me


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplay -L gives me

front:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)

and cat /proc/asound/devices gives me

 0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
  5: [ 0- 1]: hardware dependent
 16: [ 0- 0]: digital audio playback
 22: [ 0- 6]: digital audio playback
 24: [ 0- 0]: digital audio capture
 30: [ 0- 6]: digital audio capture
 33:        : timer

Now when I tried to test 0,6 with a wav file I got an error. But being kind of a noob in Linux not sure if that matters or not, pretty sure my list would say HDMI if it was recognizing it at all. I also assumed it would be an NVIDIA device and not Intel but I'm not too familiar with troubleshooting audio problems.

I'd like to thank you guys and girls in advance, my time lurking has shown me this is a very mature forum. Hope I'm not being a pest >.<!!

---

### Post by igorzwx on 2009-07-24
Check if your hardware is supported by OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[http://www.opensound.com/osshw.html](http://www.opensound.com/osshw.html)

---

### Post by Moth Dust on 2009-07-24
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

that is my audio card. It is in the list of supported cards in the first link you gave me but not the second. I'll assume that the first link is updated more often.

What does OSS have to do with ALSA though?

---

### Post by igorzwx on 2009-07-24
they do not like each other.
you can have OSS4 or ALSA, not both

---

### Post by igorzwx on 2009-07-24
see Wikipedia -> oss -> open sound system

---

### Post by Moth Dust on 2009-07-24
I do seem to have an OSS mixer on here. But I don't remember mentioning that? Are you suggesting that OSS is causing ALSA to not see some of my devices? Should i uninstall OSS?

---

### Post by igorzwx on 2009-07-24
it is ALSA emulation of OSS, not OSS4
read the Wikipedia story about OSS

---

### Post by Moth Dust on 2009-07-24
I read the OSS wiki. Basicly it was used back in the old days when it was freeware then it became proprietary and the community abandoned it and now it's freeware again. I'm not really 100% on why you wanted me to read that article. Unless you are suggesting that switching from ALSA to OSS might solve my HDMI problem.

---

### Post by igorzwx on 2009-07-24
It is up to you to decide which you like more.
You can install another Ubuntu 9.04 and try OSS4 there

But, in any case, this info might be usefull:
[7.1 Troubleshooting HDAudio devices]("http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices")
[http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices](http://wiki.archlinux.org/index.php/OSS#Troubleshooting_HDAudio_devices)

---

### Post by markbuntu on 2009-07-24
OSS4 will not do anything for an HDMI problem since HDMI is part of the graphics processor and so needs to be supported by the graphics driver. If you have a nvidia or ati card this is available in the newer proprietary drivers. The open source ati and radeonhd drivers have recently added some HDMI support for some cards but you would need the latest versions to get that.

I am not sure what is going on with intel but HDMI should be supported by the intel driver which i think is currently blacklisted in Jaunty and so unavailable. There is some threads around here about that.

The generic VESA driver does not have HDMI support and never will.

So, igorzwx, you should stop your trolling around about OSS4 until you are really sure your advice will actually help people with their specific problems.

---

### Post by Moth Dust on 2009-07-24
Thank you for the reply Markbuntu. I've upgraded to the latest Nvidia drivers and that aloud me to use my TV through the HDMI port on this laptop. Unfortunately The audio is the problem and it did not solve that. I'll continue browsing the forums for an answer but as i've said I haven't found a solution yet. Any suggestions are welcome though :D.

---

### Post by markbuntu on 2009-07-25
You should have an HDMI device in System/Preferences/Sound now and you can use it that way. Or you can add this line in the /etc/pulse.default.pa file to have it appera in the pulseaudio vlume control

load-module module-alsa-source device=hw:1,3

replace the hw designation with the device desgnation you find with

aplay -l

the card number will be the first number and the subdevice will be the second number. This is usually 3 for HDMI devices on the gpu.

FYI, this is all fixed in pulseaudio v 0.9.15 which is available here if you want to try it

[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)

---

