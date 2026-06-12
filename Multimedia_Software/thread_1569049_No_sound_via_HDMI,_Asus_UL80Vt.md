---
title: "No sound via HDMI, Asus UL80Vt"
date: 2010-09-06
forum: Multimedia Software
---

### Post by Eithrial on 2010-09-06
Hi,
I know that topic were mentioned several times, but I cant find solution anywhere.

My notebook is Asus UL80Vt
Ubuntu 10.04 64bit
Nvidia GeForce G210 M(Drivers v 256.53)
Intel Graphic Card is disabled
Sound Card: Realtek ALC269 @ Intel 82801IB
Alsa v 1.0.23

aplay -l
```
karta 0: Intel [HDA Intel], urz&#261;dzenie 0: ALC269 Analog [ALC269 Analog]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 1: NVidia [HDA NVidia], urz&#261;dzenie 3: NVIDIA HDMI [NVIDIA HDMI]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 1: NVidia [HDA NVidia], urz&#261;dzenie 7: NVIDIA HDMI [NVIDIA HDMI]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 1: NVidia [HDA NVidia], urz&#261;dzenie 8: NVIDIA HDMI [NVIDIA HDMI]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 1: NVidia [HDA NVidia], urz&#261;dzenie 9: NVIDIA HDMI [NVIDIA HDMI]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0

```hope it doesnt need translation

It's my first time with linux, so I really dont know if I should post here more pieces of information.
Ive already tried editing alsa-base.conf, however there weren't line with "options snd-hda-intel  index=-2", which, accroding to topic with Alsa Upgrade Script, should have been included.

In Windows 7 everything works fine.

What should I do?

---

### Post by kelvin.illa on 2010-09-06
I don't think there's anything that has to do with hardware selection regarding this. I was almost going to post a similar topic asking for help but I found my solution -- it really very simple. Try if it works for you:

Click on the 'sound' button on the tray. Go to "Sound Preferences..." Go to the "Hardware" tab, and under "Profile" choose "HDMI output..." That's it!

I hope this works for you as it did for me. The thing is, it just didn't change automatically.

You say you're new to Linux so I say "welcome!"

---

### Post by Eithrial on 2010-09-06
Thanks for answer, but everything in sound settings seem to be set correctly.

---

### Post by kelvin.illa on 2010-09-06
Do you not have an HDMI option on the "Profiles" under the "Hardware" tab?

---

### Post by Eithrial on 2010-09-06
I have it and is set correctly.

---

### Post by kelvin.illa on 2010-09-06
Oh, okay.

I'm sure someone else has had that and already found a solution... somewhere.

Cheers.

---

### Post by Yellow Pasque on 2010-09-06
Maybe this will help? [http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

---

### Post by traumkeks on 2010-12-09
Please, how did you deactivate your intel graphics card? I can't get that to work

---

### Post by Teodore on 2010-12-12
Eithrial,

I am using UL80Vt, after installing ubuntu 10.04.1 64 bit, and installing the repo Nvidia driver,
I managed to get the HDMI audio to work by first installing Alsa v 1.0.23 using the following guide 

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

then i refer to the link given by Temüjin

[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

and the changes i made is

If using PulseAudio, add the following line to /etc/pulse/default.pa: 
 load-module module-alsa-sink device=hw:1,7 
Change the device to hw:1,7 instead of hw:1,3

In addition, i add myself to the audio group as the guide suggested and reboot.
Start the alsamixer, press F6 to select the HDA nvidia, and press m to unmute S/PDIF 1 and voila ! My speakers are pumping the sound of joy!

---

