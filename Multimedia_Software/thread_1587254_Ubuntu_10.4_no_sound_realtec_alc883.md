---
title: "Ubuntu 10.4 no sound realtec alc883"
date: 2010-10-03
forum: Multimedia Software
---

### Post by The2Killers on 2010-10-03
Hello guys,

I'm new to the whole linux os, but since I have it on school, I decided to instal it on my laptop.
everything works, accept I have no sound what so ever.. 

I installed Alsamixer, and nothing is muted. 
If anyone could help me, explaining in simple terms how to solve this (since I'm new)

thanks!
(sorry for my English I'm from Belgium)
greetz

---

### Post by Pablo_F on 2010-10-03
Hi, 

Tell us your laptop model and download and run the alsa-info script. For the latter, use this command:

**wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh**

Select yes, automatically upload the alsa information and tell us the URL so we can see the relevant info about your audio hardware and software configuration.

Cheers! Pablo

---

### Post by The2Killers on 2010-10-03
I'm using a medion laptop.

aplay -l

```
**** Lijst van PLAYBACK hardware-apparaten ****
kaart 0: Intel [HDA Intel], apparaat 0: ALC883 Analog [ALC883 Analog]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: Intel [HDA Intel], apparaat 1: ALC883 Digital [ALC883 Digital]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: Intel [HDA Intel], apparaat 6: Si3054 Modem [Si3054 Modem]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
```

sorry, but can you please explain to me how I update the alsa drivers.. 
I downloaded them, but what do I need to do next?
again sorry I'm totally newby =s

thanks for your reply!

---

### Post by Pablo_F on 2010-10-03
Hi!

By the time being, you don't need to update the alsa drivers. The solution could be much simpler than that but we will try to see if you run the command I suggested, press "y" to the question on uploading the info and give the URL.

Cheers! Pablo

---

### Post by The2Killers on 2010-10-03
hi, thanks again for the reply, this is what i get

```
See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at http://www.alsa-project.org/db/?f=140e82cd212b0303e7518d420ae507cc35e58d23

Please inform the person helping you.
```

---

### Post by The2Killers on 2010-10-04
Sorry for double posting but, can someone pls help me :s don't know what to do...

---

### Post by jfooobet on 2010-10-04
I had the same problem.

What I did was updating the alsa driver. Here is a link to the latest driver with instructions:

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

---

### Post by The2Killers on 2010-10-11
Already deleted all drivers and reinstalled them still nothing :s

---

### Post by The2Killers on 2010-10-14
Can someone pls help :s

---

### Post by The2Killers on 2010-10-30
I still dont have any sound can someone help ......

---

### Post by The2Killers on 2010-12-02
could someone respond almost given up with linux ready to go back to windows :s

---

### Post by The2Killers on 2010-12-05
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10190070](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10190070)

this is my page idk if someone could help me..

---

### Post by lidex on 2010-12-05
Try this to re-install alsa. 
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

Next if that doesn't help do this.Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=medion 
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

### Post by The2Killers on 2010-12-06
> **lidex said:**
> Try this to re-install alsa. 
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
``````
sudo apt-get purge linux-sound-base alsa-base alsa-utils

``````
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

Next if that doesn't help do this.Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert this line at the bottom:
```
 options snd-hda-intel model=medion 
```Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

thank you so much dude srsly thx!!

---

### Post by The2Killers on 2010-12-25
ok speakers work fine but when i try a headphone or other sound device via headphone jack it doesn't work :s can you help..

---

### Post by lidex on 2010-12-29
Try switching the 'Connector' in 'Output' tab of 'Sound Preferences. You may need to tweak some mixer settings as well.
Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by The2Killers on 2011-01-05
> **lidex said:**
> Try switching the 'Connector' in 'Output' tab of 'Sound Preferences. You may need to tweak some mixer settings as well.
Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

ty for your response!

I already had alsamixer installed.
in soun card properies everything already was enables.
But still no sound :s 
sorry for my noobieness :-)
thx for the help
gz

---

### Post by lidex on 2011-01-05
Did you do this:
> Try switching the 'Connector' in 'Output' tab of 'Sound Preferences'.

---

### Post by The2Killers on 2011-01-08
yer it's on headphones..

---

