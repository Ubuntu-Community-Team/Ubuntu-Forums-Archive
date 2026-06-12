---
title: "Audio only through speakers, no headphone"
date: 2010-10-27
forum: Multimedia Software
---

### Post by Jerezano on 2010-10-27
I recently installed Ubuntu alongside my Windows 7 and everything is great except the sound. Whenever 
I play sounds the audio only comes out of my built in speakers and the headphone jack does nothing. I'm using Ubuntu 10.10 on a Toshiba Sattelite L655D-S5066.

works fine in windows 7
[IMG]http://i52.tinypic.com/1zof4fs.png[/IMG]
Help please.

---

### Post by Jerezano on 2010-10-28
bump

---

### Post by alexandari on 2010-10-28
Have you tried tweaking your mixer,check out if you can add some channels and seeing if there are any muted things and stuff

---

### Post by Jerezano on 2010-10-28
> **alexandari said:**
> Have you tried tweaking your mixer,check out if you can add some channels and seeing if there are any muted things and stuff

Yea I checked if anything was muted in the sound prefrences and alsamixer but nothing was muted.

---

### Post by lidex on 2010-10-28
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Jerezano on 2010-10-28
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

Copied it wrong the first time but realized it. Here it is
[http://www.alsa-project.org/db/?f=64eaefd69bb1ae328c13ff609bc152cd5a94ce12](http://www.alsa-project.org/db/?f=64eaefd69bb1ae328c13ff609bc152cd5a94ce12)

---

### Post by lidex on 2010-10-28
> **Jerezano said:**
> Copied it wrong the first time but realized it. Here it is
[http://www.alsa-project.org/db/?f=64eaefd69bb1ae328c13ff609bc152cd5a94ce12](http://www.alsa-project.org/db/?f=64eaefd69bb1ae328c13ff609bc152cd5a94ce12)

Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes
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

---

### Post by Jerezano on 2010-10-28
> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes
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

I followed that but I'm not seeing anything different in alsamixer or in my sound preferences. 

Card is shown as "HDA ATI SB"

---

### Post by Jerezano on 2010-10-31
bump

---

### Post by lidex on 2010-11-02
OK. Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by jwistead on 2011-01-14
> **lidex said:**
> OK. Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

This worked on my HP G61 laptop.

---

### Post by subdural on 2011-01-14
works for me, too on my toshiba satellite c650.  thanks for your help!

---

### Post by lidex on 2011-01-15
Good deal. You're welcome.

---

