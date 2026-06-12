---
title: "Can't adjust sound volume"
date: 2010-07-24
forum: Multimedia Software
---

### Post by zjmichen on 2010-07-24
Ok, so I can't adjust my sound using the tray icon.  The media keys on my Dell laptop don't work, and when I click the icon it just has "Mute All" greyed out and "Sound Preferences..."  When I click the latter I get a message saying "Waiting for sound system to respond."  My sound is working fine, I just can't adjust the volume without using alsamixer in the terminal (which is annoying).

I tried a couple of things, like reinstalling pulseaudio, adding /usr/bin/pulseaudio to the startup applications, adding myself to the pulse and pulse-access groups, all to no avail.

Last night I did move my /home directory to a separate partition, but I don't think that should matter, as everything worked seamlessly.

Any ideas?

---

### Post by zjmichen on 2010-07-25
bump.

---

### Post by lidex on 2010-07-26
Try this to remove old config files. 
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

Now this: Can you post the output of these terminal commands for me please:
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

### Post by zjmichen on 2010-07-26
Those files didn't exist.

```
zack@HAL-2000:~$ uname -a; aplay -l; dpkg -l | grep "alsa"; head -n 1 /proc/asound/card*/codec#*

Linux HAL-2000 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux
**** List of PLAYBACK Hardware Devices ****
Home directory /home/zack not ours.
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                       0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
==> /proc/asound/card0/codec#0 <==
Codec: Conexant ID 2c06

==> /proc/asound/card0/codec#1 <==
Codec: Silicon Image SiI1392 HDMI

==> /proc/asound/card0/codec#2 <==
Codec: SigmaTel STAC9228

```Thanks for the reply.

---

### Post by lidex on 2010-07-26
Interesting. You have 3 codecs. What is the Model number for this Dell laptop?
Alsa seems to be working but pulse choking.

---

### Post by zjmichen on 2010-07-27
Inspiron 1525.

---

### Post by lidex on 2010-07-27
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-m81 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by lidex on 2010-07-27
Try this also. Make sure these are installed:
```
sudo apt-get install --reinstall gnome-media gnome-media-common indicator-applet indicator-applet-session indicator-me indicator-session indicator-sound
```

---

### Post by zjmichen on 2010-07-28
Still nothing.

System -> Preferences -> Sound yields "Waiting for sound system to respond."

Also, I forgot to mention that when the login sound plays at login, it starts again halfway through (so two are playing at once) and stops abruptly.  Idk if that helps.

---

### Post by lidex on 2010-07-30
Remove your old config files.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Reboot**

---

### Post by zjmichen on 2010-07-31
They didn't exist.

---

### Post by lidex on 2010-07-31
Read through this guide courtesy *markbuntu:*
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012](http://ohioloco.ubuntuforums.org/showthread.php?t=843012)

---

### Post by zjmichen on 2010-08-02
meh.  I'm going to reinstall the OS anyway.  Thanks for your help, though.

---

