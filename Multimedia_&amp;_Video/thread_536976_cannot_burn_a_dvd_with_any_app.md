---
title: "cannot burn a dvd with any app"
date: 2007-08-28
forum: Multimedia &amp; Video
---

### Post by strungoutfan78 on 2007-08-28
ok so i know that this subjet has been beaten to death in these forums but i can't seem to find a solution.  everytime i try to burn a dvd i get this error: ```
Looking for usable media...
expr: syntax error
(standard_in) 1: parse error
Found  no disc. Please insert a usable DVD into /dev/dvdrw.
Trying again in  1 seconds...
Looking for usable media...
=========================================================
Found blank DVD+R.
Using disk label "AMERICAN_PSYCHO"
=========================================================
Burning with growisofs 7.0.1 using the following command:
growisofs -use-the-force-luke=dao -dvd-compat  -Z /dev/dvdrw -dvd-video -V "AMERICAN_PSYCHO" "/home/neil/american psycho"
=========================================================
Executing 'genisoimage -dvd-video -V AMERICAN_PSYCHO /home/neil/american psycho | builtin_dd of=/dev/dvdrw obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
Unknown file type (unallocated) /home/neil/american psycho/.. - ignoring and continuing.
  0.76% done, estimate finish Mon Aug 27 11:38:26 2007
  1.53% done, estimate finish Mon Aug 27 11:39:31 2007
  2.29% done, estimate finish Mon Aug 27 11:39:53 2007
/dev/dvdrw: "Current Write Speed" is 2.5x1352KBps.
:-[ WRITE@LBA=5f0h failed with SK=4h/ASC=03h/ACQ=00h]: Input/output error
:-( write failed: Input/output error
/dev/dvdrw: flushing cache
/dev/dvdrw: closing track
/dev/dvdrw: closing disc
:-[ CLOSE DISC failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type

```

i have tried enabling dma and get this response: ```
neil@craphole:~$ sudo hdparm -d1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device


```

could someone please help.  as of now i have to use my linux box to convert video and when it's ready to burn send it across the network to my windows box to burn it.  frustrating.. :mad:

thanks.

---

### Post by yabbies on 2007-08-28
what did you use to rip the dvd? 
are you trying to burn an iso?

---

### Post by strungoutfan78 on 2007-08-29
the video is one which i downloaded in avi format, converted to mpeg with kino, then used dvdauthor to create file structure.  ive tried using makexml and burning from the resulting xml file.  ive tried converting the vob files into an iso.

i receive this error after trying to burn an iso, a text file, anything.  ive even tried chanaging ownership of my dvd drive and i chown'd /usr/bin/growisofs as well as /usr/bin/genisoimage.  nothing.:confused:

kino reports that it doesnt have access to /dev/raw1394.  this is probably coincidence as i dont see how the two tie together but maybe a clue?

---

### Post by yabbies on 2007-08-29
I know this is silly, and in no way am I trying to insult your intelligence. Does your dvd writer support DVD+Rs? I just don't get while it would come up as "Wrong medium type"

This has me thoroughly perplexed. Are you able to burn CD's?

---

### Post by strungoutfan78 on 2007-08-29
yes my writer supports DVD+R, DVD-R, DVD+/-RW, DL....  and so on.  i have not yet tried to burn a cd as i am fresh out of blanks at the moment,  but the last time i tried to burn a cd or dvd for that matter it was successful.  mind you this was before i reinstalled my OS.  i really don't get it.  i can't count how many times i have started from scratch, yet still everytime i reinstall (USING THE SAME EXACT MEDIA!) i get different hardware/software issues.  this inconsistency boggles me.

---

