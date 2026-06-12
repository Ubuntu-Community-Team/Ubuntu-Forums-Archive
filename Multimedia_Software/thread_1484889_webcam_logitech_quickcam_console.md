---
title: "webcam logitech quickcam console"
date: 2010-05-16
forum: Multimedia Software
---

### Post by rodi1 on 2010-05-16
hi,
i want to create webcampics with connected logitech quickcam with webcam and webcam.conf 
only console

every thing is working fine, webcam takes pics stores them to the www folder and archieves them with date and time stamp to another folder.

but the brightness of the pictures is not correct at every photo taken.

the pics are lightblue in the morning houres and getting better at about 12 o clock and then they are to dark in the evening- 

what should i do to get correct pictire brightness?
webcam.conf settings to brightness did not take effect.

thanks br
rodi

---

### Post by no2498 on 2010-05-16
see if the cam works in cheese webcam booth
you can change settings with cheese

---

### Post by rodi1 on 2010-05-16
hi, thanks for your reply-

there is no gui installed-
its only text based install for amp

the application im using is webcam a ubuntu package

---

### Post by no2498 on 2010-05-17
in/on 910 and up cheese should be installed
look in sound & video

---

### Post by portentum on 2010-05-17
no2498: I don't think you're understanding what he's saying. He has no desktop environment installed, it is a command line only system, so GUI applications are ruled out. (this is my interpretation anyway)

rodi1: There's a package on Debian called [uvcdynctrl]("http://packages.debian.org/squeeze/uvcdynctrl") that should do what you want, assuming it is a UVC webcam. I don't know that there's an Ubuntu binary for it, but you could always try installing the Debian package (sometimes not a good idea, sometimes ok, up to you if you want to risk it - otherwise you can always compile from [source]("http://www.quickcamteam.net/documentation/how-to/how-to-install-the-webcam-tools")).

---

