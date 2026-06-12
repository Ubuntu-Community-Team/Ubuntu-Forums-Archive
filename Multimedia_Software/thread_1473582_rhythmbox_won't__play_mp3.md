---
title: "rhythmbox won't  play mp3"
date: 2010-05-05
forum: Multimedia Software
---

### Post by almark on 2010-05-05
After upgrading to lucid lynx rhythmbox won't play mp3 anymore, rhythmbox tries to find some plugins but fails with messages like

The autoaudiosink element is missing.

The requested plugins are:

GStreamer element autoaudiosink

Solutions anyone? 

Regards
Mark

---

### Post by Yellow Pasque on 2010-05-05
Make sure appropriate packages are installed:
```
sudo apt-get install --reinstall gstreamer0.10-plugins-good gstreamer0.10-pulseaudio
```
Log out and log in. If that does not work, manually specify the audio sink:
```
gconftool-2 --type string --set /system/gstreamer/0.10/default/musicaudiosink "pulsesink"
gconftool-2 --type string --set /system/gstreamer/0.10/default/chataudiosink "pulsesink"
gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosink "pulsesink"
```
Log out and log in. Try again.

---

### Post by almark on 2010-05-05
Hey Temüjin, 

That fixed the problem, thanks a lot !

Regards
Mark

---

### Post by HC48 on 2010-05-19
Hello,
I have ripped a CD to mp3 with RipperX and can't get the mp3 files to play at all. I have tried Rythmbox, VLC and Audacious which all play the wav files. I didn't have this problem in Karmic and used Cdex to rip to mp3 before.
I have tried Temûjin's advice but it doesn't work. The files aren't recognized.
Can someone please help.
H :) (beginner)

PS when trying to open the file in Rythmbox it searches for the greffons but can't get the 'Démultiplexeur Etiquette ID3" (I'm working in French) I suppose that is the same in English = **demuxer tag id3**

LATER: 
Checked gstreamer packages and soundconverter needs:
**gstreamer0.10-plugins-ugly-multiverse**
I added the packages and now my mp3 files are working in all my players (rythmbox, VLC, audacity)
In fact the problem seems to be with the mp3 files made in RipperX. I have got all the gstreamer plugins advised etc and have played some mp3 files made with my mp3 player (ZEN).

H :)

I have redone my mp3 files in RipperX and now they work. Yay!

---

### Post by PrimaryMaster on 2010-06-12
Thanks Timuchin (Turkish origin??)... your solution worked for me too :)

---

### Post by dscoggins on 2010-06-21
Thanx for the info worked for me too. Was using Amarok until I tried to listen to music while watching a video lecture in Chrome. Installed Rhythmbox to remedy, or rather address the problem.

---

### Post by Yellow Pasque on 2010-06-21
> **dscoggins said:**
> Thanx for the info worked for me too. Was using Amarok until I tried to listen to music while watching a video lecture in Chrome. Installed Rhythmbox to remedy, or rather address the problem.
Chrome uses ALSA API directly. If you're running a recent Kubuntu and using Pulseaudio, then this fix may help you: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

