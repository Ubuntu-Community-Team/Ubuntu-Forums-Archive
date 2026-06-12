---
title: "DVD drive thrashes on DVD movies but not CDs or unprotected DVDs"
date: 2007-07-08
forum: Multimedia &amp; Video
---

### Post by damonkohler on 2007-07-08
My DVD drive:

> 
$ wodim --devicesBeginning native device scan. This may take a while if devices are busy...
wodim: Overview of accessible drives (1 found) :
----------------------------------------------------------------------
0    dev='/dev/hdc'   rwrw-- :  'LITE-ON'  'DVDRW SOHW-832S'
----------------------------------------------------------------------


The drive won't mount or play DVD movies. It does however, play an exercise DVD just fine. I'm assuming the movie is protected and the other DVD is not? Also, it will mount CDs fine. When I put a movie in the drive, it just thrashes for awhile and then gives up. Here's what I've done so far to try and set up for playing DVDs:

First, I installed all the various gstreamer codecs: bad, ugly, etc. Then I ran the install-css.sh script I found in /usr/share/doc/libdvdread3. I didn't have to install libdvdcss2 explicitly. I think it must have come with some other package. Maybe dvd::rip? Then I noticed the thrashing problem, upgraded the firmware, and checked my region code:

> 
$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:n


I believe 1 is the correct region.

Then I followed the DVD directions here: [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

I've installed libdvdcss2 and w32codecs (which shouldn't be required I assume) from Medibuntu.

Still, movies don't mount, much less play. I think that, since the drive plays the exercise video and CDs just fine, this isn't a hardware issue.

Help?

---

### Post by damonkohler on 2007-07-18
I bought a new DVD drive, set the region code, and now everything works fine. I guess it was a hardware problem.

---

### Post by Gremlinzzz on 2007-07-18
I play dvd movies store bought with smplayer.works good. 
[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)
im using smplayer package (Qt3; without KDE support)
 if dont work and you want to remove
sudo apt-get autoremove smplayer
:guitar:

---

