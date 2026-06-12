---
title: "mic"
date: 2010-05-18
forum: Multimedia Software
---

### Post by kartabosh on 2010-05-18
hey
does anyone know how to activate the microphone on a eeepc 1000h?
on the big pc i have the mic in the gnome-alsamixer and i just take the mute off but in here i dont have mic in alsamixer
i can record in the sound recorder but i want to hear myself live

---

### Post by kartabosh on 2010-05-18
heeelp

---

### Post by lidex on 2010-05-20
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Also helpful is the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by kartabosh on 2010-05-20
alexander@laptop:~$ uname -a
Linux laptop 2.6.33-020633-generic #020633 SMP Thu Feb 25 10:59:18 UTC 2010 i686 GNU/Linux
alexander@laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
alexander@laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
alexander@laptop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC269

---

### Post by lidex on 2010-05-20
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by kartabosh on 2010-05-21
that didn't work...
the only control i have on volume is microphone boost, no simple microphone...

---

### Post by lidex on 2010-05-21
Try gnome-alsamixer. 
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
Use 'Edit -> Sound Card Properties' menu to enable elements.
Soundcard tab to select / adjust levels.

No help? Upgrade your alsa install via the alsa-upgrade link in my sig.

---

### Post by kartabosh on 2010-05-23
i know about alsamixer and i've been there, could it be that netbooks dont allow the soundcard to unmute the mic? sound works fine its just that there is no mic control, should the alsa upgrade magically bring a mic control?

[http://img690.imageshack.us/img690/5161/screenshotli.png](http://img690.imageshack.us/img690/5161/screenshotli.png)

---

### Post by lidex on 2010-05-23
Did you upgrade to 1.0.23 alsa?

---

### Post by kartabosh on 2010-05-24
my kernel Linux laptop 2.6.33 does not appear in the supported kernel list should i try anyway?

---

### Post by lidex on 2010-05-24
Hmm. See if you can install backports. 
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot

---

### Post by kartabosh on 2010-05-24
tried it, nothing changed

---

