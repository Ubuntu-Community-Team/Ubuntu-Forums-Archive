---
title: "Random Sound Muting"
date: 2008-12-22
forum: Multimedia Software
---

### Post by DreadPirate on 2008-12-22
I'm having a rather unusual problem with sound on my Ubuntu 8.10 AMD x64 system. The issue I am running into is that the sound will frequently mute without any warning or provocation. The volume setting will be normal, but I will get no sound from the system. And once "muted", the only way to get the sound back is to cycle the volume up and down several times using the multimedia keys on my keyboard.

I have already gone through the PulseAudio guide at the top of this forum, and that hasn't helped things at all. This happens in all applications - Firefox listening to pandora, Amarok listening to mp3s, and watching videos in VLC are just a few situations where I have had this happen. It is very annoying, and I would appreciate any assistance in resolving this issue.

---

### Post by linux_tech on 2008-12-22
If you havn't already installed these, they will likely help improve
your sound

```

sudo apt-get install gnome-alsamixer
sudo apt-get install alsa-oss
sudo apt-get install libasound2
sudo apt-get install libasound2-plugins

```
To open volume control type:

```

gnome-volume-control

```
To open gnome-alsamixer type

```

gnome-alsamixer

```
Tune settings to what works best for your hardware

---

### Post by DreadPirate on 2008-12-22
Tried all of that and the same problem is still happening. I've looked at the sound on all of the mixers when this happens, and none of them *look* muted - I simply can't get sound from any program at all.

---

### Post by linux_tech on 2008-12-22
Try
```
sudo /etc/init.d/alsa-utils stop
sudo alsa force-reload
sudo /etc/init.d/alsa-utils start
```

---

### Post by DreadPirate on 2008-12-23
Linux_Tech - Tried that as well, the problem is still occurring.

---

### Post by linux_tech on 2008-12-23
It sounds like a conflict between programs

There is a good way to remove pulse audio here-
[http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/](http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/)

Pulseaudio has conflicts with various programs. Try removing it and test sound again. 

Alternatively you can also remove pulse audio this way
```
sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo rm /etc/X11/Xsession.d/70pulseaudio
```

Go to System > Preferences > Sessions->
deselect Pulseaudio Manager

---

