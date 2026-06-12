---
title: "'Failed to mount' dialog on DVD insertion"
date: 2009-05-05
forum: Mythbuntu
---

### Post by funkydan2 on 2009-05-05
Hi,

Since upgrading my MythTV box to jaunty, when I put in a DVD I now get a 'fail to mount' dialog pop up in the middle of the screen. It doesn't stop the frontend of MythTV being used with a remote, but it does mean that I have plug in a mouse in order to click the 'ok' button to dismiss the dialog.

Has anyone else experienced this problem and know how to make it go away?

Daniel

---

### Post by phroman on 2009-05-07
I have this problem too, I get a dialog box pop up when I insert a DVD at the desktop:

```
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: /dev/sr0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/sr0 is already mounted on /media/cdrom
```

If I hit the eject button the the DVD Drive at the desktop I get this:

```
 Failed to eject "/org/freedesktop/Hal/devices/storagemodel/DVD_RW_111D

Given device "org/freesedktop/Hal/devices/storage_model_DVD_RW_DVR_111D" is not a volume or drive.

```

I did see a bug report here: [https://bugs.launchpad.net/mythbuntu/+bug/238296](https://bugs.launchpad.net/mythbuntu/+bug/238296):  It says to add 'ro' to /etc/fstab

```
/dev/scd0 /media/cdrom0 udf,iso9660 ro,user,noauto,exec,utf8 0 0
``` 

I did that, but it resulted in only eliminating the /dev/sr0 is write-protected line from the pop-up dialog box.

I have all of the following sim-linked to /dev/sr0
/dev/cdrom
/dev/cdrw
/dev/dvd
/dev/dvdrw
/media/cdrom
And I did chmod 777 all of them, just to see if it was a permissions problem.  When I insert a DVD in Mythfrontend, and go to Optical Discs > Play DVD, the screen goes blank for a second and it kicks me back out the the menu.  Is there some sort of conflict with all these devices being sim-linked to the same place?

EDIT:  I forgot, after the last install, in MCC, to enable 3rd party software - libdvdcss, I did, restarted and everything works now.  I still get errors upon inserting discs at the desktop, however, in Mythfrontend, dvd playback and ripping are totally fine.

---

### Post by MerceanCoconut on 2009-07-25
I was able to solve this by disabling "Mount removeable drives when hot-plugged" in the "Removeable Drives and Media" settings in Xfce.  Why Xfce thinks inserting a DVD is hot-plugging a drive is beyond me.

---

