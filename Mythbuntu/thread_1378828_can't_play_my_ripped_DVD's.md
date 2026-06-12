---
title: "can't play my ripped DVD's"
date: 2010-01-11
forum: Mythbuntu
---

### Post by benlyboy on 2010-01-11
Here an odd one for you. 

I just did an update. Now I can no longer watch my ripped videos. when I click on them they try to load then just return me to the page I was on.

I looked at the log for the frontend, and even I can see that it is trying to open the DVD drive not the directory where the file is stored. I even put a DVD in the dive and sure enough when i clicked on a movie (any movie) it would play the DvD in the drive.


Here's the log.

> 2010-01-11 21:58:12.215 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2010-01-11 21:58:13.770 TV: Attempting to change from None to Watching DVD
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: Using dvdnav version svnR1169
libdvdnav: vm: failed to open/read the DVD
2010-01-11 21:58:16.051 Failed to open DVD device at /dev/dvd
2010-01-11 21:58:23.518 TV: Attempting to change from None to Watching DVD
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: Using dvdnav version svnR1169
libdvdnav: vm: failed to open/read the DVD
2010-01-11 21:58:23.541 Failed to open DVD device at /dev/dvd
 

Kinda know whats wrong just not sure how to fix it, or how it happend.

Any ideas ?

---

### Post by jayman8547 on 2010-01-12
Had the same issue after upgrading everything to 9.10.  Make sure you are not using storage groups for your media.  On the backend setup under storage, make sure video DOES NOT point to the location of your DVD's.  On your frontends make sure you are pointing to DVD locations.

---

### Post by benlyboy on 2010-01-12
ok I think maybe my setup is wrong, however I'm not sure.

The ripped DVD's are placed in the video group file ( /var/lib/mythtv/videos)

The frontend's "directories that hold videos" is set to /var/lib/mythtv/videos

Are you saying that I need to create a new directory for the ripped DVD's?

---

### Post by myth1914 on 2010-01-19
There is an option for the type of media (mpeg2, xvid, etc.) within (going by memory here)
Setup-> Setup -> video -> playback? -> media type (I apologize for a potentially bad path as I don't have my box in front of me)  This option specifies the player for each type of media (internal or external player, which is usually mplayer)

There is only one that is checked for using the external player, uncheck that and try again.  Most if not all of my ripped DVDs were some mpeg2 variable and this resolved it on each machine.

---

### Post by myth1914 on 2010-01-19
> **benlyboy said:**
> ok I think maybe my setup is wrong, however I'm not sure.

The ripped DVD's are placed in the video group file ( /var/lib/mythtv/videos)

The frontend's "directories that hold videos" is set to /var/lib/mythtv/videos

Are you saying that I need to create a new directory for the ripped DVD's?

I just realized I may have misunderstood your situation.  If your frontend video path is pointed to /var/lib/mythtv/videos, does that path contain the videos on the local machine or is that a mounted share from the server?

If you update the videos from the mythvideo screen and they do in fact populate but do not play, I would refer to my other post.

If in fact, they clear out, you have a bad path to the files themselves and need to:
1. update the video path
2. check your nfs mount (my auto mounts failed after the upgrade to 9.10 as the network came online after the nfs attempted to mount)

Please post any progress...

---

### Post by l0r3zz on 2011-01-11
Was there any resolution to this? I have the same problem on 10.10
with MythTv .24

---

