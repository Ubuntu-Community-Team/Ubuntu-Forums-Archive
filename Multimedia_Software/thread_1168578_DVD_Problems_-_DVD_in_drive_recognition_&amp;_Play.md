---
title: "DVD Problems - DVD in drive recognition &amp; Playback problems"
date: 2009-05-24
forum: Multimedia Software
---

### Post by cynicalcylon on 2009-05-24
Right, this is gonna be a long list, so please bare with me.
Also, I'm a Linux/Ubuntu  baby, but will happily accept & follow any advice given.

Firstly, and I guess most importantly, no DVDs I insert into my DVD drive are being recognised as inserted - it's like nothing is there.
I don't **think** it's a problem with the actual player, as I have been able to view DVDs in the past and have created data CDs (for use with Windows systems) with no problems; ie. the system recognises that there is is a blank CD in the drive.
Sometimes, the system recognises that there is a DVD in the drive, but with no particular rhyme or reason to it I have been unable to deliberately do so.
BTW, when I am having this problem, I have noticed that the little green-working light on the front of the drive always flashes away like a goodun (but not when the DVD is recognised), is it trying to tell me something?

Secondly, on the rare occassions that the system has recognised that there is a DVD in the drive, as soon as I have to shut down or restart the system, problem 1 starts all over again.
I'm possibly doing something I'm not realising and as such am not saving any settings, but I don't know what I'm doing in the first place, even if I did know how to save the settings I may have inadvertantly created.

Thirdly, The few times I have been able to play DVDs, both the video and audio are jerky and/or pixelated (VLC Player), green-screened (Kaffeine), played menus but not main movie (Totem-xine) - with the following error message:

[IMG]http://img.photobucket.com/albums/v37/wiccachik/Misc/CSSError.png[/IMG]

