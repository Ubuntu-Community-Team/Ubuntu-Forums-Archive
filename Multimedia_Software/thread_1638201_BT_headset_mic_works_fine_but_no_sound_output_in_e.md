---
title: "BT headset: mic works fine but no sound output in earphones"
date: 2010-12-05
forum: Multimedia Software
---

### Post by silviot on 2010-12-05
Hi all,

I have a Nokia BH-106 bluetooth headset.
The mic is working, but I can't get sound output working for the earphone.
On another pc it works fine.
I'm on a vanilla Ubuntu Maverick.
What logs/etc should I attach to this request for help?
Thanks for your help,

              Silvio

---

### Post by lidex on 2010-12-05
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by silviot on 2010-12-06
Here it is: [http://www.alsa-project.org/db/?f=8e9c924d1a9ae9059acfa8f6fffa373d31b9203c](http://www.alsa-project.org/db/?f=8e9c924d1a9ae9059acfa8f6fffa373d31b9203c)

---

### Post by lidex on 2010-12-06
> **silviot said:**
> Here it is: [http://www.alsa-project.org/db/?f=8e9c924d1a9ae9059acfa8f6fffa373d31b9203c](http://www.alsa-project.org/db/?f=8e9c924d1a9ae9059acfa8f6fffa373d31b9203c)

OK then. Let's try this.
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
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

### Post by silviot on 2010-12-07
Done, with no luck.
BTW in alsamixer I couldn't see any changes (available volumes, available devices) after adding model=auto to alsa-base.conf.
I also don't see any difference if the headset is on/paired or off.

             Silvio

---

