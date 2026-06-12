---
title: "Distorted Audio from PVR-500 with MythTV"
date: 2007-01-24
forum: Multimedia &amp; Video
---

### Post by jlr4u on 2007-01-24
I have a PVR-500 that worked fine using TV/Cable input to the card.   I wanted to connect a satellite receiver to the composite video line and audio input from either of the tuners.  Under this configuration, the audio came out distorted.  The sound was absolutely terrible.   I could run the audio into the computer line-in and the sound was perfect, but could not figure out how to get this line-in into the encoder.   After researching the web, I found out that a lot of users where having the same problem and the resolution seemed to be to change the IVTV drivers.   Below are the steps I took to fix my problem

This is how to Build a  Newer IVTV Version
```
sudo /etc/init.d/mythtv-backend stop
sudo gedit /etc/apt/sources.list
```
Change this line:
```
deb http://dl.ivtvdriver.org/ubuntu edgy firmware
```
To be this:
```
deb http://dl.ivtvdriver.org/ubuntu edgy all
```
Update your package lists.
```
sudo apt-get update
```
Rebuild Modules
```
sudo rm /usr/src/ivtv*deb 
sudo m-a clean ivtv
sudo m-a update,prepare
sudo m-a a-i ivtv
sudo depmod -a
```
Do a cold boot (remove power from the computer)
Re-boot and look for any updates.


That’s all there is to it.

A special thanks to superm1 for his support!

---

### Post by superm1 on 2007-01-25
Glad this worked! :)
It's been added to the ivtv troubleshooting section on the ivtv howto.

---

