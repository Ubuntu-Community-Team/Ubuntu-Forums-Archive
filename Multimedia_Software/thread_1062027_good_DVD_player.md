---
title: "good DVD player?"
date: 2009-02-06
forum: Multimedia Software
---

### Post by braveheart2 on 2009-02-06
i can't get any of my DVD's to work with the default Ubuntu apps...i've done everything it says to do in the 8.10 documentation for DVD watching and it doesn't work...so what would be a good DVD media player? if its going to be cross platform than how do i install it to wine?

thanks:D

---

### Post by Melcar on 2009-02-06
Try VLC.

---

### Post by nebu on 2009-02-06
try mplayer

---

### Post by braveheart2 on 2009-02-06
> **Melcar said:**
> Try VLC.

ok, do i need any of the plugins or the version with X support? or just the multimedia streamer and common data? is there anything else i should know before installing this?

---

### Post by wolfen69 on 2009-02-06
if you add the medibuntu repo and libdvdcss2, you should have no problems. i use vlc.

---

### Post by braveheart2 on 2009-02-06
this is the error i get when using Mplayer.

---

### Post by braveheart2 on 2009-02-06
how do i install medibuntu? the site doesn't make sense.

(sorry about double post, didn't mean to)

---

### Post by 123Mike on 2009-02-06
mplayer has to be the grand master overlord of player software. Normally just command line, but there are a number of gui front ends for it. I think mplayer has an optional gui version as well (gmplayer)

Also, I've seen a few dvd rip programs as well. Acidrip and ogmrip from what I recall. It let's you convert a dvd into a video file, and uses mencoder (which is part of mplayer) to encode/convert the video. mencoder is probably also the grand master overlord of encoders.

---

### Post by andrew.46 on 2009-02-06
Hi 123Mike,

> **123Mike said:**
> mplayer has to be the grand master overlord of player software. Normally just command line, but there are a number of gui front ends for it. I think mplayer has an optional gui version as well (gmplayer)

A recent development for MPlayer has also been the incorporation of the code that allows the use of DVD menus when accessing a DVD movie. I am not sure if the best MPlayer front-end SMPlayer has support for this feature yet.

Andrew

---

### Post by Crafty Kisses on 2009-02-06
VLC all the way!

---

### Post by mc4man on 2009-02-06
> I am not sure if the best MPlayer front-end SMPlayer has support for this feature yet.
It does if you make a change in the setting for the mouse, the implementation isn't so good yet (in regards to mplayer, mainly audio stream related)

@braveheart2
that error in mplayer suggests it's looking to the wrong device. Mplayer defaults to /dev/dvd, your drive may be /dev/dvd1 or higher
run this to see

```
sudo lshw -C disk
```

---

### Post by braveheart2 on 2009-02-06
@mc4man, ok i did it...now what am i looking for in the terminal after i type that?

---

### Post by Bablefish on 2009-02-06
I like Kaffiene

---

### Post by mc4man on 2009-02-06
> looking for in the terminal after i type that? 

Here's part of the entry for one of my cd/dvd drives ( look at red arrow, the blue arrow is good to know also
>  *-cdrom:0               
       description: DVD-RAM writer
       product: DVD A  DH20A4P
       vendor: ATAPI
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1 [COLOR="Red"] <---[/COLOR]
       logical name: /dev/dvdrw1
       logical name: /dev/scd0   [COLOR="Blue"]<---[/COLOR]
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: 9P59
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready


---

### Post by braveheart2 on 2009-02-06
> **mc4man said:**
> Here's part of the entry for one of my cd/dvd drives ( look at red arrow, the blue arrow is good to know also

well mine is different...so im guessing thats bad? how do i change it? is yours set to watch DVD's?

---

### Post by mc4man on 2009-02-06
Why don't you just copy and paste what your seeing into a reply to this thread

---

### Post by braveheart2 on 2009-02-06
```
faith11@ubuntufaiths:~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: WDC WD1600AAJB-2
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 58.0
       serial: WD-WCAS29050790
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0004e19d
  *-cdrom
       description: DVD reader
       product: DVD-ROM SD-616Q
       vendor: SAMSUNG
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: F403
       capabilities: removable audio dvd
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted
faith11@ubuntufaiths:~$ 

```

there ya go.

---

### Post by mc4man on 2009-02-06
Looks absolutely fine, did you follow the adcive offered earlier in this thread about medibuntu, libdvdcss2 ect.?

If so you may need to ck. to see if a region has been set on the drive.

If not there a sticky in the main page for Multimedia & Video you can look thru or here's a simple dvd only 

[http://ubuntuforums.org/showthread.php?p=6223490#post6223490](http://ubuntuforums.org/showthread.php?p=6223490#post6223490)

( to ck. settings on mplayer open it  from the Applications menu, right click -> preferences -> misc, if it says /dev/dvd for DVD Device your good there

---

### Post by Nakota on 2009-02-06
the easyest way is to install an app called ubuntu twaek its 3ed party ([http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)) from here you open the applcations tab then the third party packages from this point you will need to hit the unlock button (keep in mind that third party programs can be securety risks but in this instance its coming from an ubuntu server so it should be ok) check the mediabuntu checkbox and close the program (it will ask to reload... let it) now the mediabuntu packages should be avalible from synaptic, check libdvdcss2 and apply you should now be able to play dvds.... be aware that if your in the us its illigal to download a dvd codac without paying the creator (if you have one under windows i beleve that counts as paying for it seeing as its the same pc) 

if you install any of the other 3ed party packages and synaptic shows an error uncheck it and refresh and it should resolve the problem

---

### Post by braveheart2 on 2009-02-07
> **mc4man said:**
> Looks absolutely fine, did you follow the adcive offered earlier in this thread about medibuntu, libdvdcss2 ect.?

If so you may need to ck. to see if a region has been set on the drive.

If not there a sticky in the main page for Multimedia & Video you can look thru or here's a simple dvd only 

[http://ubuntuforums.org/showthread.php?p=6223490#post6223490](http://ubuntuforums.org/showthread.php?p=6223490#post6223490)

( to ck. settings on mplayer open it  from the Applications menu, right click -> preferences -> misc, if it says /dev/dvd for DVD Device your good there
that link fixed all my problems, thank you! wow Ubuntu is amazing:shock:
> **Nakota said:**
> the easyest way is to install an app called ubuntu twaek its 3ed party ([http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)) from here you open the applcations tab then the third party packages from this point you will need to hit the unlock button (keep in mind that third party programs can be securety risks but in this instance its coming from an ubuntu server so it should be ok) check the mediabuntu checkbox and close the program (it will ask to reload... let it) now the mediabuntu packages should be avalible from synaptic, check libdvdcss2 and apply you should now be able to play dvds.... be aware that if your in the us its illigal to download a dvd codac without paying the creator (if you have one under windows i beleve that counts as paying for it seeing as its the same pc) 

if you install any of the other 3ed party packages and synaptic shows an error uncheck it and refresh and it should resolve the problem

ok, I'll look into that.

---

