---
title: "Cannot play audio CD from VLC"
date: 2011-02-07
forum: Multimedia Software
---

### Post by carfield on 2011-02-07
It saying that cannot open "cdda:///dev/sr0", how can I check for more information?

---

### Post by mc4man on 2011-02-07
You might want to post what version of vlc and what release of ubuntu.

Meanwhile ck. and see if the drive w/ the audio cd is actually /dev/sr0

```
sudo lshw -C disk
```
look in the *-cdrom: section(s)

---

### Post by carfield on 2011-02-08
Thanks a lot, I am using ubuntu 10.10 and my vlc version is 1.1.4

Here is the output of "sudo lshw -C disk"

  *-cdrom
       description: DVD-RAM writer
       product: iHAS120   6
       vendor: ATAPI
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 7L04
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

And my VLC showing the error:

[0x8790204] cdda access error: could not read TOCHDR
[0x8790204] cdda access error: no audio tracks found
[0xb7000694] main input error: open of `cdda:///dev/scd1' failed: (null)

---

### Post by mc4man on 2011-02-08
You're showing some conflicting info  - in first post
> t saying that cannot open "cdda:///dev/sr0"
Then last post 
> 0xb7000694] main input error: open of `cdda:///dev/scd1' failed: (null) 
Do you have 1 or 2 drives? (assuming 1

When you put an audio cd in that drive does an icon show up on Desktop?

Assuming it does try any of these

put an audio cd in and hold the shift button down till you get a pop up, in the drop down choose vlc

Open vlc > Tools >  Preferences > Input and Codecs, set the optical device to /dev/sr0 and save

From a terminal w/ audio cd in the drive
```
vlc cdda:///dev/sr0
```

---

### Post by carfield on 2011-02-08
Sorry it is /dev/sr0, I just give a try to /dev/sr1 and it show same error 

Thanks for suggestion but I still see that error.... Maybe my DVD drive have problem? The CD is perfectly ok

---

### Post by mc4man on 2011-02-08
When you insert the audio cd does an icon show up on the Desktop?
The sudo lshw ... you posted before indicated no disc in the drive
> configuration: ansiversion=5 status=nodisc
When an audio cd is in the drive the lshw ...  command should show 'ready'
Ex. here, audio cd in my second drive
>  *-cdrom:1
       description: DVD reader
       product: DVD-ROM GDR8164B
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 0L06
       capabilities: removable audio dvd
       configuration: ansiversion=5 [COLOR="Blue"]status=ready[/COLOR]


Bit of a longshot - search gvfs in synaptic, completely remove and then re-install the gvfs-backend package

> Maybe my DVD drive have problem? 
Always a possibility

---

### Post by carfield on 2011-02-09
I just try with all my CDs, some work and some doesn't, but they are all worked in Windows, look like somehow my DVD-RW more sensitive to bad CD disc

---

