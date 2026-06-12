---
title: "[SOLVED] is it possible to rip a DVD and play it on my netbook?"
date: 2008-12-11
forum: Multimedia Software
---

### Post by shiningkenmonster on 2008-12-11
hey, i just saw the DVD box of the movie Hitch, it is on sale at Target.

the only problem is that i have a netbook with no DVD/CD-ROM drive. and i am kind of new to Ubuntu and i am not sure what programs to use.

i have a dell mini 9 with a dell's version of Ubuntu 8.04.

i was planning to use my friend's window desktop pc and rip the dvd onto my 4 GB usb flash drive.

is there a way for me to view it on my netbook with this?

(i am planning to buy this movie for myself and i am not planning to share file with anyone.)

---

### Post by jerome1232 on 2008-12-11
Yes there are a number of applications which can accomplish this.

dvdbackup and genisoimage are command line utilities that work. For gui utilities Dvd::rip, k9copy, Thoggen Dvd Ripper, AcidRip Dvd ripper work great as well.

Personally I like k9copy, or sometimes dvdbackup/genisoimage, but I simply make iso backups of my dvd's (playable with VLC). If you want the movies actually transcoded the above applications can do that too, it just takes alot longer and is more difficult. All of these applications are available via the repo's.

You will probably need the ability to read encrypted dvd's, [this]("https://help.ubuntu.com/community/Medibuntu") is a guide using medibuntu's repos to get that functionality working.

Feel free to ask question if you have any.
cheers!

---

### Post by blackened on 2008-12-11
> **shiningkenmonster said:**
> ...i was planning to use my friend's window desktop pc and rip the dvd onto my 4 GB usb flash drive...

You have quite a few options, both free and not.

Free - (I've used both of these, spyware free, both work well)

DVD Shrink [http://www.afterdawn.com/software/video_software/dvd_rippers/dvd_shrink.cfm]("http://www.afterdawn.com/software/video_software/dvd_rippers/dvd_shrink.cfm")

DVD Decryptor [http://www.mrbass.org/dvdrip/]("http://www.mrbass.org/dvdrip/")

Pay - (I use this through wine, it's my personal favorite and the most versatile I've found yet)

DVDFab [http://www.dvdfab.com/]("http://www.dvdfab.com/")

You may also need something like SUPER or Total Video Converter to convert (unnecessary with DVDFab) the shrunken files into an appropriate format such as ogg video, mpg, avi, wmv etc.

---

### Post by sabitha on 2008-12-11
You Can use [WinFF]("http://code.google.com/p/winff/")
> WinFF is a GUI for the command line video converter, FFMPEG. 
It will convert most any video file that FFmpeg will convert. 
WinFF does multiple files in multiple formats at one time. 
You can for example convert mpeg's, flv's, and mov's, 
all into avi's all at once. 

WinFF is available for Windows 95, 98 , ME, NT, XP, VISTA, and Debian,
Ubuntu, Redhat based GNU/Linux distributions. 
WinFF is available in Brazillian Portuguese, Bulgarian, Chinese
Tradditional, Danish, English, French, German, Italian, Polish, 
Portuguese, Spanish, and Turkish.

---

### Post by kpkeerthi on 2008-12-11
Also try handbrake

---

