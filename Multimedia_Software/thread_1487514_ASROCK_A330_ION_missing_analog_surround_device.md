---
title: "ASROCK A330 ION missing analog surround device?"
date: 2010-05-19
forum: Multimedia Software
---

### Post by fi2 on 2010-05-19
Hi all,

Right up-front I must say sorry, for I am aware of the comprehensive stuff found here about alsa audio, yet, I got stuck here.

I have installed Ubuntu 10.04 (32) on a brand-new ASROCK A330ION. In the final stage it is meant to be used with fiber output, but for the time of messing around I connected an active 5.1 speaker set to the jack sockets. Now here comes the bit: whatever I do only the 2 front speakers perform. I have dug up the net and tried editing /etc/pulse/... config files, creating different kind of .asoundrc, name it. No use. Whatever I do, it is stereo. 

I tried to reroute channels in .asoundrc, but all I could achieve was that all the centre and rear wav-s of the *"speaker-test (...) -twav*" appeared on the same old front speakers. 

The one thing that gave me a tickle is that on quite a few forums it is mentioned, that the analog surround output should be on device 1. All aplay -l tells about my system however is 0 and 3. 

> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0How can it be? As a matter of fact I found even a red-capital warning somewhere stating, that all this messing around is obsolete above Ubuntu 9.10, for it is in menu->preferences->sound->hardware. Now All I can find there is either analog stereo, or HDMI.

Is it really so, that I can only use surround on fiber? Something tells me I miss a bit somewhere, at it just annoys me greatly. Could anybody give me a hand please?

Here is my alsa-info:
[http://www.alsa-project.org/db/?f=701f8a7c4f5432c63546e7f05d9624aaa7fe4f0e](http://www.alsa-project.org/db/?f=701f8a7c4f5432c63546e7f05d9624aaa7fe4f0e)

---

### Post by lidex on 2010-05-20
First of all, upgrade your alsa install via the alsa-upgrade link in my sig. If you previously install alsa-backports, uninstall it first. Then post this info: ```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Also helpful is the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by fi2 on 2010-05-21
Thanks. In the meantime I had found your link and by now everything works.

As I searched the web, I found much complain from users who were just simply unable to get surround sound. Just wonder, why is 1.0.21 in the latest distribution, while alsa 1.0.23 has been available for long. Any reason for that? It seems, surround sound will not work out for those, who try it with the old alsa driver. 

Anyway, thanks again.

---

### Post by svenni on 2010-11-11
I have the same problem on my ASRock A330 ION, but have installed Ubuntu 10.10 with the new Alsa drivers. So I'm able to enable "Smart 5.1" in alsamixer, but I still don't have any option to set the output levels of the rear and center/LFE channels. Is there anything else you did to get this working?

---

