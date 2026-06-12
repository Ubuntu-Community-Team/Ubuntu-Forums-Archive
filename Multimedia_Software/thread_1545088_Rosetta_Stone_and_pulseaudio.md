---
title: "Rosetta Stone and pulseaudio"
date: 2010-08-03
forum: Multimedia Software
---

### Post by nicknefarious on 2010-08-03
My thread is both an information and a discussion/question thread.

First of all the information.

I have long searched for a solution to my desire for Rosetta Stone in Wine but could not get it to recognise my microphone.

Finally today I removed (uninstalled) pulseaudio. It took a few packages with it and I am waiting to see what effect they will have. But finally, by checking the ALSA Driver in the Wine configuration, along with uninstalling pulseaudio, my Rosetta Stone works perfectly. A great deal better than in my XP Virtualbox Virtual Machine. Stoked!!!

For those who are interested I have Wine 1.1.42-0ubuntu4 installed, Rosetta Stone 3.4.5 and am using a Dell XPS M1530 with Ubuntu 10.04 64-bit OS. It's been a long time!!!

My question part relates to the removal of pulseaudio. There have been no obvious negative effects as yet, and from my readings it would seem there shouldn't be, however I am concerned at the other packages it took with it (dependencies). Can anyone give any further advice/info here? I know for sure it took the package ubuntu-desktop which when I try to reinstall it tries to drag pulseaudio and all it's associated packages along with it. Can I/we live without these dependent packages? If not how can I get them back without pulseaudio?

All advice and info and guidance provided is much appreciated.

Big thanks,

Nick

---

### Post by nicknefarious on 2010-09-15
> My question part relates to the removal of pulseaudio. There have been no obvious negative effects as yet, and from my readings it would seem there shouldn't be, however I am concerned at the other packages it took with it (dependencies). Can anyone give any further advice/info here? I know for sure it took the package ubuntu-desktop which when I try to reinstall it tries to drag pulseaudio and all it's associated packages along with it. Can I/we live without these dependent packages? If not how can I get them back without pulseaudio?

All advice and info and guidance provided is much appreciated.

Big thanks,

Nick

I'm going to change this to ANY (ABSOLUTELY ANY) advice would be greatly appreciated.

My question is... is it safe to remove pulseaudio and all of the packages it takes along with it when you uninstall it? Last time I did this it messed with things like the system volume control and caused some random sound problems like not being able to preview audio (mouse over audio files to hear a preview)...

Is there some way to force remove pulseaudio without removing the other packages?

Please help...

Thanks,

Nick

---

### Post by Yellow Pasque on 2010-09-15
ubuntu-desktop is just a metapackage that pulls all of the default packages in an ubuntu install. It is safe to remove ubuntu-desktop.

> Last time I did this it messed with things like the system volume control
Volume control: use [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

> not being able to preview audio (mouse over audio files to hear a preview)...
This feature actually uses rhythmbox to play the files, so you have to be able to play music there before it will work. Check the volume in rhythmbox and also run the following commands to set gstreamer to use ALSA instead of pulseaudio

```
gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosrc alsasrc
gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosink alsasink
gconftool-2 --type string --set /system/gstreamer/0.10/default/chataudiosink alsasink
gconftool-2 --type string --set /system/gstreamer/0.10/default/musicaudiosink alsasink
```

---

