---
title: "Looking for information on ubuntu's audio framework"
date: 2010-07-05
forum: Multimedia Software
---

### Post by reakin on 2010-07-05
Hi,

I am looking for more information on the current framework used in Ubuntu (I am on 10.04, but also thinking about what will be used in future releases) so that I can properly debug and setup some applications.  I think it is pulseaudio, but can't find a way to check this.  Qjackctrl and Audacity are both telling me they are running on ALSA drivers, but I thought Ubuntu moved away from this a while ago.

While most things are working quite smoothly, I occasionally see an error message like 'cannot load module alsa', or 'audio device is in use'.  Then, after some more closings and openings, tarting and stopping, it works again.  I would really like to know where to look to find out why the audio device is jammed at these times, and how to unjam it.

Lastly, I see the Sound Preferences dialog in System/Preferences has been revamped.  You no longer get to choose what your audio backend is, and there is an awesome pane that shows which applications are currently running sound.  The one thing is, not all apps seem to be using the correct framework in order to be shown in this pane.

If you know more info on the audio framework in Ubuntu, please share!

Best,
Rich

---

### Post by lidex on 2010-07-06
Alsa is still in use in ubuntu. Pulseaudio is a sound server that sits on top of it and allows multiple clients to access the sound system simultaneously. This app may help (from Alt+F2 Run Dialog):
```
/usr/bin/gstreamer-properties
```
If that doesn't run, make sure these are installed:
```
sudo apt-get install gnome-media gnome-media-common
```

Some apps, such as vlc and mplayer, allow you to select the audio output via preferences. In those you'll want to select pulse.

Pulse info:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")
[http://pulseaudio.org/wiki/PerfectSetup]("http://pulseaudio.org/wiki/PerfectSetup")

Alsa:
[http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page")
[http://alsa.opensrc.org/index.php/Main_Page]("http://alsa.opensrc.org/index.php/Main_Page")

---

