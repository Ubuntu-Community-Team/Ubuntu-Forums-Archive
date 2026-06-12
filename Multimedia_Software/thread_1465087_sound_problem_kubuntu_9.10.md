---
title: "sound problem kubuntu 9.10"
date: 2010-04-29
forum: Multimedia Software
---

### Post by linuxnoob420 on 2010-04-29
hi folk This is my firs time posting in ubuntu forums i been using gnome since hardy now I swiched to kde its been working well in till now    MY sound stopped working i think it was my fault but i dont know how to fix it firefox has perfect sound but nothing else at start up kde tells me   HDA Intel (Context Analog) reverting to pulsesaudio and it don't work ether     Please I really need some help i looked everywhere   p.s. i tried sudo alsa force-reload it worked but not after restarting the computer and i had no volume control in till I logout and back

---

### Post by lidex on 2010-04-29
kubuntu doesn't use pulseaudio from my understanding. Why is it running?

---

### Post by linuxnoob420 on 2010-04-29
well your guess is better that mine maybe thats the problem can i get rid of it if i dont need it and how? like i said im new to kde

---

### Post by lidex on 2010-04-29
Try this:
```
sudo apt-get remove --purge pulseaudio paman pulseaudio-utils paprefs padevchooser pulseaudio-esound-compat pulseaudio-module-gconf pavumeter pulseaudio-module-x11 pavucontrol 
```
```
rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Reboot.

---

### Post by linuxnoob420 on 2010-04-29
i ran that and got this
exp@exphub:~$ sudo apt-get remove --purge pulseaudio paman pulseaudio-utils paprefs padevchooser pulseaudio-esound-compat pulseaudio-module-gconf pavumeter pulseaudio-module-x11 pavucontrol
[sudo] password for exp:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package pulseaudio is not installed, so not removed
Package paman is not installed, so not removed
Package pulseaudio-utils is not installed, so not removed
Package paprefs is not installed, so not removed
Package padevchooser is not installed, so not removed
Package pulseaudio-esound-compat is not installed, so not removed
Package pulseaudio-module-gconf is not installed, so not removed
Package pavumeter is not installed, so not removed
Package pulseaudio-module-x11 is not installed, so not removed
Package pavucontrol is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libdiscid0 mplayer-skins libmusicbrainz3-6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
exp@exphub:~$

---

### Post by lidex on 2010-04-29
OK then. Guess it wasn't installed. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by linuxnoob420 on 2010-04-29
okay sorry i left the computer for a min here it is
exp@exphub:~$ uname -a
Linux exphub 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux
exp@exphub:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
exp@exphub:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.
exp@exphub:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Conexant CX20561 (Hermosa)
exp@exphub:~$

im not sure how to make a code tag sorry

---

### Post by linuxnoob420 on 2010-04-29
Toshiba m-305-s4910 laptop is what i have

---

### Post by lidex on 2010-04-30
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=toshiba  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

---

### Post by linuxnoob420 on 2010-04-30
shoot when I ran nothing happend just a bouncing gear 
gksudo gedit /etc/modprobe.d/alsa-base.conf

---

### Post by Yellow Pasque on 2010-04-30
Instead of gksudo gedit, that could be:
```
kdesudo kwrite ...
```
Or maybe kate instead of kwrite (IDK what Kubuntu uses for a default editor)

---

### Post by linuxnoob420 on 2010-04-30
thank man it was kate

---

### Post by linuxnoob420 on 2010-04-30
shoot it didn't work well i need to thank you guys for the help but im going to get some sleep be back tomorrow but please post any thing useful

---

### Post by lidex on 2010-04-30
> **Temüjin said:**
> Instead of gksudo gedit, that could be:
```
kdesudo kwrite ...
```
Or maybe kate instead of kwrite (IDK what Kubuntu uses for a default editor)

That's what I get for using boilerplate and definitely need to learn kde.

---

### Post by linuxnoob420 on 2010-05-01
hopefully this image can help the error on the top left corner is something else i keep getting

---

### Post by lidex on 2010-05-01
Try upgrading your alsa install. Click the alsa-upgrade-script link in my sig.

---

### Post by linuxnoob420 on 2010-05-04
well i tried that alsa upgrade script sorry i was busy for the past 2 days well any way it didn't work damn it well I guess im back to square 1 just so you guys know im not in a big rush to fix it i just want to get it running now    amarok wont play sound even if i run sudo alsa force-reload now this is as of to day before i ran the alsa script after the script nothing changed at all that i can see yet. could the problem be worsening itself i could get amarok working before

---

### Post by linuxnoob420 on 2010-05-04
okay this is over no i cant list or fix the amount of problems im having now my Internet my video sound is all getting too crazy. i think im just going to reinstall a fresh  start at least then i could track down the cause right now im kinda in a rut i feel like once i fix the sound
another problem will show. I thank you guys for the help. sorry i kinda gave up. any more info will be pretty much useless since by the end of today my system will be new and fresh
and no im not upgrading to 10.04 yet just 9.10 any way I thank you guys for trying   and have a good one

---

