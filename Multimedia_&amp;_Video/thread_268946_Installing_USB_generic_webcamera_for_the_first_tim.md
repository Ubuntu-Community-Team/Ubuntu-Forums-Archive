---
title: "Installing USB generic webcamera for the first time"
date: 2006-09-30
forum: Multimedia &amp; Video
---

### Post by saskboy on 2006-09-30
I'm trying to install a generic CIF USB Camera (2110) [as it shows in Windows]. It didn't come with a Linux driver, and I've never installed a webcamera on Linux before, so please treat me like a beginner.

Does anyone know the best way to go about installing a webcamera on Ubuntu.

I found the following instructions for EasyCam, which I can't do because I don't know how to edit the sources.list file.
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras?highlight=%28webcam%29](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras?highlight=%28webcam%29)
Add the following line to your /etc/apt/sources.list

deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

Then you need to update the packages and install easycam

sudo apt-get update
sudo apt-get install easycam2
+++++++++

Thanks for any suggestions [aside from buying a new camera],
Saskboy
:-k

---

### Post by saskboy on 2006-10-01
Is there a forum that better suits webcamera questions, or installing drivers?

---

### Post by apoth on 2006-10-03
I can't really help much with getting your webcam working - I can't get mine working.

As far as editing your sources.list goes, try putting this in a terminal:

```
sudo nano -w /etc/apt/sources.list
```

The options at the bottom like ^O mean, in this example ctrl-O.

---

### Post by saskboy on 2006-10-22
Thank you for trying to help. I installed EasyCam, and the webcam viewer in the Applications menu doesn't open the webcamera still. I don't see where to edit the configurations, it just opens an error box for /dev/video0 couldn't connect.

---

### Post by saskboy on 2006-11-18
Does anyone have suggestions for installing generic USB webcameras in Linux?

---

