---
title: "Headphone sense &amp; monitor flickering"
date: 2008-03-20
forum: Multimedia &amp; Video
---

### Post by FalseLobster on 2008-03-20
Hello, I'm relatively new to Linux and have been running a dual boot of Windows XP & Ubuntu 7.10 for a little while now.  Overall, I'm very happy with my Ubuntu installation, but I have two issues.

The first, I understand, is fairly common:  there is no headphone jack sense, and sound plays through both my speakers and my headphones when a headphone is plugged in.  I did some research on the Internet and attempted a few solutions to no avail.  I gave up, ignored the problem for a while and am now posting asking what to try(but having forgotten what I already tried).

The second problem I have is that my display frequently flickers to black and back rapidly.  I have no idea how to approach this problem.

Some information:

My computer is a laptop from cyberpowerpc.com,
```
owner@owner-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
Opening the Volume Control, I am presented with one tab Playback and, from left to right, I have Microphone, PCM, and Front.  Playing with these settings, mute/unmute, plug/unplug appears to yield no results.

My graphics card is an NVIDIA 7600 Go, as far a drivers go, all I did after install was enable the proprietary NVIDIA accelerated graphics driver in the Restricted Drivers Manager.

I do not run into the screen flicker issue in Windows XP, but I have run into numerous issues regarding its emulation of Refresh Rate (I can only set my refresh rate to 58 or 59 in Windows, and I suspect that many applications run into issues identify my display as a result).

Under Screen and Graphics Preferences, it defaults to
Model: Custom 1
Resolution: 1680 x 1050 @ 50 Hz.

I cannot change the refresh rate with the model set as Custom 1.


Any guidance regarding either of these issue would be much appreciated.

---

### Post by FalseLobster on 2008-03-21
Is bumping allowed on these forums?  I couldn't find any forum rules before I posted.  This is my second post, btw.

So... anyone got any suggestions?

*bump*

---

