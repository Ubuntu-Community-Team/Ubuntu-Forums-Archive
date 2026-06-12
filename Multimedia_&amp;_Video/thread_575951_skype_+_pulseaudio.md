---
title: "skype + pulseaudio"
date: 2007-10-14
forum: Multimedia &amp; Video
---

### Post by demiurgicdaemon on 2007-10-14
I am loving pulseaudio, but I have tried all the guides and everything that I can think of, but I cannot get it to work with skype.  I am having no other problems with pulseaudio except for skype.
When I start skype in terminal with or without padsp , I get the following two errors repeated, I assume, everytime skype tries to access the sound:
> ALSA lib control.c:875: (snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so
> ALSA lib pcm.c:2106: (snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so


The errors occur many times with different frequencies after starting skype.  When I look at the available devices in skype's options, pulse is listed, but no matter what device I select, I seem to get the same issue.
My skype version is :1.4.0.118
My pulseaudio version is: 0.9.5

I am running Feisty, but with kernel 2.6.22-9.  I have two audio devices: onboard HDA-intel and USB Plantronics DSP-500.  I would appreciate any help given.  Thanks.

---

### Post by Scunizi on 2007-10-15
Have you tried the Skype Linux forum?

---

### Post by kluut on 2008-01-22
I tried a lot of guides to have skype (2.0) working with pulseaudio under gutsy. The thing that finally worked for me was to start skype with pasuspender. So basically, when you start skype it temporarily suspends pulseaudio, and lets skype have direct access to the soundcard.

pasuspender is part of pulseaudio-utils, but only as of version 9.7. The version that comes with gutsy is 9.6. So I installed the backport by adding

deb [http://ppa.launchpad.net/ubuntu-backports-testers/ubuntu](http://ppa.launchpad.net/ubuntu-backports-testers/ubuntu) gutsy main

to /etc/apt/sources.list, and upgrading all the pulseaudio 9.6 packages that I had installed to version 9.7, including pulseaudio-utils.

Then I installed skype (the feisty version on [http://www.skype.com/intl/en/download/skype/linux/beta/](http://www.skype.com/intl/en/download/skype/linux/beta/) will do). I also had to install some dependencies (libqt4-core and libqt4-gui). Then I could start skype from the command line with

pasuspender skype

Didn't have to change any settings within skype to have audio working.

Hope this helps.

---

### Post by hyperair on 2008-01-23
There's one problem in that solution. Suspending Skype means you cannot hear any sounds from anywhere else while Skype is on, not even if you weren't making a call. I think I might be switching to Ekiga in this aspect. At least you can kill pulseaudio only when you need to make a call. There's even a Perl script somewhere written using DBUS to suspend pulseaudio when a call comes in, or when you make a call. 

Either way I hope this problem is fixed, as it's really annoying.

---

### Post by mkalen on 2008-05-22
> **demiurgicdaemon said:**
> 
When I start skype in terminal with or without padsp , I get the following two errors repeated, I assume, everytime skype tries to access the sound:

> 
ALSA lib control.c:875: (snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so


[QUOTE]
ALSA lib pcm.c:2106: (snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so 



[/QUOTE]

Skype uses ALSA (it can not yet use pulseaudio directly). The missing module to let ALSA play through pulseaudio can be found in the "libasound2-plugins" package.

---

