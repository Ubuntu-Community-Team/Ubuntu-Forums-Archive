---
title: "No audio through HDMI cable"
date: 2009-08-07
forum: Mythbuntu
---

### Post by 4dognight on 2009-08-07
I just upgraded my tube tv to a LCD TV. I want to use audio through the hdmi cable to the tv. I have an abit an-m2hd MB,. It comes with HDMI output. It has HD audio also. I dont have an audio amp , so I dont want to use SPDIF.
I have the HD audio enabled in the BIOS.
When I run aplay -l I get,

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I dont think it has HDMI capabilities under linux, or somethings not working.
I have run alsamixer and I have the IEC958 enabled.
I have another myth server using the same MB, and I do use SPDIF for it, and it works. But for this server I just want to use the HDMI cable to carry the audio and video, as I dont use an audio amp for this tv.

I have tried every setting for audio output device in myth frontend settings. Only ones that work are the analog.

I curently get around it by using the analog output and connect a pair of PC speakers up. This seems cheesy though, and would prefer to use the HDMI cable.

any suggestions?

---

### Post by larsolav on 2009-08-07
Looks like the HDMI audio is not set up, as it is not showing up after aplay -l.
This MB uses the NVIDIA® GeForce®7050PV/nForce 630a chipsets, are you using the NVIDIA drivers?

---

### Post by 4dognight on 2009-08-07
Yes, I am running the nvidia driver.

---

### Post by Maheriano on 2009-08-07
The Linux HDMI driver isn't yet 1.3a compliant last I checked so it simply mixes DVI video and SPDIF audio down the HDMI line. So if you run SPDIF you'll get the exact same sound.

---

### Post by 4dognight on 2009-08-07
> **Maheriano said:**
> The Linux HDMI driver isn't yet 1.3a compliant last I checked so it simply mixes DVI video and SPDIF audio down the HDMI line. So if you run SPDIF you'll get the exact same sound.

I do know my other server works using SPDIF.(I forgot to check what aplay -l returns on the other server, using SPDIF)
 Are you saying I am out of luck trying to get audio through my HDMI cable? That would be no fun.

---

### Post by Lampi on 2009-08-07
what alsa version are you using? (*cat /proc/asound/version*)?

With Jaunty you got kernel 2.6.28 - so the ALSA version should be 1.0.18 - You might find out HDMI audio works with the latest alsa-build (1.0.20)

There is a script in this forum to help you update to the new version, you find it here: [**ALSA Upgrade Script**]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810") try it! If it doesn't help you can revert the changes it made

---

### Post by Maheriano on 2009-08-07
> **4dognight said:**
> I do know my other server works using SPDIF.(I forgot to check what aplay -l returns on the other server, using SPDIF)
 Are you saying I am out of luck trying to get audio through my HDMI cable? That would be no fun.

You can get it but the driver simply filters the SPDIF signal through the HDMI cable, it doesn't transfer true HDMI sound. So even if you manage to get it, it'll be no different than simply hooking up a SPDIF cable.

---

### Post by 4dognight on 2009-08-08
I got it to work!
Thanks to this web page on how to upgrade ALSA, which provided the HDMI device.

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
aplay now returns
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


And this page on how to configure ALSA

[http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto#Discover_what_settings_your_sound_card_wants](http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto#Discover_what_settings_your_sound_card_wants)

My .asoundrc file contains

pcm.!default {
       type hw
       card 0
       device 3
   }
pcm.!default {
     type plug
     slave.pcm "hdmi"
  }



Thanks for all who replied, and those who wrote the info in the links.

---

