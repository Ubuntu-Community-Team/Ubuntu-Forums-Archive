---
title: "Incredibly Slow CD Ripping"
date: 2013-05-24
forum: Multimedia Software
---

### Post by dschaller on 2013-05-24
I have a Lenovo Thinkpad E420 with Ubuntu 12.04. Ever since it was brand new, I have never been able to rip CDs with it. Discs take 45-90 minutes to rip, if they complete at all. I've tried many different sofware packages. Ripoff seems to work the fastest (30-40 minutes). With some backends you can actually hear the disc constantly spinning up, spinning down, spinning back up every five seconds or so...

The drive seems to work normally otherwise. Playing audio CD works, accessing data, watching DVD, etc.

I have no problem ripping CDs on my desktop system which is also Ubuntu 12.04.

Is there a known issue with Ubuntu and the CD drive in this laptop?

---

### Post by andrew.46 on 2013-05-24
I don't know this drive in particular but perhaps try a few different rippers. Something a little different is *abcde*, worth a try?

---

### Post by dschaller on 2013-05-25
I tried abcde as suggested. I do like it, but the backend uses cdparanoia which gives the same problem as other rippers (disc spins up and spins down repeatedly while it's reading). abcde takes about an hour to rip a disc like the others.

I'm wondering if this is a configuration issue with Ubuntu and this particular hardware. It's as if there's a setting buried somewhere that isn't right.

---

### Post by mc4man on 2013-05-25
Laptop cdrom drives always rip slower then desktop drives but obviously your times seem excessive
Are the cd's in good shape?
Do you get the same slow speeds from a new cd?

You could add a -Z parameter to cdparanoia on new or like new disks to decrease ripping time

Also you may wish to try this with abcde - 
For CDROM= instead of the usual /dev/sr0 or /dev/sr1 try using /dev/disk/by-id/xxxxx

To find run
```
ls -la /dev/disk/by-id
```
Your cdrom device should be listed, use that.

Ex. of doing so  **on my laptop** - 
> ls -la /dev/disk/by-id
total 0
drwxr-xr-x 2 root root 340 May 25 15:41 .
drwxr-xr-x 5 root root 100 May 25 15:41 ..
lrwxrwxrwx 1 root root   9 May 25 15:41 [COLOR="#0000CD"]ata-HL-DT-ST_DVDRW_GSA-S10N_K1M7CBK3205[/COLOR] -> ../../sr0
lrwxrwxrwx 1 root root   9 May 25 15:41 ata-ST9160823ASG_5NK0LY2C -> ../../sda


So in ~/.abcde.conf
> CDROM=/dev/disk/by-id/ata-HL-DT-ST_DVDRW_GSA-S10N_K1M7CBK3205


Also - what is your cdrom model?

---

### Post by dschaller on 2013-05-25
Thanks mc4man. I was really starting to go crazy. Pointing to the disk by id did not make any difference, but adding the -Z option to cdparanoia made a very noticable improvement. It lowered the rip time for a full disk to about five minutes. Not quite as fast as my desktop machine, but definitely acceptable. I created an .abcde.conf file with this line in it:

> CDPARANOIAOPTS="-Z"

So I assume the software I was getting bad results with before (Sound Juicer, Ripoff, Rhythmbox, etc.) were all using the cdparanoia backend so I was getting the same results with all of them? Also, is there a reason why things work fine on my desktop machine (where I have not disabled paranoia mode) but on the laptop it bogs down to unusable?

By the way, I do not know the model of the CD drive in this machine. It's the stock DVDRW that comes with the Lenovo E420. I can't find an indication of the model number on it.

---

### Post by dschaller on 2013-05-25
According to the Ubuntu disk utility, the drive model is a GT33N. Made by Hitachi, I think.

Hmm. I see too at the Lenovo website that there are some firmware upgrades for it as recently as Oct 2012. Wonder if that would improve the performance. No way to upgrade the firmware that I can see, though, except using Windows -- which I blew out the day I bought the computer!

---

### Post by mc4man on 2013-05-25
> **dschaller said:**
> 
By the way, I do not know the model of the CD drive in this machine. It's the stock DVDRW that comes with the Lenovo E420. I can't find an indication of the model number on it.

What does this show under the  *-cdrom section
(version line is the firmware version


```
sudo lshw -C disk
```
 
Edit  - I see we were posting at same time, does lshw provide anything new?

---

### Post by andrew.46 on 2013-05-26
It might be interesting to see if cdda2wav (without the paranoia options) was any faster or slower than *cdparanoia -Z *. Both work with abcde.  This does not do anything about your problem drive but it might be interesting nevertheless...

---

### Post by Yellow Pasque on 2013-05-26
> **dschaller said:**
> No way to upgrade the firmware that I can see, though, except using Windows -- which I blew out the day I bought the computer!

Bad idea. Even if you hate Windows, you should keep it around (unless you're desperate for disk space) for situations like that. It can also be handy to have Windows if you want to test hardware in another OS and/or need to send the laptop for repair.

---

