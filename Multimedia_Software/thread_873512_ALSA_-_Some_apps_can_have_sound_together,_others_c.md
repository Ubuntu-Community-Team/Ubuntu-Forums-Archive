---
title: "ALSA - Some apps can have sound together, others cannot?"
date: 2008-07-29
forum: Multimedia Software
---

### Post by Redsandro on 2008-07-29
Hi,

I have this similar problem both on an Ubuntu 8.04 machine with onboard sound using the ALSA mixer, and a Xubuntu 8.04 machine with a cheap sound card running ALSA. I only started to notice this when I tried running apps from my media center.

If I run *rhythmbox*, *gngeo*/*zsnes*/*xbmc* has no sound but I can run as many *vlc* instances as I want and hear sound from the videos.
If I run *gxine*, *vlc* has no sound but *gngeo*/*zsnes*/*xbmc* has.
If I run *xbmc*, nothing else has sound (*gxine* has though), and programs started by the same process (a script) that kills *xbmc* also have no sound. If the same script reloads *xbmc*, it also has no sound anymore.

What is different in these apps? My system sais it's using ALSA. Clearly, multiple sound sources are possible, and I'd like to find out how to start apps in this sound-enabled mode.

You see, some apps can play sound together and others don't, and I do have the ALSA sound system. So I need to figure out if I can override this somehow.

**-update-**

I already have alsa-oss installed, and running *aoss xbmc* does not make the multiple sound sources work.

**-update-**

Don't know why.. I tried *aoss* once and now I can run *gngeo* and *xbmc* at the same time with sound, even without using *aoss*. However, if a script I launch from xbmc kills xbmc and opens for example gngeo, then it has no sound. Even if both commands are prefixed with oass.

:(

---

### Post by markbuntu on 2008-07-29
Some of those apps are using alsa or oss and some are using pulseaudio and that is where the problem lies. 

You can check that with the Pulse Audio Manager. If the app is using pulseaudio it will appear in the devices section as #something and you can adjust the volume by clicking properties to get the device screen. 

If the app does not show up, it is using ALSA directly and so will shut out any pulse app but will share with other alsa/oss apps since you installed the alsa-oss wrapper. If a pulse app is working, it will share with other pulse apps, but not with alsa apps.

You can fix this by following my guide which basically tricks the alsa/oss apps to use pulse and makes pulse use alsa. This works for me and some others who have tried it:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

It is not really so complicated as it looks. It mostly involves making sure you have all the stuff you need and setting it up to work together.

---

### Post by Redsandro on 2008-07-29
Hey thanks for the article! I'll keep a bookmark for reference. But for now, I *just* managed a workaround.

First, I must say I don't think my computer uses pulse. I don't know where to find the Pulse Device Manager or something, but when I type pulseaudio at a terminal,  literally 2 pages of errors pop up.

Second, I think the apps I use all are using alsa. I force older apps to use alsa or choose aoss. I found out my sound card does not support hardware mixing, but alsa supports software mixing. I read alsa is as good (or better) as pulse audio, but not prefered since the author closed the source for some reason. Some apps seem to apply a lock to the sound hardware so others don't have sound. But if such an 'other' app runs *before* the sound-stealing-app, then everything that loads after it has audio. Odd but true.

I've said a lot of 'think' above, but the workaround I made up *does* work for the apps I am using at the moment:

I start with a python script that creates a thread which starts mplayer playback something and then pause it. After this, everything has sound simultaneously. Seriously!

For example, on my media center with xbmc, where I have the same problem when running emulators and stuff, I replaced the autostart of xbmc with this script:

*xbmc-softmix.py*```
# XBMC-starter for older or cheaper soundcards that don't support hardware audiomixing
# Redsandro, 2008-07-29

import os, threading

class KeepAlsaBusy (threading.Thread):
	def run (self):
		os.system('mplayer -ao alsa -input file=[color=darkred]/path/to/[/color]mplayer.cmd /usr/share/xbmc/skin/Project\ Mayhem\ III/sounds/back.wav')

KeepAlsaBusy().start()
os.system('xbmc')

# [Command to kill the thread here] if you want mplayer to quit together with xbmc
# I just don't know how to do that.. yet. So please tell me :)
```

*mplayer.cmd*```
pause

```

---

### Post by Yellow Pasque on 2008-07-29
OSS4 has an awesome virtual mixer and no need for ALSA or PulseAudio... The only minor issue some people have with it is system sounds. Some apps (like Swiftweasel) kill esd upon startup because esd doesn't play nice with ALSA.

---

