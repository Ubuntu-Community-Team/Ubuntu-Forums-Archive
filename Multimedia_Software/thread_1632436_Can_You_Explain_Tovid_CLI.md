---
title: "Can You Explain Tovid CLI"
date: 2010-11-28
forum: Multimedia Software
---

### Post by derricklongley on 2010-11-28
Okay, I have gone through over 5 to 10 programs and over 10 dvds trying to not use the CLI because I know it is a total different process and I have just started to learn how to use CLI. I have come across several threads mentioning using tovid in the CLI, but lots have outdated code and are written for people not in the noob section. Can someone walk me through how to turn an avi into a dvd and burn it? I believe I have all the dependencies because I went here and followed the instructions [http://tovid.wikia.com/wiki/Tovid_dependencies](http://tovid.wikia.com/wiki/Tovid_dependencies). Thanks to those willing to help.

---

### Post by GregBrannon on 2010-11-28
AVI is a video/multimedia format and DVD is typically used to refer to the format of the storage media.  One can't be turned into the other.

Perhaps if you explain better what you're trying to do - give specifics - and someone will be able to help.  There should be GUI applications available to copy/rip multimedia files and then burn them to DVDs so that you don't have to use the command line, but maybe you're doing something odd that requires it.  One can't tell from the info you've given.

Good luck!

---

### Post by ron999 on 2010-11-28
> **derricklongley said:**
>  Thanks to those willing to help.
Look at your other thread here:- [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1630198]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1630198")

---

### Post by derricklongley on 2010-11-28
I have been trying to follow directions like below, but I have only been able to complete the first instruction. Can someone throughly explain step two because I have seen instructions with more stuff to do listed, but both ways produced this error

 
DVDAuthor::dvdauthor, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>




#1 Convert the file to MPEG-2.
Code:
ffmpeg -i filename.avi -target ntsc-dvd foo.mpg
(Creates a file named foo.mpg)

#2 Build the file structure.
Code:
dvdauthor -o DVD/ -t foo.mpg && dvdauthor -o DVD/ -T
(Creates a folder named DVD)

#3 Make an iso.
Code:
mkisofs -dvd-video -v -o DVD.iso DVD
(Creates a file named DVD.iso)
EDIT
If the mkisofs command doesn't work, use genisoimage instead, like this:-
Code:
genisoimage -dvd-video -v -o DVD.iso DVD

---

