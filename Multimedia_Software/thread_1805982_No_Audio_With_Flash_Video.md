---
title: "No Audio With Flash Video"
date: 2011-07-16
forum: Multimedia Software
---

### Post by hayhursm on 2011-07-16
Hello Everyone,

I am using Firefox 5.0 with Ubuntu Lucid x64 and I have no audio with Flash video.  Audio works just fine on other applications so I'm guessing this might be a permission's issue or setting of some sort?  I also have: **flashplugin-installer 11.0.1.60~110713-ppa0~lucid & flashplugin-nonfree 11.0.1.60~110713-ppa0~lucid** installed with **ALSA v1.0.24.2**.  Any help is always appreciated!

---

### Post by lovinglinux on 2011-07-17
Try this: [http://pulseaudio.org/wiki/PerfectSetup#ALSAApplications](http://pulseaudio.org/wiki/PerfectSetup#ALSAApplications)

---

### Post by hayhursm on 2011-07-19
> **lovinglinux said:**
> Try this: [http://pulseaudio.org/wiki/PerfectSetup#ALSAApplications](http://pulseaudio.org/wiki/PerfectSetup#ALSAApplications)


Thank you for your reply!  What exactly are you suggesting?  The Wiki suggest to install Beta version of Flash Player 11 which I already have installed on my system.  All sound worked before I upgraded my video card.  Before I was using an Nvidia that had the S/PDIF connector going to the motherboard.  The video card I have now has it's own on board sound processor and no S/PDIF connection is needed.  Here are some details:

[B]desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0[/B]

I need **card 2, device 9**; I had to insert this into /etc/pulse/default.pa: **load-module module-alsa-sink device=hw:2,9 **to get sound.  Also, my Pulseaudio Sound Preferences lists two HDA NVidia options but the one designated for HDMI (refer to screen shot) has no sound.  I'm guessing Pulseaudio detected the HDMI output but is using the wrong device number?  If that's the case, is there a way to fix that?

---

### Post by hayhursm on 2011-07-22
Bump

---

### Post by lovinglinux on 2011-07-22
I am suggesting this: [http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions](http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions)

I am not using Ubuntu right now, but once you make those changes, you need to reconfigure flash to use alsa from the sound preferences. I guess you can only see that option while playing some flash video.

---

### Post by hayhursm on 2011-07-22
> **lovinglinux said:**
> I am suggesting this: [http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions](http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions)

I am not using Ubuntu right now, but once you make those changes, you need to reconfigure flash to use alsa from the sound preferences. I guess you can only see that option while playing some flash video.

Thank you, that fixed it!!  Adding this from your link to /etc/asound.conf fixed the problem: 
[B]pcm.pulse {
type pulse
}
ctl.pulse {
type pulse
}
pcm.!default {
type pulse
}
ctl.!default {
type pulse
}[/B] Of course, your first reply link contained about the same information so that's my fault for not paying closer attention. Again, thank you for helping a Linux newb, at least these little set backs allow me to learn something :)

---

### Post by lovinglinux on 2011-07-23
> **hayhursm said:**
> Thank you, that fixed it!!  Adding this from your link to /etc/asound.conf fixed the problem: 
[B]pcm.pulse {
type pulse
}
ctl.pulse {
type pulse
}
pcm.!default {
type pulse
}
ctl.!default {
type pulse
}[/B] Of course, your first reply link contained about the same information so that's my fault for not paying closer attention. Again, thank you for helping a Linux newb, at least these little set backs allow me to learn something :)

You are welcome.

---

