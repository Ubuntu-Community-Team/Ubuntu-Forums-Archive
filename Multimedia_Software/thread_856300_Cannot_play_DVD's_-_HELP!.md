---
title: "Cannot play DVD's - HELP!"
date: 2008-07-11
forum: Multimedia Software
---

### Post by pbremner on 2008-07-11
I cannot get Totem / KM Player or VLC to play any standard dvd movie. The disk is recognised and placed on the desktop correctly (with name of movie) but when trying to play it an error message is displayed sayng "An error occurred. Could not read from resource". If I play a video file on the HDD, MPEG, AVI etc it plays perfectly every time. Music CD's played from external drive work perfectly.

All the hardware / software used to work correctly until I did a system update to Hardy - All updates loaded. Any ideas would be appreciated. 
Regards; :confused:

---

### Post by m0r9un0v on 2008-07-11
Try "sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-good gsteamer0.10-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-ugly"

---

### Post by Bachstelze on 2008-07-11
> **m0r9un0v said:**
> Try "sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-good gsteamer0.10-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-ugly"

I would assume he has all the codecs since it worked before the upgrade...

@pbremner : in VLC, File > Open disc, note what's in the "Device name" box, and see if you do have such a device. For example, on my system, it says **/dev/hdb**, which is indeed the name of my DVD drive, as I can see for example in the kernel buffer :

```
firas@nobue ~ % dmesg | grep hdb
[    3.285954] hdb: TSSTcorp CDDVDW SH-S202J, ATAPI CD/DVD-ROM drive
```

So basically, make sure VLC is using the right device, which might have changed during the upgrade. Once again, the kernel buffer will tell you what it is :

```
firas@nobue ~ % dmesg | grep -i dvd
[    3.285954] hdb: TSSTcorp CDDVDW SH-S202J, ATAPI CD/DVD-ROM drive

```

---

### Post by silkstone on 2008-07-11
Again you probably have this since it worked before the upgrade, but check that libdvdcss2 is installed.

---

### Post by vierdreieins on 2008-07-14
I'm having the precise same problem, and have tried the suggestions to no success. The disc isn't mounting and isn't showing up on my desktop; I always get the same error message when Totem tries to open it.

---

### Post by BLTicklemonster on 2008-07-14
Enable the medibuntu repositories in sudo gedit /etc/apt/sources.list

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

```
sudo aptitude remove libdvdcss2
```

then

```
sudo aptitude install libdvdcss2
```

Movies will now look totally wrong, and totem still won't be able to open it.

```
sudo aptitude install kaffeine
```

run it by typing 

```
kaffeine 
```

in the terminal

Somewhere in there, I can't remember where, is a place to adjust the hue. Push it all the way to the right.

Hope this helps.

---

### Post by vierdreieins on 2008-07-14
This didn't help. I don't think it's a codec problem or anything like that. It's like it's not recognizing my DVDROM.

---

### Post by vierdreieins on 2008-07-14
When running Kaffeine I get this:

kbuildsycoca running...
Reusing existing ksycoca
 HDIO_GET_DMA failed: Inappropriate ioctl for device

(sorry, don't know how to put it in a code box.)

---

### Post by stofel on 2008-07-14
hi
had the same problem.
smplayer solved it. follow the link, i can only show you the door.....
[http://ubuntuforums.org/showthread.php?t=856854&highlight=play+movie+DVD](http://ubuntuforums.org/showthread.php?t=856854&highlight=play+movie+DVD)

---

### Post by vierdreieins on 2008-07-14
SMplayer got it actually working, but it skips and the image is scrambled.

---

### Post by espressobeanies on 2008-07-14
I got the same problem. Nothing works.

---

### Post by BLTicklemonster on 2008-07-26
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Might help...

---

