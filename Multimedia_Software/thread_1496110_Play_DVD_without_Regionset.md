---
title: "Play DVD without Regionset"
date: 2010-05-28
forum: Multimedia Software
---

### Post by rykel on 2010-05-28
Hi,

I am in Asia (Region 6), and I bought a DVD from USA (Region 1) in May 2010.

The copy protection is from Sony.

My DVD Drive has only ONE region change remaining and I have installed libdvdcss2 through libdvdread4/css.sh. I also do NOT have a firmware update for my DVD drive.

NONE of the following players would play the DVD in Ubuntu - Totem-gstreamer, totem-xine, xine-ui, vlc, gxine, GNOME MPlayer, mplayer.

In Windows XP, the error message was simply that the region is wrong.

Is there anything else I can do to play the DVD without using regionset? (as I cannot allow my drive to be stuck in the USA region)

Please help! Thank you.

---

### Post by mc4man on 2010-05-28
None of the players mentioned enforce region coding, so if you were to run this does it show 'Matshita' for dvd drive model? 
```
sudo lshw -C disk
```

If so, then in the past there has been nothing you could do about a region mismatch, recently there is a potential fix, though not without some risk.

If *it isn't a matshita drive* then try opening ~/.dvdcss, find the folder for the disk in question and delete it. (folder name is volume label of disk

---

### Post by rykel on 2010-05-30
mc4man: You are right - it is a Matshita! (I almost felt like vulgarizing the name of the drive right there)

So what is the risky fix I can try? Mine is an old drive, and if it is gonna give me all the mad problems, I am willing to kill it.   :guitar:



>  *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM UJ-831S
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: 1.40
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted


---

### Post by mc4man on 2010-05-30
Unfortunately you are out of luck again.. the drive is not yet supported (too old)

I'll link the page, you can ck. and see if UJ-83x get support. (wouldn't hold  your breath

[http://forum.rpc1.org/viewtopic.php?f=2&t=4624](http://forum.rpc1.org/viewtopic.php?f=2&t=4624)

================================================================

Basically the idea is the firmware is dumped from your drive, a rpc1 patched firmware is created and then you'd flash the drive with the newly created firmware.
(needs to be done in windows, though back in linux because the opensource players and Os don't enforce regions it would then work fine.

---