I have all the restricted drivers, mediabuntu repositores and such, I have the newer 0.9.8a version of VLC, deleted Totem-gstreamer in favour of Totem-xine.
I have, in fact, done all that has been mentioned on the forums but to no avail.
I understand that this is a common problem, but nothing mentioned seems to work, unless I need to basically uninstall & reinstall it all from scratch :(

---

### Post by xc3RnbFO8P on 2009-05-24
Show the output of: 
> gedit /etc/fstab

---

### Post by cynicalcylon on 2009-05-24
Is this any good?

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5e36e626-21c3-47ab-b54a-ad6d0e8a2711 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6bc9c36b-7e87-49a4-8312-3c7657434721 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


---

### Post by xc3RnbFO8P on 2009-05-24
Insert DVD and in Terminal:
> sudo mount /media/cdrom0/ -o unhide

---

### Post by cynicalcylon on 2009-05-24
Got this:

> mount: No medium found

---

### Post by xc3RnbFO8P on 2009-05-24
In Terminal:
> sudo gedit /etc/fstab
copy/paste , save and reboot:
**/dev/scd0       /media/cdrom0 auto user,noauto,exec,utf8 0 0**
If it doesnt work:
> sudo gedit /etc/fstab
**/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0  0**

---

### Post by cynicalcylon on 2009-05-24
Still not showing as having a DVD present in the drive :confused:

---

### Post by mc4man on 2009-05-24
A few things stand out in your orig. post

> but with no particular rhyme or reason to it I have been unable to deliberately do so.
BTW, when I am having this problem, I have noticed that the little green-working light on the front of the drive always flashes away like a goodun


after inserting media the flashing light indicates the drive is trying to access sectors on the disk to identify the type, filesystem ,ect. If the light doesn't settle (go steady or off) then it's unable to do so
This usually indicates an issue with the drive (dirty or malfunctioning laser
How long have you waited before ejecting the disk?

> Secondly, on the rare occassions that the system has recognised that there is a DVD in the drive, as soon as I have to shut down or restart the system, problem 1 starts all over again.

Are you saying that once it's recognized a dvd then all dvd's inserted till a reboot are recognized? Or just the one in the drive?

If it's the former then try inserting a data or audio cd, accessing it, ejecting and then try a dvd (extremely rare and obscure issue with certain dvd drives

Put a dvd in the drive, wait a bit and run (whether the light settles or not
```
sudo lshw -C disk
```

The third issue is probably unrelated in you have libdvdcss2 and libxine1-ffmpeg installed, running this will ck.
```
sudo apt-get install libdvdcss2 libxine1-ffmpeg
```

---

### Post by cynicalcylon on 2009-05-24
> **mc4man said:**
> 
This usually indicates an issue with the drive (dirty or malfunctioning laser)
I decided to try a CD Lens Cleaner and a DVD Lens Cleaner disk, and they both played straight away, with no problems. I also played an audio CD, which worked fine.

> **mc4man said:**
> 
How long have you waited before ejecting the disk?
I have waited different amounts of time, between a few seconds and several hours.

> **mc4man said:**
> 
Are you saying that once it's recognized a dvd then all dvd's inserted till a reboot are recognized? Or just the one in the drive?
I had never thought to try a different DVD when it has been recognised, so I'm afraid that I do not know if it is just one disc at a time, if changing the DVD at this time makes a difference.
Well, I have just tried this and it worked when I inserted a first DVD, but when I inserted another DVD the problem was back again (ie. not recognising DVD in drive).

> **mc4man said:**
> 
If it's the former then try inserting a data or audio cd, accessing it, ejecting and then try a dvd (extremely rare and obscure issue with certain dvd drives)
I tried a DVD, after I successfully played the Lens Cleaners and the audio CD and it played fine, but when I changed the DVD to another the same problem happened (not recognising DVD in drive and lights flashing constantly)

> **mc4man said:**
> 
Put a dvd in the drive, wait a bit and run (whether the light settles or not
```
sudo lshw -C disk
```
When I tried this, I got the following:

>  *-cdrom                 
       description: DVD-RAM writer
       product: CD/DVDW SH-S182M
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: SB03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: ATA Disk
       product: MAXTOR STM350032
       vendor: Maxtor
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: MX15
       serial: 5QM0VWCH
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000b6113


---

### Post by mc4man on 2009-05-24
Well everything you've posted info wise from fstab to lshw is fine, plus cd's play and 'some' dvd's.
That would seem to indicate a drive issue.

What's not 100% clear is whether 'some' dvd's are -  individual dvd's, - totally at random for all dvd's or - a particular set of circumstances.
The latter may shift some or all of the cause away from a malfunctioning drive.

Small note: there are varying opinions on the usefulness of those cleaning disks, some swear by, others feel they can do more harm than good. At this point I would refrain from using anymore. Most cleaning disks are basically just an audio or data cd with a brush.

> I tried a DVD, after I successfully played the Lens Cleaners and the audio CD and [COLOR="Blue"]it played fine[/COLOR], but when I changed [COLOR="Red"]the DVD to another[/COLOR] the same problem happened

What you could try to do is see if there is a repeatable pattern using those 2 disks and possibly an audio cd.

Lets say you call the blue dvd dvd A and the red one dvd B

From a fresh boot does dvd A mount when inserted?

If it does, when you eject and re-insert does it mount?

If no to either does inserting, than ejecting an audio cd allow it to mount?

Then with dvd B repeat the above.

Does dvd B mount from any of the above circumstances?

---

### Post by koconnor100 on 2009-05-24
> **mc4man said:**
> A few things stand out in your orig. post




after inserting media the flashing light indicates the drive is trying to access sectors on the disk to identify the type, filesystem ,ect. If the light doesn't settle (go steady or off) then it's unable to do so
This usually indicates an issue with the drive (dirty or malfunctioning laser
How long have you waited before ejecting the disk?


Are you saying that once it's recognized a dvd then all dvd's inserted till a reboot are recognized? Or just the one in the drive?

If it's the former then try inserting a data or audio cd, accessing it, ejecting and then try a dvd (extremely rare and obscure issue with certain dvd drives

Put a dvd in the drive, wait a bit and run (whether the light settles or not
```
sudo lshw -C disk
```

The third issue is probably unrelated in you have libdvdcss2 and libxine1-ffmpeg installed, running this will ck.
```
sudo apt-get install libdvdcss2 libxine1-ffmpeg
```

THANK YOU THANK YOU THANK YOU THANK YOU ...

just a simple alt-F2 , a copy and paste  of that code string sudo apt-get ...etc etc ... and my dvd Kill Bill Vol 1 is now playing !!

THANK YOU THANK YOU THANK YOU THANK YOU ...

did I mention thank you ?

---

### Post by zobcat on 2009-05-24
This sounds like the same thing that happened to my sisters dvd drive. After trying everything in the world, it ended up being a dirty lens. If you're comfortable opening up the drive itself, all you have to do is get to the lens and gently clean it with a Q-tip. Or, you could just go buy a new one for $20.  Good luck!

---

### Post by cynicalcylon on 2009-05-25
> **mc4man said:**
> 
From a fresh boot does dvd A mount when inserted?
No

> **mc4man said:**
> 
If no to either does inserting, than ejecting an audio cd allow it to mount?
Then with dvd B repeat the above.
Does dvd B mount from any of the above circumstances?
I tried first one audio CD before - no DVD mount after
I then tried 2 different CDs before - no DVD mount
I tried this with several different CDs and DVDs and it didn't mount at all this time.

---

### Post by cynicalcylon on 2009-05-25
Well, it now appears that it was indeed the actual drive that was the problem.

After various comments about the drive possibly being the problem and **zobcat**'s suggestion about getting a new one (I really hadn't thought about it until then, so thank you), I put in an old drive I had kept from my last PC build and I have had no problems[B].

[/B]I would just like to thank you all from the bottom of my heart for all the advice and help you have given me. You gave me so much time & help, I'm just sorry it was an easy fix that I hadn't even realised was an option until now.
Much luv to you! :D

---

