---
title: "External speakers do not work."
date: 2010-12-27
forum: Multimedia Software
---

### Post by bhishan on 2010-12-27
I have Windows 7 and Ubuntu 10.10 on my Toshiba laptop. In windows everything is fine but in ubuntu if i plug in external speakers they do not work. Even when the external speakers are plugged in the laptop's internal speakers keep working. I searched for other forums but could not find a solution although many people seem to have this problem.

---

### Post by lidex on 2010-12-29
Could be an easy fix. Need some more info though.
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by bhishan on 2010-12-29
> **lidex said:**
> Could be an easy fix. Need some more info though.
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

[http://www.alsa-project.org/db/?f=b68c296a63cbd287051561c38a3391326022cbdc](http://www.alsa-project.org/db/?f=b68c296a63cbd287051561c38a3391326022cbdc)

---

### Post by lidex on 2010-12-29
Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=thinkpad 
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

### Post by bhishan on 2011-01-02
> **lidex said:**
> Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=thinkpad 
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

Thanks! Worked like a charm.

---

### Post by faust99 on 2013-04-22
Seemed to work for me (fingers crossed).....so far speakers have been functioning non-stop for about 2 hours. Normally they fail after 10-50 minutes.

---

### Post by codemaniac on 2013-04-22
old thread, closed. Please feel free to start a new thread.

---

