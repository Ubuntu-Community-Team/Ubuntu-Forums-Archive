---
title: "Combine two sound devices into a virtual one?"
date: 2008-06-23
forum: Multimedia Software
---

### Post by b33z on 2008-06-23
Hi Everyone.

I figured that one of you might be able to help me with my problem, I 
have googled my a*s off for the last three days without any luck.

I want my sound to play simultaneously through my headphonejack and the S/PDIF output, and then through pulseaudio.

Is there any way to create a virtual sound device from two other devices and then make pulseaudio to use it?

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

Nvidia CK804 = headphone output (this seems to be the default sound device)

Nvidia CK804 - IEC958 = S/PDIF output.

I can play sounds through both the devices one at a time, when I choose 
'NVidia CK804 - IEC958' through System > Preferences > Sound and restart X i get sound **in some applications** 
through the S/PDIF output. When I choose any other playback device (NVidia CK804, ALSA, Pulseaudio, OSS) I only get sound through my headphonejack.

So is there anyone that can point me in the right direction? Or have any idea for another solution?

At least someone might know how to change the default sound device to the S/PDIF output (device 0,2 )? so that I can use the digital output with Pulseaudio.

(I followed this guide to setup Pulseaudio: [http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+cards](http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+cards) )

Best Regards
Johan

---

### Post by briancb on 2010-10-27
In 10.10 I solved the problem.

Install pulse audio device chooser (padevchooser) Synaptic

launch padc

It will appear as an icon in panel

choose configure local sound server

check box simultaneous output

This send sound to both the amp and via bluetooth to headphones

---

