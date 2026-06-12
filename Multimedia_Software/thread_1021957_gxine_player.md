---
title: "gxine player"
date: 2008-12-26
forum: Multimedia Software
---

### Post by pshown on 2008-12-26
When I try to open a DVD in gxine player I get the following error:
No input plugin was found.
Maybe the file does not exist or cannot be accessed, or there is an error in the URL.
Anyone know how I can fix this?

---

### Post by mc4man on 2008-12-26
First run in a terminal
```
sudo lshw -C disk
```

find the entry for your dvd drive and ck. the logical names for the drive.
The dvd one will probably show /dev/dvd1, whatever it is take note.

Then open gxine -> file -> configure -> preferences. Under the gui tab choose 'advanced'.

Then click 'media' tab and below that 'dvd'
In the device box click on the folder icon and choose from the list what was shown in lshw and click on it, then click open to set.

Ex. lshw shows this
 > *-cdrom:1
       description: DVD writer
       product: DVD DD DW1640
       vendor: BENQ
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1  [COLOR="Red"]<-[/COLOR]
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: BSMB


In the list click on the dvd1 listing and then 'open'  (remember to click 'save'


Edit : if you want to set gxine as default player then post what your using, 
intrepid -very simple
hardy - takes a min or so

---

