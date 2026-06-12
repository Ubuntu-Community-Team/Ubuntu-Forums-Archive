---
title: "no sound after update"
date: 2010-06-10
forum: Multimedia Software
---

### Post by herato on 2010-06-10
Hi!

Yesterday I updated my ubuntu 8.04, after few months I haven't done it.
Sound stops.

I tried to remove pulse...nothing happened. 
I installed Alsa mixer...nothing happens (when I open alsamixer, it is blank and if I select "Sound card properties" it crashes).

I installed ac97_bus and souncore usinge modconf...still no sound.

What can I do?

My card is nVidia Corporation MCP51 High Definition Audio, pc is a hp pavillon.

Thanks!

---

### Post by lidex on 2010-06-13
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by lewyssmith on 2010-06-14
I have the same problem, silence... so here are *my* stats:--

> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a; aplay -l; dpkg -l | grep "alsa"; head -n 1 /proc/asound/card*/codec#* 
```


```
uname -a
Linux lewis-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                         0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transitional package
rc  libsdl1.2debian-alsa                 1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA options)

head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

```

As for my h/w, the sound system is on-board (Asrock)...
```
lspci
Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
```

This works with another Linux.

TIA            Lewis Smith

---

### Post by lewyssmith on 2010-06-14
Another very similar thread* has pointed me to the [silly] answer, at least for me, perhaps for you?
Find the SOUND PREFERENCES (System-Preferences-Sound) and fiddle the 'Output volume' (which was set to none in my case), possibly also the 'Output' tab 'Connector' type.

I had in fact already searched in vain for this sort of control, and was foxed by finding nothing for sound under System-Administration; and not noticing the Sound entry of the Preferences menu because it is hidden (but scrollable if you realise the need) by a common Ubuntu problem of inadequate screen resolution!

Also, I was misled by the absence of a 'volume' icon in the system tray (or wherever); which I still lack - it does not appear in the list of things to add to the panel.

Thanks to the other thread* & lidex for the clue. Humbled but not guilty.

* "Sound no longer", lidex's 'Alsa Upgrade Sript' notes.

 Lewis Smith

---

### Post by lidex on 2010-06-14
I have three indicator applets in my panel 'add to' dialog. Try adding them one-at-a-time to see which one gets you the volume control. Or maybe it's all three. I honestly can't remember what finally did it for me. Also make sure these packages are installed:
```
sudo apt-get install --reinstall gnome-media gnome-media-common indicator-applet indicator-applet-session indicator-me indicator-session
```

I also have indicator-applet-complete, but that may not be necessary.

---

### Post by lewyssmith on 2010-06-18
Thank you again, lidex, for your 'pointers'. I am writing from another Linux, but will apply your recommendations when I next try Ubuntu (for I am still at the stage of 'trying' it).

Regards      Lewis Smith

---

### Post by lidex on 2010-06-18
> **lewyssmith said:**
> Thank you again, lidex, for your 'pointers'. I am writing from another Linux, but will apply your recommendations when I next try Ubuntu (for I am still at the stage of 'trying' it).


Take the plunge!!

---

