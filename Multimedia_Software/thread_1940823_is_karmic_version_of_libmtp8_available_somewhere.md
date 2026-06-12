---
title: "is karmic version of libmtp8 available somewhere?"
date: 2012-03-14
forum: Multimedia Software
---

### Post by gopher38 on 2012-03-14
Here's why I ask.  I've got a Creative Vision M that I'm using with Lucid.  Thing works reasonably well for music (not video) with Rhythmbox and Banshee, but gives a segmentation fault (for everything) with Amarok and Gnomad2.  Problem seems to be caused by post Karmic implementation of libmtp8 (mentioned in another thread which I can't seem to find right now).

OK, so Banshee is fine for me for music.  However, I want to transfer some video files too.  Found two possible fixes mentioned on other threads:

1) CL: Command lines calls for mtp-tools seem to work, but I can find NOOOOO documentation anywhere.  This is the only call I've found.

mtp-connect --sendfile /home/guest/Desktop/video* Video

Which works, but I want to create/delete some folders and -after much experimentation - I still can't get it to work.  The man page (which is almost nothing) says to use -h for syntax, but it doesn't work.

2) Downgrade libmtp: That's what this page suggests. 

[http://ubuntuforums.org/showthread.php?p=9666027]("http://ubuntuforums.org/showthread.php?p=9666027")

 That will apparently get everything working, but it says to use karmic libmtp8, which is no longer available.  Couldn't find this in hardy either.  Anyone know where I can find this?  (Or alternatively, find any documentation on CL mtp-tools?)

Thanks.

---

### Post by wolfen69 on 2012-03-14
Here is [libmtp8_0.3.0-1ubuntu3.deb]("http://launchpadlibrarian.net/21051905/libmtp8_0.3.0-1ubuntu3_i386.deb") and here is [libmtp8_0.3.7-3ubuntu2_i386.deb]("http://launchpadlibrarian.net/33660034/libmtp8_0.3.7-3ubuntu2_i386.deb")
Not sure which one you need. Of course I'm assuming you need the 32bit files. The files were found [here.]("https://launchpad.net/ubuntu/karmic/+package/libmtp8")

---

