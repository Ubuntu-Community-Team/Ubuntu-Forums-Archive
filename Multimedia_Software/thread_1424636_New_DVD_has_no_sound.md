---
title: "New DVD has no sound"
date: 2010-03-08
forum: Multimedia Software
---

### Post by cybrsaylr on 2010-03-08
Just got a new DVD popped it in and video plays fine but there is no sound.
First time this happened. Most CDs and DVDs play fine along with all the other audio players, programs, Youtube and other streaming audio and video play fine. 

Anyone have any suggestions to get sound working on this DVD? Movie Player is the app I tried using that plays video fine but no audio.

PS: I dual boot.
When the DVD is played with Windows 7, sound and video play fine.

---

### Post by cybrsaylr on 2010-03-09
Bump.
Can anyone help?

---

### Post by thundre on 2010-03-09
That DVD probably has multiple audio streams available, and the one that Movie Player is using is not the right one.  There should be a command to cycle through the available streams, check the documentation.  IIRC the # key does this on mplayer.

---

### Post by cybrsaylr on 2010-03-09
OK It must be something in Movie Player where there is no audio.

Just installed VLC player and it plays the DVD audio and video fine with Karmic.

Anyone have any idea how to get audio to work with Movie Player?

---

### Post by cybrsaylr on 2010-03-11
Anyone have any idea how to get audio to work with Movie Player?

---

### Post by cybrsaylr on 2010-03-14
Bump.

Anyone?

---

### Post by Yellow Pasque on 2010-03-14
Chances are you're just missing some gstreamer plugin package:
```
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ffmpeg
```
If the disc still won't work, start Movie Player from the command-line and try the disc:
```
totem
```
Post the output.

---

### Post by cybrsaylr on 2010-03-14
Still won't play sound, just video with Movie player but this DVD plays sound and video fine with VLC.


OK Temüjin, I put in your first code and got this:
> -desktop:~$ sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ffmpeg
[sudo] password for clm: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
E: Couldn't find package gstreamer0.10-plugins-ffmpeg


Then put in totem code in and here's the output:
> -desktop:~$ totem
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Attempting to use device /dev/sr0 mounted on /media/cdrom0 for CSS authentication
*** Zero check failed in ifo_read.c:517
    for vmgi_mat->zero_3 = 0x00000000010000000000000000000000000000
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Attempting to use device /dev/sr0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/clm/.dvdnav/.map'
*** Zero check failed in ifo_read.c:517
    for vmgi_mat->zero_3 = 0x00000000010000000000000000000000000000
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

*** libdvdread: CHECK_VALUE failed in nav_read.c:263 ***
*** for dsi->dsi_gi.zero1 == 0 ***

** Message: no file info

*** libdvdread: CHECK_VALUE failed in nav_read.c:263 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:263 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:263 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:263 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:263 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:263 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:263 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:263 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in nav_read.c:263 ***
*** for dsi->dsi_gi.zero1 == 0 ***


---

### Post by Yellow Pasque on 2010-03-14
Sorry, should have been gstreamer0.10-ffmpeg, but you probably have it already.
Anyway.. as you can see, totem's complaining that it can't find libdvdcss, which you probably have installed already if VLC can play your encrypted disc. This is probably a bug in totem/gstreamer (I've seen similar things on Launchpad).

---

### Post by cybrsaylr on 2010-03-14
Thanks for helping Temüjin.

---

### Post by Yellow Pasque on 2010-03-14
Aye.
If you want, you can try the latest gstreamer stuff: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by cybrsaylr on 2010-03-15
Thanks I'll check it out.

Do you happen to know what code may be needed?

---

