---
title: "No input sound Ubuntu 10.04"
date: 2010-09-04
forum: Multimedia Software
---

### Post by anchorschmidt on 2010-09-04
I'm using a Dell Vostro 1700 with Ubuntu Lucid Lynx and nothing I do with the sound preferences changes anything. I've also tried running alsamixer. no luck. Can anyone help me?

---

### Post by lidex on 2010-09-05
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by anchorschmidt on 2010-09-06
Here is the link [http://www.alsa-project.org/db/?f=8aa8e20eb81a82b236c14e7be1db6860c0adf834](http://www.alsa-project.org/db/?f=8aa8e20eb81a82b236c14e7be1db6860c0adf834)

---

### Post by lidex on 2010-09-06
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel enable_msi=0 model=eapd 
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

### Post by mubtasim123 on 2011-02-08
can you help me with this? sounds similar [http://ubuntuforums.org/showthread.php?p=10441012#post10441012](http://ubuntuforums.org/showthread.php?p=10441012#post10441012)

---

