---
title: "Feisty - Multimedia and Extras - First things to do after installation"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by umuro on 2007-05-10
I have a cutting edge kubuntu without any multimedia problems

In a nutshell I have made the following changes to the system.

-  Installed the package, "Ubuntu Restricted Extras"
-  Enabled universe, multiverse and restricted repositories 
-  Added the following extra repositories
  deb [http://www.rastageeks.org/downloads/debian](http://www.rastageeks.org/downloads/debian) binary/
* deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
* deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
## get the keys grom rastageeks and medibuntu sites above!!!
- Fully upgraded the system then
- Installed the graphics driver from NVIDIA.com
- Enabled DVD playback:
```
   sudo apt-get install libdvdnav4 libdvdplay0
   sudo apt-get install libdvdcss2 w32codecs
```

- Installed my webcam following instructions for mine in [http://www.rastageeks.org/](http://www.rastageeks.org/)
- Fixed the [green image problem]("http://ubuntuforums.org/showthread.php?t=126696&highlight=green") for my webcam

- Installed "audacious" for sound stream playback, it's the most compatible one for different radio streams

Now I have a multimedia beast. Apart from seriously developing code on Feisty, now I am
- Listening to my favorite radios using "StreamTuner"
- Seeing the webcam of my girlfriend using "Kopete"
- Watching my DVD using "Kaffeine"

Anything better?

---

### Post by Zacharias on 2007-05-10
libdvdnav4 libdvdplay0 libdvdcss2 w32codecs i have already installed those packages, but still cant watch video even i hear the sounds of videos.

Fiesty and my graphic card is ATI x800

---

### Post by therandman on 2007-05-12
Are you running 64-bit  or 32-fit kubuntu, umuro?

---

### Post by umuro on 2007-05-13
32-bit

---

