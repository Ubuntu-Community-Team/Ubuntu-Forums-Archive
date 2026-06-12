---
title: "Cant turn off speakers when headphones plugged in"
date: 2010-09-01
forum: Multimedia Software
---

### Post by vonpatrick on 2010-09-01
I'm sure this has probably come up before, but I could't find an already existing thread. I have ubuntu 10.04 and when I plug my headphones into the headphone jack, they come on, but the speakers don't shut off. How do I fix this? I have already downloaded and installed the latest Alsa drivers. And I still can't figure it out.

---

### Post by lidex on 2010-09-03
There are more than a few threads regarding this issue. It's also addressed in the forum sticky, I believe. However...
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by martaluisapais on 2010-11-15
I plug in the earphones and the speakers stay on. I uploaded the data here : [http://www.alsa-project.org/db/?f=1985716802aa1dd8c59232120ac7366c0282b238](http://www.alsa-project.org/db/?f=1985716802aa1dd8c59232120ac7366c0282b238)

---

### Post by lidex on 2010-11-15
> **martaluisapais said:**
> I plug in the earphones and the speakers stay on. I uploaded the data here : [http://www.alsa-project.org/db/?f=1985716802aa1dd8c59232120ac7366c0282b238](http://www.alsa-project.org/db/?f=1985716802aa1dd8c59232120ac7366c0282b238)


Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
options snd-hda-intel model=hp-dv5 enable_msi=1
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

Go here if that doesn't work:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio)

---

