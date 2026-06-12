---
title: "DVD And Audio Problems"
date: 2009-08-19
forum: Multimedia Software
---

### Post by bsouk on 2009-08-19
Recently I just installed Ubuntu 9.04 on my laptop, and mostly everything works great except for a few slight issues that are really bothering me...

First of all I can get no audio from online source's, only video. Nor do i get any audio when playing an audio file in say VLC even though it loads and plays the file. I've tried a few things from other threads like fiddling with preferences. But nothing seems to be working. 

Second, I cannot get the system to Play DVD's. It is a DVD Capable drive.
To try and fix this I downloaded 
              [COLOR=Black][libdvdnav4]("apt:libdvdnav4"),              [libdvdread4]("apt:libdvdread4"),              [gstreamer0.10-plugins-bad]("apt:gstreamer0.10-plugins-bad") and [gstreamer0.10-plugins-ugly]("apt:gstreamer0.10-plugins-ugly")[/COLOR] 
as per the instructions from the support site, and the ran the command

sudo /usr/share/doc/libdvdread4/install-css.sh

in terminal. Which then told me that libdvdcss2 was installed.But it still
refuses to detect any DVD. I also downloaded VLC because I heard that might 
play them but this is the message I get when trying to open the disk:

[COLOR=#ff0000]Playback failure:[/COLOR][COLOR=#000000]
DVDRead could not open the disk "/dev/dvd".[/COLOR][COLOR=#ff0000]
Your input can't be opened:[/COLOR][COLOR=#000000]
VLC is unable to open the MRL 'dvd:///dev/dvd'. Check the log for details.

 Whatever the case may be I could really use some help of any kind. Thanks!
[/COLOR]  p, li { white-space: pre-wrap; }

---

### Post by Otto Mobeal on 2009-08-19
bsouk, I have the same problem, so I just tried the things you had in your message - to limited effect.  I can now see the DVD for about 5 seconds, then I get the error: "Internal Data Flow Error".  I have included a screen shot.

Also,
Computer: Gateway MX3560
OS: Ubuntu 9.04
Loaded: 8/18/2009 as an update from Website.

---

### Post by wojox on 2009-08-19
Look @ this link:

[http://ubuntuforums.org/showpost.php?p=7197110&postcount=5](http://ubuntuforums.org/showpost.php?p=7197110&postcount=5)

---

### Post by bsouk on 2009-08-19
Well I went through the command sequence on the link and It is still acting like the drive doesn't even exist... not to sure what to do here.

Oh! But I do now have audio from online video streams! Thanks!

---

