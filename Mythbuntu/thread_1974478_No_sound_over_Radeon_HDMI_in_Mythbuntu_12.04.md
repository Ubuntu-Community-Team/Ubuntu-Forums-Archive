---
title: "No sound over Radeon HDMI in Mythbuntu 12.04"
date: 2012-05-06
forum: Mythbuntu
---

### Post by Rich99 on 2012-05-06
Hi, I've just tried my first install of Mythbuntu 12.04. It installed fine, but I have no sound.  I have a Radeon 5450, connected by HDMI to a LCD TV.  Lspci lists the HDMI:
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cedar HDMI Audio [Radeon HD 5400/6300 Series]

I ran additional drivers, and had 2 options for fglrx - fglrx graphics driver & fglrx graphics driver (post-release updates).  The first installs fine, the second fails, so I'm currently running with the first installed - according to catalyst driver 8.96.4.

aplay -l gives:
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

If I run alsamixer, I can choose from 2 devices - HDA Intel PCH, which has all the controls I'd expect, and HDA-Audio Generic (which I presume is the Radeon HDMI), but which only has a S/PDIF control. I've unmuted the S/PDIF, but no joy.

I tried installed xfce4-mixer, and if I choose 'HDA-Audio Generic; the only control I have is 'IEC958'.

I've tried adding radeon.audio=1 to /etc/default/grub, but it made no difference.

Does it sound like I've got the right drivers installed, or am I better grabbing the most current fglrx driver & building it myself?  The fact that the driver is not showing the right controls in alsamixer etc, makes me wonder if the right driver is installed?

If the lack of controls etc in alsamixer is the norm, then how do I choose which output I want programs to use?

---

### Post by Rich99 on 2012-05-06
Well, I successfully built the latest catalyst drivers, but it made no difference.

Any ideas what's happenning?

---

### Post by Rich99 on 2012-05-06
Hmm - I unmuted the S/PDIF for the HDMI in Alsamixer, and managed to get some noise from the mythfrontend audio config/test.  Maybe S/PDIF means HDMI?

---

