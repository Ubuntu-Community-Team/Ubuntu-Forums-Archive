---
title: "Can one use the dd command without a mounted DVD"
date: 2011-01-05
forum: Multimedia Software
---

### Post by GutsyGibbonMarc on 2011-01-05
Hi--

I have a DVD with an important video on it.  Not sure the problem but the DVD is unmountable in Windows and in Ubuntu. The DVD clearly works on the source burner (GoVideo) but does not play anywhere else. I just want to retrieve the VOB or video files from it. 

After an hour of research it seems that the dd command and any other command only works on mounted drives (/dev/cdrom0 or dev/DVD, etc).  When I do a mount command with a regular disk I see the mount as /dev/scd0 /dev/cdrom0.  But when I put in the problem DVD, Ubuntu does not mount it. 

Is there a way to do a block by block copy w/o mounting. Is there a way to force a mount?

Thanks,

---

### Post by mc4man on 2011-01-05
dd should be able to copy from an unmounted disc using the /dev/srX where X is the device (typically 0 or 1
ex. this is currently copying an unmounted dvd video
dd if=/dev/sr0 of=1.iso
(though if there are read errors dd will fail ( adding  conv=noerror can help there

dvdisaster will also read from an unmounted disk (at least here) and will not fail on read errors and can be re-run multiple times increasing the read tries to try to recover if needed

Edit: 
ex. of dvdisaster
disc (filesystem) not mounted
>  sudo lshw -C disk
  *-cdrom:0               
       description: DVD writer
       product: DVDR   PX-712A
       vendor: PLEXTOR
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.09
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=ready

see screen

---

### Post by GutsyGibbonMarc on 2011-01-05
When I do a cat /etc/fstab I see the device as /dev/scd0 however when I run the dd command, it says "No medium found".  Leading me to believe that the dd command expects it to be mounted. 

Thank you for your help,

MH

---

### Post by GutsyGibbonMarc on 2011-01-05
Actually the error message is:

"dd: opening /dev/scd0: No medium found"

---

### Post by mc4man on 2011-01-05
run (with disc in drive
sudo lshw -C disk

If it reports status=nodisc then you are out of luck
If it shows, as above, status=ready then you should be able to copy, whether the filesystem on the disc is mounted or not is not relevant

---

### Post by GutsyGibbonMarc on 2011-01-05
It reports as status = open.  (Not "ready"). 

capabilities : removable audio cd-r cd-rw dvd
configuration: ansiversion5 status = open

Appreciate the help!

MH

---

### Post by mc4man on 2011-01-05
status = open is the same status=nodisc, so there's not much to be done (can't copy from 'nothing'
If you can somehow, sometime get the media recognized then you can copy, mounted or not

---

