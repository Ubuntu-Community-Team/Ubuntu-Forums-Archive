---
title: "dvd playback problem, codec related?"
date: 2008-04-16
forum: Multimedia &amp; Video
---

### Post by posey on 2008-04-16
I have an Inspiron 1525 running 7.10 (Dell image). The install is less than a week old and fully updated.

I have a brand new DVD, Sweeney Todd, that plays, but as a jumbled mess and the audio is choppy. [Screenshot]("http://home.earthlink.net/~pureawesome/dvdplayback.png")

I have an older DVD, Invader Zim, that plays just fine.

I'm using VLC to play them; Totem is installed but isn't working. 

Video is Intel GM965/GL960 aka X3100, using the intel driver with no compiz. Changing the video drivers in VLC doesn't make things better or worse.

I have installed: ubuntu-restricted-extras, libdvdcss2, libdvdnav4, libdvdread3, gstreamer-good, gstreamer-bad, gstreamer-ugly
Debian patched: libdvdnav-ifo4, libdvdread-ifo3

I have a Gentoo box that played the Sweeney Todd DVD just fine, no extra effort on my part. It is also fully updated, but has the same versions of the dvd libs as the Ubuntu laptop does. So the DVD works and is playable by linux/VLC.

I'm thinking it has to do with the codecs on the Ubuntu laptop, but why would the Debian/Ubuntu ones be different enough that it doesn't work. 

Help please.

---

### Post by mc4man on 2008-04-16
You may want to install regionset and ck. if a region has been set. If_ not_ set it to your region. Probably you should also go to home directory, find .dvdcss and delete the folder for sweeny todd. (if not obvious delete all the folders inside .dvdcss - they'll be recreated next you play the disk). Then try sweeny with vlc.

edit; you really don't need the patched libdvdread-ifo3 for vlc, more suited for mplayer (i think it's better to manually patch dvdread in mplayer source and build your own .

---

### Post by SnakeHips on 2008-04-16
this guide might sort it out.

[http://ubuntuforums.org/showthread.php?t=661833&highlight=java+runtime](http://ubuntuforums.org/showthread.php?t=661833&highlight=java+runtime)

---

### Post by posey on 2008-04-16
Yay, it works now. Thank you!

I installed regionset, but didn't set it to any region. Since this isn't my laptop I didn't feel comfortable making that decision for the owner without the owner's consent (family).

I also looked inside the home folder, and there were lots of .png files of the title screen of Sweeney Todd, so I deleted those and .dvdcss/Sweeney Todd.

---

### Post by crjackson on 2008-04-16
> **posey said:**
> I have an Inspiron 1525 running 7.10 (Dell image). The install is less than a week old and fully updated.

I have a brand new DVD, Sweeney Todd, that plays, but as a jumbled mess and the audio is choppy. [Screenshot]("http://home.earthlink.net/~pureawesome/dvdplayback.png")

I have an older DVD, Invader Zim, that plays just fine.

I'm using VLC to play them; Totem is installed but isn't working. 

Video is Intel GM965/GL960 aka X3100, using the intel driver with no compiz. Changing the video drivers in VLC doesn't make things better or worse.

I have installed: ubuntu-restricted-extras, libdvdcss2, libdvdnav4, libdvdread3, gstreamer-good, gstreamer-bad, gstreamer-ugly
Debian patched: libdvdnav-ifo4, libdvdread-ifo3

I have a Gentoo box that played the Sweeney Todd DVD just fine, no extra effort on my part. It is also fully updated, but has the same versions of the dvd libs as the Ubuntu laptop does. So the DVD works and is playable by linux/VLC.

I'm thinking it has to do with the codecs on the Ubuntu laptop, but why would the Debian/Ubuntu ones be different enough that it doesn't work. 

Help please.

Here, try this...

Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Gutsy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and paste the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

---

### Post by crjackson on 2008-04-16
OOPS!  I was too slow..

---

