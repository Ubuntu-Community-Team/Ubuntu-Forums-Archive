---
title: "Another thread about sound problems..."
date: 2008-10-29
forum: Multimedia Software
---

### Post by Maheriano on 2008-10-29
Help, I followed another thread that posted this tutorial and now I have no sound:

> Remove the obsolete nspluginwrapper package:
Code:

sudo aptitude remove nspluginwrapper

Remove obsolete packages and configuration files:
Code:

sudo aptitude remove libflashsupport

Code:

sudo rm ~/.pulse/* ~/.asoundrc* /etc/asound.conf

Step1:- Procedure to follow

Ensure you have the necessary packages installed
Code:

sudo aptitude install padevchooser libao-pulse libasound2-plugins libsdl1.2debian-pulseaudio

Add PPA to your sources.list - this adds a repository to Synaptic. You can also do this using a GUI method. In the menu got to System>administration>software sources. Click add and cut and paste the two deb lines below one at a time then close. Or, use the command line:
Code:

gksudo gedit /etc/apt/sources.list

Add the following lines to the end,save and exit
Quote:
# PulseAudio Fixes
deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) hardy main
Update your repository lists, then upgrade your system (answer yes to install packages that cannot be validated)
Code:

sudo aptitude update

Code:

sudo aptitude upgrade

Set PulseAudio as the default ALSA device and enable the correct driver for libao applications
Code:

asoundconf set-pulseaudio

Code:

echo “default_driver=pulse” >~/.libao

Now you need to Go to System/Preferences/Sound. Ensure all the “Sound Playback” entries are set to their default setting of “Autodetect”, otherwise you may experience difficulties.

After logging out and back in, everything should work correctly! These packages will install PulseAudio complete with tweaks to reduce stuttering/CPU usage, and Flash 10 (release candidate). Finally, Flash & PulseAudio work correctly without crashes

Before I was able to hear all sound (including Audacious) except for Flash videos in Firefox....that's where the troubleshooting began. It was all working fine via SPDIF out on my motherboard but now after running those commands above I have no sound at all. How do I roll back?

---

### Post by garyedwardjohnston on 2008-10-29
Not sure what you've done and haven't done.

After a clean install, I:

1)  install proprietary drivers
2)  install updates
3)  install ubuntu-restricted-extras

in that order.

Everything works great after that :)

---

### Post by Maheriano on 2008-10-30
I did all those entries from the tutorial I posted, that's it. Any idea how I can undo them or get my sound working again?

---

