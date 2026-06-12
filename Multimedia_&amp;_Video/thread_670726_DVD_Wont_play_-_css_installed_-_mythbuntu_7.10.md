---
title: "DVD Wont play - css installed - mythbuntu 7.10"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by JRGould on 2008-01-17
So, I've scowered these forums and the rest of the intarwebs but I still can't figure this out.

The gist of my issue is that I can't get DVD movies to play, be it in mythTV or in mplayer. Data DVDs read fine, and non-encrypted dvds seem to play fine (RvB season 1) but DVD movies just don't seem to be recognized. 

I made sure restricted extras were installed
tried ls -s /media/cdrom1 /media/dvd
tried ls -s /dev/hdc /dev/dvd
did this: /usr/share/doc/libdvdread3/install-css.sh
ran reigonset

I've even tried installing regular ubuntu 7.10, all to no avail. 

any further suggestions would be much appreciated

-Jeff

---

### Post by cor2y on 2008-01-17
Visit the medibuntu and get the specific packages for dvd playback from there or add the medibuntu repo.
[www.medibuntu.org](www.medibuntu.org)
Try playback after that and see.

---

### Post by JRGould on 2008-01-17
looks like medibuntu.org is down... I'll keep checking and post back. Thanks.

---

### Post by mdpalow on 2008-01-17
You could try the link in my signature below to help you.

---

### Post by JRGould on 2008-01-18
alright, so I installed all of the medibuntu packages and still, little to no dice. 

myth frontend just goes black for a few secs when I try to play a dvd, gxine says something along th lines of 'No input plugin found. mayb the file does not exist' and then 'Read error from: /dev/dvd' (or /dev/hdc, when I tried to change it, hoping there was something wrong with the symlink)
and MPlayer says 'No stream found to handle url dvd://1' 

could I just have incompatible hardware? it's a stock dvd drive from an old compaq...

---

### Post by Black_Heart on 2008-01-18
i've been having the same problems w/ my system. its also a compaq, so maybe it is the hardware...

---

### Post by oldos2er on 2008-01-18
You need libdvdcss2 to read commercial DVDs.

---

### Post by JRGould on 2008-01-18
> **oldos2er said:**
> You need libdvdcss2 to read commercial DVDs.

I do.

---

### Post by sfalcon1 on 2008-01-23
I had a dvd that would not read in any linux distro.  today i updated my debian  with the new libdvdread3 0.9.7-6 and it started to work.   right now ubuntu is at 0.9.7-3.  you should be able to build it from deb source.  I have not tried yet.

UPDATE: it still will not play the disc but will read the vob files now.

scott

---

