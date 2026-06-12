---
title: "Edit avi program"
date: 2007-08-24
forum: Multimedia Production
---

### Post by wormser on 2007-08-24
I am looking for a program to shink an avi video?  Any recommendations for an easy to use program.  The video size is 500mb and I would like to decrease the size of the file to make it better for streaming.

---

### Post by SpiritIsReality on 2007-08-26
howdy
til somebody shows up

not up to much for multimedia yet, but this might help
[http://www.google.ca/search?hl=en&q=intitle%3Alinux+shrink+dvd&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=intitle%3Alinux+shrink+dvd&btnG=Search&meta=)
it looks like k9copy
 or maybe acidrip here
[http://linuxappfinder.com/taxonomy/term/16](http://linuxappfinder.com/taxonomy/term/16)

linux multimedia book here
[http://codeidol.com/unix/](http://codeidol.com/unix/)

and a good google primer
[http://codeidol.com/other/google-hack/](http://codeidol.com/other/google-hack/)

at videolan.org at the forums, found this, but it's for that
other os, but uses gnu tools mencoder and ffmpeg.
[http://www.erightsoft.com/home.html](http://www.erightsoft.com/home.html)
good coder for me, beginner, worth dual booting with 
shared fat32 partition....find the download,bottom of here
[http://www.erightsoft.com/S6Kg1.html](http://www.erightsoft.com/S6Kg1.html)
have to learn mencoder, but till then...

if you try source c, right click for menu, escape key to exit the player.

well looks like I messed up.
this is for streaming, but doesn't look easy
[http://www.google.ca/search?hl=en&q=intitle%3Alinux+avi+stream+shrink&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=intitle%3Alinux+avi+stream+shrink&btnG=Google+Search&meta=)
[http://library.n0i.net/linux-unix/applications/multimedia/transcode/misc.html](http://library.n0i.net/linux-unix/applications/multimedia/transcode/misc.html)

maybe vlc player at videolan.org, vlc package, ubuntu
it does streaming/coding.
[http://www.google.ca/search?hl=en&q=site%3Avideolan.org+avi+stream+shrink&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Avideolan.org+avi+stream+shrink&btnG=Google+Search&meta=)

back to the cactus

trails

---

### Post by chrome307 on 2007-08-26
You could try WinFF - it comes with presets including FLV, AVI, DVD etc

[IMG]http://i18.tinypic.com/4mbtlbk.jpg[/IMG]

Available here and instructions on installation for Ubuntu :

[http://biggmatt.com/winff/](http://biggmatt.com/winff/)

---

### Post by FakeOutdoorsman on 2007-08-26
If you want to edit an avi file, go with Kino, but if you want to encode a video I second chrome307's WinFF recommendation.  It's a GUI for ffmpeg, which is a command-line program.  You will need to get ffmpeg too, but WinFF says:

> A note for Ubuntu users, and other distro's i'm sure: The ffmpeg version from Ubuntu's repository is majorly cut down on codecs and libraries for legal reasons. Therefore a some presets will not work. Namely 3gp, MP3, and others that use MP3 audio codecs. In order to fix this you need to build or get a fully enabled version of ffmpeg.

The easiest way to do this is with Medibuntu.
1. Add Medibuntu repository to your sources.list. [Easy instructions]("http://medibuntu.sos-sts.com/repository.php").
2. sudo aptitude update
3. sudo aptitude install ffmpeg (or install via Synaptic and make sure it is the Medibuntu version).

---

### Post by SpiritIsReality on 2007-08-27
howdy

thanks for the info, pards

trails

---

