---
title: "copyrighted DVDs not playing"
date: 2012-09-25
forum: Multimedia Software
---

### Post by p110011 on 2012-09-25
I can mount a burned DVD someone gave me, and I can see my back-up files I burned to a DVD, but I can't watch a store bought movie. 

I went through all this [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) Installed the Ubuntu-Restricted-Extras, but still no good.

Funny, the other day I went through this and it worked, now I cant get it going again. :confused:

---

### Post by OrangeCrate on 2012-09-25
<Never mind, I see you already had what I was going to suggest.>

---

### Post by josephmills on 2012-09-25
have you tried to install libdvdcss2 ? 
[http://download.videolan.org/](http://download.videolan.org/)


I also think that medibuntu has that in there repo ? 
[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)


Hope that this helps

---

### Post by necromonger on 2012-09-25
it could also be cinavia and i do not know of a fix.

---

### Post by p110011 on 2012-09-25
> **josephmills said:**
> have you tried to install libdvdcss2 ? 
[http://download.videolan.org/](http://download.videolan.org/)


I also think that medibuntu has that in there repo ? 
[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)


Hope that this helps
I am now getting updates for libdvdcss2 in auto updates, it says it is  downloaded, but not installed. I'll try to get it installed

---

### Post by BicyclerBoy on 2012-09-25
Cinavia is audio watermarking..
Doesn't cinavia pop up warning messages on supporting displays?

Play (decode) your audio (AC3/DTS) thru' external AVR/HTamp..
You can transcode to audio format that is decoded externally (AC3, DTS).

Do you know if new "real-brand" AVR/HT-amps support cinavia ?

@OP
I sometimes get problems if DVD is in drive after reboot or some periodic system probing etc..
Eject & re-insert the DVD, wait until DVD mounts..
Run handbrake & look at the output log..

BDs playback (not BD+) much better than DVDs if you can live without menus.

---

### Post by p110011 on 2012-09-25
> **BicyclerBoy said:**
> 

@OP
I sometimes get problems if DVD is in drive after reboot or some periodic system probing etc..
Eject & re-insert the DVD, wait until DVD mounts..
Run handbrake & look at the output log..

BDs playback (not BD+) much better than DVDs if you can live without menus.

Thanks, but I've rebooted about ten times trying to get a DVD mounted.
The drive spins a bit, and no apps. show a DVD drive mounted, nothing shows in the file browser. But like I said, other types of data will get the drive mounted.
Here is my sudo lshw of my removable disk drives with pulp fiction inserted.
[HTML]*-cdrom:0
                description: DVD writer
                product: DVDR   PX-716A
                vendor: PLEXTOR
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: 1.03
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
           *-cdrom:1
                description: SCSI CD-ROM
                product: CD-ROM F564E
                vendor: OEM
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/sr1
                version: 1.15
                capabilities: removable audio
                configuration: ansiversion=5 status=nodisc
[/HTML]

---

### Post by BicyclerBoy on 2012-09-25
That's not what I meant..

Eject & re-insert **after** any reboot..
It is possible your /etc/fstab or udev rules do not auto mount the DVD..but why this does stop all types of DVD disks from mounting is unexplained..

Try
mkdir /media/dvdrom
mount -t iso9660 -o ro /dev/sr0 /media/dvdrom
ls -al /media/dvdrom/

or run HandBrake on the disk & look at the stdout log..

---

### Post by p110011 on 2012-09-25
> **BicyclerBoy said:**
> That's not what I meant..

Eject & re-insert **after** any reboot..
It is possible your /etc/fstab or udev rules do not auto mount the DVD..but why this does stop all types of DVD disks from mounting is unexplained..

I've tried both ejecting and leaving the disk after a reboot.
> **BicyclerBoy said:**
> 
Try
mkdir /media/dvdrom
mount -t iso9660 -o ro /dev/sr0 /media/dvdrom
ls -al /media/dvdrom/

or run HandBrake on the disk & look at the stdout log..
I actually just got handbrake a few hours ago, just before I found this problem.
I was looking for the logs you referred, and after I clicked source/dvd I saw my movie. So now I'm putting a file on a micro card to play in a tablet (the whole reason for how I got to this point). 

I'll try the commands later, does that change the drive to auto mount?

---

### Post by josephmills on 2012-09-25
did you install ubuntu-restricted-extras,libdvdread4 , libdvdnav4 and libdvdcss2 

```
sudo apt-get install ubuntu-restricted-extras libdvdread4 libdvdcss2 libdvdnav4 
```

Yet ?

---

### Post by p110011 on 2012-09-25
> **josephmills said:**
> did you install ubuntu-restricted-extras,libdvdread4 , libdvdnav4 and libdvdcss2 

```
sudo apt-get install ubuntu-restricted-extras libdvdread4 libdvdcss2 libdvdnav4 
```Yet ?

Yes I did. It seemed a bit strange to me that I got a few updates on the dvdcss2 within a few days. But looking at the software manager, all are now installed.

---

### Post by BicyclerBoy on 2012-09-26
@OP post #9

HandBrake click "activity window..

---

### Post by p110011 on 2012-09-26
Thanks, OK, at first there was just two lines until I clicked source/DVD again. Here is the log.
[HTML][06:58:07] gtkgui: HandBrake rev4860 (2012071899) - Linux i686 - http://handbrake.fr
[06:58:08] hb_init: starting libhb thread
[06:58:08] hb_init: starting libhb thread
libdvdread: Using libdvdcss version 1.2.12 for DVD access
[06:59:48] hb_scan: path=/dev/dvd, title_index=0
libbluray/bdnav/index_parse.c:157: indx_parse(): error opening /dev/dvd/BDMV/index.bdmv
libbluray/bluray.c:1471: nav_get_title_list(/dev/dvd) failed (0xb470658)
[06:59:48] bd: not a bd - trying as a stream/file instead
[06:59:48] dvd: Region mask 0xfe
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.12 for DVD access
libdvdnav: DVD Title: PULP
libdvdnav: DVD Serial Number: 26E95242
libdvdnav: DVD Title (Alternative): PULP
libdvdnav: Unable to find map file '/home/chouinard/.dvdnav/PULP.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000024f7
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000081c6
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 1
libdvdread: Using libdvdcss version 1.2.12 for DVD access
[06:59:49] scan: DVD has 1 title(s)
[06:59:49] scan: scanning title 1
[06:59:49] scan: opening IFO for VTS 1
[06:59:49] scan: duration is 02:34:12 (9252076 ms)
[06:59:49] pgc_id: 1, pgn: 1: pgc: 0xb487478
[06:59:49] scan: vts=1, ttn=1, cells=0->38, blocks=0->3944604, 3944605 blocks
[06:59:49] scan: checking audio 1
[06:59:49] scan: id=0x80bd, lang=English (AC3), 3cc=eng ext=1
[06:59:49] scan: checking audio 2
[06:59:49] scan: id=0x81bd, lang=Espanol (AC3), 3cc=spa ext=1
[06:59:49] scan: checking subtitle 1
[06:59:49] scan: id=0x20bd, lang=English (Closed Caption), 3cc=eng
[06:59:49] scan: title 1 has 28 chapters
[06:59:49] scan: chap 1 c=0->0, b=0->10024 (10025), 28063 ms
[06:59:49] scan: chap 2 c=1->2, b=10025->119581 (109557), 259624 ms
[06:59:49] scan: chap 3 c=3->3, b=119582->170179 (50598), 136333 ms
[06:59:49] scan: chap 4 c=4->4, b=170180->355090 (184911), 439777 ms
[06:59:49] scan: chap 5 c=5->5, b=355091->529339 (174249), 409610 ms
[06:59:49] scan: chap 6 c=6->7, b=529340->663126 (133787), 308574 ms
[06:59:49] scan: chap 7 c=8->8, b=663127->797964 (134838), 326487 ms
[06:59:49] scan: chap 8 c=9->9, b=797965->854502 (56538), 140352 ms
[06:59:49] scan: chap 9 c=10->11, b=854503->1164936 (310434), 748945 ms
[06:59:49] scan: chap 10 c=12->13, b=1164937->1253899 (88963), 195575 ms
[06:59:49] scan: chap 11 c=14->14, b=1253900->1370837 (116938), 291502 ms
[06:59:49] scan: chap 12 c=15->16, b=1370838->1595914 (225077), 520918 ms
[06:59:49] scan: chap 13 c=17->17, b=1595915->1773585 (177671), 430486 ms
[06:59:49] scan: chap 14 c=18->18, b=1773586->1881888 (108303), 251272 ms
[06:59:49] scan: chap 15 c=19->20, b=1881889->2075522 (193634), 463688 ms
[06:59:49] scan: chap 16 c=21->21, b=2075523->2241077 (165555), 408629 ms
[06:59:49] scan: chap 17 c=22->22, b=2241078->2357337 (116260), 266331 ms
[06:59:49] scan: chap 18 c=23->23, b=2357338->2455746 (98409), 227412 ms
[06:59:49] scan: chap 19 c=24->25, b=2455747->2597825 (142079), 328499 ms
[06:59:49] scan: chap 20 c=26->27, b=2597826->2753751 (155926), 365649 ms
[06:59:49] scan: chap 21 c=28->28, b=2753752->2818794 (65043), 147159 ms
[06:59:49] scan: chap 22 c=29->29, b=2818795->2907864 (89070), 208392 ms
[06:59:49] scan: chap 23 c=30->30, b=2907865->2952301 (44437), 116292 ms
[06:59:49] scan: chap 24 c=31->31, b=2952302->3087716 (135415), 304516 ms
[06:59:49] scan: chap 25 c=32->33, b=3087717->3385593 (297877), 668768 ms
[06:59:49] scan: chap 26 c=34->36, b=3385594->3829685 (444092), 985564 ms
[06:59:49] scan: chap 27 c=37->37, b=3829686->3944599 (114914), 273472 ms
[06:59:49] scan: chap 28 c=38->38, b=3944600->3944604 (5), 176 ms
[06:59:49] scan: aspect = 0
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
[06:59:53] scan: decoding previews for title 1
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
[06:59:53] scan: title angle(s) 1
[06:59:53] scan: audio 0x81bd: AC-3, rate=48000Hz, bitrate=192000 Espanol (AC3) (Dolby Surround)
[06:59:53] scan: audio 0x80bd: AC-3, rate=48000Hz, bitrate=384000 English (AC3) (5.1 ch)
[06:59:57] scan: 10 previews, 720x480, 23.976 fps, autocrop = 100/106/0/2, aspect 1.33:1, PAR 8:9
[06:59:57] scan: title (0) job->width:640, job->height:272
[06:59:57] libhb: scan thread found 1 valid title(s)
libdvdread: Using libdvdcss version 1.2.12 for DVD access
[/HTML]

I was able to put this movie on my Arcos Tablet with Handbrake, but I still can't watch a DVD on this PC. I just tried using VLC, and after browsing for a disk I just chose dev/dvd, I got part of the movie "main" menu. It was pixelated  and sound was skipping.

---

### Post by BicyclerBoy on 2012-09-26
If your VLC is std. package build it uses system libdvdnav, libdvdread both are likely out-dated.
Current libdvdread is at >=4.2..later is not always better tho..

This does not affect self-contained packages..maybe your HandBrake uses private patched version of the libraries..

Could be region 1 problems..Region 1 DVDs are able to be inflected with extra protection RCE.
Try playing the title track directly, no menu..

Looks like HandBrake has BD support now...

---

### Post by p110011 on 2012-09-27
> **BicyclerBoy said:**
> If your VLC is std. package build it uses system libdvdnav, libdvdread both are likely out-dated.
Current libdvdread is at >=4.2..later is not always better tho..

This does not affect self-contained packages..maybe your HandBrake uses private patched version of the libraries..

Could be region 1 problems..Region 1 DVDs are able to be inflected with extra protection RCE.
Try playing the title track directly, no menu..

Looks like HandBrake has BD support now...
Well I can't browse for any title or .TS, VLC only showed dvd. Nothing expands to show what's inside. I do have Handbrake working now, so it's good.

---

