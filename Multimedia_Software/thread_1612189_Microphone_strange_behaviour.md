---
title: "Microphone strange behaviour"
date: 2010-11-02
forum: Multimedia Software
---

### Post by SuperGeo on 2010-11-02
Hello,

I'm running Ubuntu Desktop 10.04 on a Acer Aspire laptop.

The problem I have is related to the microphone:

1- The volume is too low

2- Trying to raise the input volume of it on Sound preferences make the recordings in Audacity present a strange Offset from the 0db level, although it does raise the volume a little bit.

3- Trying to raise the volume a little more increase the offset and takes the signal drawing (in audacity) outside the visible part of the track, so there is just a line in the upper side.

[http://img534.imageshack.us/img534/1603/micproblem.png](http://img534.imageshack.us/img534/1603/micproblem.png)
Here is a picture showing the behaviour in Audacity as I slide the volume in the Sound settings from 0% to 100%.

[http://img100.imageshack.us/img100/6238/micsettings.png](http://img100.imageshack.us/img100/6238/micsettings.png)
Sound settings screenshot

This problem keeps me turning to Windows everytime I want to record. :(
Hope you guys can help me.

Thanks.

---

### Post by lidex on 2010-11-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by SuperGeo on 2010-11-03
Here is the link you asked for:

[http://www.alsa-project.org/db/?f=0923068fd9b9686808d816ded82e023cc95baf99](http://www.alsa-project.org/db/?f=0923068fd9b9686808d816ded82e023cc95baf99)

---

### Post by lidex on 2010-11-03
> **SuperGeo said:**
> Here is the link you asked for:

[http://www.alsa-project.org/db/?f=0923068fd9b9686808d816ded82e023cc95baf99](http://www.alsa-project.org/db/?f=0923068fd9b9686808d816ded82e023cc95baf99)

Use the alsa-upgrade link in my sig to get v. 1.0.23

Now this.
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=acer 
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

[Audacity]("http://forum.audacityteam.org/viewtopic.php?p=75044#p75044")

---

