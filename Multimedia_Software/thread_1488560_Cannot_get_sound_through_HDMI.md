---
title: "Cannot get sound through HDMI"
date: 2010-05-20
forum: Multimedia Software
---

### Post by Alethenorio on 2010-05-20
Hi Guys

I have an HP 8510w laptop and I run ubuntu 10.04 out of an external harddrive.

I have no problem getting video over hdmi using the latest proprietary nvidia drivers however I cannot get sound through the HDMI cable.

I have read around without being able to find a solution.

Running "aplay -l" shows only my intel sound card and also there is no hdmi sound interface in the sound preferences (Only the normal output interface).

I am using the latest proprietary nvidia drivers (Believe it to be 1.95) and the graphics card is a Quadro FX 570.

Does anybody know how I can get sound out to work via the hdmi cable? Any help is appreciated.

Regards
Alethenorio

---

### Post by lidex on 2010-05-20
I don't have any personal experience here but I will try to point you in the right direction.
[http://ubuntuforums.org/showthread.php?t=1466111]("http://ubuntuforums.org/showthread.php?t=1466111")
[http://forum.xbmc.org/showthread.php?t=59877]("http://forum.xbmc.org/showthread.php?t=59877")
[http://alsa.opensrc.org/DigitalOut]("http://alsa.opensrc.org/DigitalOut")
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240")

---

### Post by Alethenorio on 2010-05-21
Thanks for the links.

I have updated Alsa to the latest version as most threads seem to suggest however still no luck.

I get no other device interface than analog.

I found a thread with people with the same issue. We are able to do some changes to get a digital interface to appear however no sound comes through HDMI and also on the analo output Ubuntu thinks headphones are on at all times so no sound through speakers (But headphones work).

The Thread in question can be seen here.

[http://ubuntuforums.org/showthread.php?t=1347301&highlight=Alethenorio](http://ubuntuforums.org/showthread.php?t=1347301&highlight=Alethenorio)

Any other ideas?

Regards
Alethenorio

---

### Post by lidex on 2010-05-21
You may want to try the 185 series nvidia drivers. I've seen it mentioned a few times. Don't think the latest has hdmi support.
Also unmute ALL the iec* entries in gnome-alsamixer.

---

