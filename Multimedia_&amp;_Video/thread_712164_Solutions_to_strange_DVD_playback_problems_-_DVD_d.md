---
title: "Solutions to strange DVD playback problems - DVD drive region"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by magozoom on 2008-03-01
I was experiencing (what appeared to be random) DVD playback problem, some discs played, some not, in a combination of media players.

After reading several threads describing the same situation and going through
all the suggested steps... reinstalling libdvdcss, switching to VLC media player, switching backend... etc etc I came across the drive region setting possibility. 

DVD drive region setting seems to me a very unlikely candidate and the shell output from totem and vlc etc does not hint at this. It works, however.

This is the error I got when starting totem from shell:

```

libdvdnav: Using dvdnav version 1.1.7 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/magnus/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1608 ***
*** for pgcit->nr_of_pgci_srp < 10000 ***

```

After installing regionset from standard repositories and setting DVD drive to 2 (euro etc..) everything works like a dream. Here the output from "sudo regionset"

```

regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:2
New mask: 0xFFFFFFFD, correct? [y/n]:y
Region code set successfully!

```

So, the problem is not related to libdvdcss or anything, but the region on the DVD drive not being set properly. Seems to me this could be the solution to many of the problems I have been reading about.

---

### Post by GavinZac on 2008-03-09
Bump! I've just come across this solution myself so rather than making a new thread I'll add my own experiences. DVDs wouldn't play/rip so I re-installed all the usual software a few times, to no avail. I googled the error message from VLC and eventually came across "regionset". DVD players will often only play DVDs from their own regions and so sometimes this causes issues.

You can only change regions 4 or 5 times so do this carefully! Some will have the wrong region set, others wont have any set at all. Consult the chart:

  1  North America (USA and Canada)
  2  Europe, Middle East, South Africa and Japan
  3  Southeast Asia, Taiwan, Korea
  4  Latin America, Australia, New Zealand
  5  Former Soviet Union (Russia, Ukraine, etc.), rest of Africa, India
  6  China

then install regionset:
**sudo apt-get install regionset**

then run regionset:
**sudo regionset**

Hit y then Enter to change the region, then enter the region your DVDs are from - but note, don't expect to change this often because, as I said, you only get 4 or 5 changes. Set it to the region you are from!

And in future, fight for your rights to not have to deal with this regionalised ******** from your local DVD or similar format (im looking at you, Blue Ray) player vendors :)

---

