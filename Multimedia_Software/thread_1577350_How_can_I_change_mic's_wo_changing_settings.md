---
title: "How can I change mic's w/o changing settings?"
date: 2010-09-18
forum: Multimedia Software
---

### Post by Denny Johnson on 2010-09-18
On a Dell 14n, 10.04.
Mic problem:
To use the mic jack/external mic, I need to have MIC 3 selected at SYSTEM/PREFERENCES/SOUND/INPUT
To use the built in mic, I need to have MIC 1 selected

How can I get these mic's to work w/o having to change the settings each time I want to switch mic's............so that if the mic jack is plugged in, then the external mic works...........and if the mic jack is unplugged, then the built in mic works.

Thanks

---

### Post by lidex on 2010-09-19
That is a good question. Can you post the output of these commands please:
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

### Post by Denny Johnson on 2010-09-19
Thanks lidex..........it's a Dell laptop, Inspiron 1420, came w Ubuntu installed, 7.04 IIRC.
10.04 now, almost problem free.

```
denjohn@denjohn-laptop:~$ uname -a
Linux denjohn-laptop 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux
denjohn@denjohn-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
denjohn@denjohn-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                                 1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                           0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                        0.10.28-1                                       GStreamer plugin for ALSA
denjohn@denjohn-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9228

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06
denjohn@denjohn-laptop:~$ 

```

---

### Post by lidex on 2010-09-21
Try some model options in alsa-base.conf
Only use one at a time and reboot to initialize.
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=ref 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Two other models to try are:
```
dell-bios
auto
```

---

### Post by Denny Johnson on 2010-09-22
Thanks lidex
I inserted the 'options snd-hda-intel model=ref' line at the bottom, saved, closed, and rebooted.

I have now lost the internal mic, tried all 6 of the SOUND/INPUT/Connector settings.
Have the headphone mic w 2 of the 6 settings: MIC1/MIC and MIC1/LINE IN

You said "Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab."
The HARDWARE tab is attached, but I dont know how to adjust my profile.

"On the output tab choose the correct device."
OUTPUT tab attached, doesn't seem that I have a choice of devices.

The new INPUT window and ALSA f3 and f4 sre also attached...........in case that helps you see the problem.

---

### Post by Denny Johnson on 2010-09-24
Also lost the internal speaker w that change.

---

### Post by lidex on 2010-09-24
Try the other two models.

---

### Post by Denny Johnson on 2010-09-25
Thanks lidex,
Not sure, but I assume I should only insert one at a time the 3 models into  'gksudo gedit /etc/modprobe.d/alsa-base.conf'

I removed       'options snd-hda-intel model=ref'      and tried the other 2 models.
They both worked the same as before I inserted any of the 3 models, that is internal and external speakers work as they should, but I have to go to SOUND and change mic setting when I want to switch between int and ext mics.

Not that big a deal, thought if there was a routine fix for this, good. 
I can live w changing the settings when needed.

Thanks for the effort.
Best wishes
Denny

---

### Post by lidex on 2010-09-25
Routine? Depends on the hardware and what you consider that to be.
You might try upgrading alsa to v. 1.0.23 via the link in my sig. Either alone or in combination with the aforementioned tweaks to alsa-base.

If the upgrade does work then you should be good to go when Maverick releases as it come stock with 1.0.23

---

### Post by fbiagi on 2011-02-16
I have exactly the same laptop, Dell Inspiron 1420 originally with Ubuntu 7.10. 
Now it has a fresh kubuntu 10.04 and i have exactly the same problem.

I change several times the model in the alsa-base.conf (an then used alsa force-reload) with no luck.

Also I couldn't get to work the headphone's microphone that has with only one 3.5 jack (headphones work ok). This ones worked with the 7.10 and 8.04 kubuntu.

system information:
```
$ uname -a
Linux fb-sat 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686 GNU/Linux

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  libsdl1.2debian-alsa                           1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and ALSA 
ii  linux-backports-modules-alsa-2.6.32-28-generic 2.6.32-28.27                                    Ubuntu supplied Linux modules for version 2.
ii  linux-backports-modules-alsa-lucid-generic     2.6.32.28.32                                    Backported drivers for alsa-driver snapshot.

$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9228

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06
```

also:
```
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jan 20 2011 for kernel 2.6.32-28-generic (SMP).
```

please, if somebody know how to solve this or if somebody has the original alsa-base.conf that came from the factory default installation it would be very much appreciated.

---

