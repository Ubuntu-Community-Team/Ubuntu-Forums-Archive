---
title: "[SOLVED] dvd isn't recognized"
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by dsimpson on 2007-12-20
I put in a DVD to play and the light on the DVD blinks but nothing plays and the VLC players doesn't open. I go to Computer and click on CDROM/DVD-ROM and I get an error message which says; Unable to Mount media. There is probably no media in the drive. What is going on. I have a Samsung DVD-ROM SD 612, It is set up to run on VLC player, but nothing is happening. I downloaded and activated VLC, installed all the codecs, did the region setting and still nothing. I really need detailed help with this one. Tell me what other information I need to post to get this fixed. Thanks

---

### Post by Ampi on 2007-12-20
I'm having the same problem. I don't understand it because on my Fedora 4 it works perfectly but in my Ubuntu it doesn't, so help is welcome....

---

### Post by dsimpson on 2007-12-21
I appreciate that the problem is out there, but am hoping that there is someone who has an answer to our problem. I cannot think that this is an isolated incident that someone else hasn't experienced so please, someone! send a fix my way.

---

### Post by logos34 on 2007-12-21
post the output from the following:

sudo lshw -C disk

cat /etc/fstab

What about cds, do they work?

---

### Post by Ampi on 2007-12-21
Cd's do work! But DVD's still don't, you can choose the DVD and push "play" but then it just does nothing...

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# /dev/hdb1
UUID=2596ce7d-0a93-4975-a56c-14b9bf57272e  /               ext3         defaults,errors=remount-ro  0  1  
# /dev/hdb5
UUID=3969b0e6-6281-4940-9964-7c28b8721607  none            swap         sw                          0  0  
/dev/hdd                                   /media/cdrom0   udf,iso9660  user,noauto                 0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto              0  0  

/dev/hda1                                  /mnt/fedora     ext3         defaults                    0  0  
/dev/hdb1                                  /media/hdb1     ext3         defaults                    0  0  
/dev/hdb5                                  /media/hdb5     swap         defaults                    0  0

> 
  *-disk:0                
       description: ATA Disk
       product: Maxtor 6E040L0
       vendor: Maxtor
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: NAR61590
       serial: E16X9MSE
       size: 38GB
       capacity: 38GB
       capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
       configuration: apm=off mode=udma5 smart=on
  *-disk:1
       description: ATA Disk
       product: MAXTOR 6L040J2
       vendor: Maxtor
       physical id: 1
       bus info: ide@0.1
       logical name: /dev/hdb
       version: A93.0500
       serial: 662131550926
       size: 37GB
       capacity: 37GB
       capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
       configuration: mode=udma5 smart=on
  *-cdrom
       description: DVD writer
       product: BENQ DVD DD DW1640
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       version: BSJB
       serial: 9JB5U150F253191354PP
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
       configuration: mode=udma2 status=ready
     *-disc
          physical id: 0
          logical name: /dev/hdd

---

### Post by logos34 on 2007-12-21
ok, it''s being detected correctly.

what about

ls -l /dev | grep dvd*

---

### Post by schauerlich on 2007-12-21
DVD's won't play by default in Ubuntu because they use a proprietary codec. Instructions to install these can be found on this thread: [http://ubuntuforums.org/showthread.php?t=539884](http://ubuntuforums.org/showthread.php?t=539884)

---

### Post by logos34 on 2007-12-21
If you just put in the VLC codecs and not libdvdcss2, then read this:

[https://help.ubuntu.com/community/RestrictedFormats#head-79bfba9a0e96d62a622a47430239a1d49454c953](https://help.ubuntu.com/community/RestrictedFormats#head-79bfba9a0e96d62a622a47430239a1d49454c953)

you need to add Medibuntu repos to sources

---

### Post by dsimpson on 2007-12-21
logos34, thanks for the reply, here is what I have listed. Duane



 *-disk:0                
       description: ATA Disk
       product: WDC WD800JB-00JJC0
       vendor: Western Digital
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: 05.01C05
       serial: WD-WCAM9M535909
       size: 74GB
       capacity: 74GB
       capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
       configuration: mode=udma4 smart=on
  *-disk:1
       description: ATA Disk
       product: WDC WD400BB-00AUA1
       vendor: Western Digital
       physical id: 1
       bus info: ide@0.1
       logical name: /dev/hdb
       version: 18.20D18
       serial: WD-WMA6R2081558
       size: 37GB
       capacity: 37GB
       capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
       configuration: mode=udma4 smart=on
  *-cdrom:0
       description: CD-R/CD-RW writer
       product: SONY CD-RW CRX140E
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: 1.0n
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
       configuration: mode=udma2 status=nodisc
  *-cdrom:1
       description: DVD reader
       product: SAMSUNG DVD-ROM SD-612
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       version: BS04
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
       configuration: status=nodisc
  *-disk
       description: SCSI Disk
       product: psc 2510
       vendor: HP
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 1.00
       capabilities: removable
       configuration: ansiversion=2
     *-disc
          physical id: 0
          logical name: /dev/sda

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=2be3b0b2-0f0a-4fa6-a99c-0550a2571d91 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=973af920-518c-4a66-ba39-93da31a977f9 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by dsimpson on 2007-12-21
logos34, also on the last post you did, here is what I got;

ls -l /dev | grep dvd*
lrwxrwxrwx 1 root   root           3 2007-12-14 13:00 dvd -> hdd

---

### Post by logos34 on 2007-12-21
well, there's a symlink to the correct device, 

If you can read and burn DATA dvds (you can right?), just not play movies, then it's likely a codecs issue.  Get the restricted-extras pkg and/or libdvdcss2 and hopefully that will solve the problem.

---

### Post by dsimpson on 2007-12-21
No, I cannot even open the player to view or play any files that I know, don't have any dvd data discs to try. I tried opening a dvd of photos saved from a digital camera and it gave me the same message, although when I checked it the next day, (I left the dvd in overnight) the pictures had loaded. I was able to then save to my harddrive for viewing. I don't know how that happened. I have gone to medibuntu, done the libdvdcss thing, done the regionset, but it just seems that the dvd player isn't recognized although it shows up in the file browser as the correct player. When I try to mount, it doesn't even attempt it, just the error message.

---

### Post by logos34 on 2007-12-21
hmm...

(you probably already have done this) run

gnome-volume-properties

-tick first three boxes on storage tab
-on multimedia tab tick video playback box and select vlc

---

### Post by dsimpson on 2007-12-21
have done all that with the exception being vlc %m, which I got from another post, can't remember where, but it is supposed to use vlc if there are other media available.

Unable to mount media. there is probably no media in the drive

this is ridiculous, I have a dvd in there, but it isn't seen.

---

### Post by Leo the Lion on 2007-12-21
> **logos34 said:**
> hmm...

(you probably already have done this) run

gnome-volume-properties

-tick first three boxes on storage tab
-on multimedia tab tick video playback box and select vlc

I'm having a very similar problem. CDs play fine, but when I insert a DVD, either Totem or VLC will recognize and play them but I get a scrambled screen (see picture)

---

### Post by mc4man on 2007-12-21
While this probably is not going to help you and certainly not what you want to hear maybe you need to get a new drive. I had a similar though more mysterious issue over the summer where commercial dvds would only mount as blank media. Won't bore you with the details, thread is here
[http://ubuntuforums.org/showthread.php?t=551147](http://ubuntuforums.org/showthread.php?t=551147)
In any event I came to the conclusion that while the affected drives still worked ok in windows,, they were getting old and ubuntu (or linux) is more sensitive to such. There seems to be a limited time frame in which media has to recognized or it either doesn't mount or mounts wrong. Replacing the drives fixed it immediately. Hopefully you can find other solution

---

### Post by dsimpson on 2007-12-21
thanks mc4man, you're right, not exactly what I want  to hear. Unlike leo the lion, I don't even get a scrambled picture, I can't even get it mounted. I will wait for more help, hoping that I don't really have to spring for a new dvd drive. Live 3 hours from the nearest computer store so I will not jump on the last suggestion until absolutely the last thing to try. 
Anyone else have suggestions to try?

---

### Post by dsimpson on 2007-12-21
As an add on bit of information, I tried; mounting a cd in the cdrw player, everything worked fine, it mounted, the disc show up under computer etc. I did the same on my dvd player and the cd mounted fine, the disc showed up under computer and the files and jpegs opened up fine. It just seems that the dvd drive isn't recognizing the dvd's that are placed in there for play. What could be causing this?

---

### Post by mc4man on 2007-12-22
a little snippet from a tech blog concerning dvd drives that  _may_ be relevant

These are basically two drives in one, they use a dual laser package since a DVD laser won't read CDs and vice versa. The drive is seemingly failing to switch between modes properly, you didn't say what make of drive it is, but this used to be a common fault with Samsung drives.

---

### Post by dsimpson on 2007-12-22
thanks Mc4man,
That could very well be my problem, I posted my system earlier and the dvd is Samsung CD/DVD ROM -SD612 as the model. I will wait to see if there has been any way this might have been resolved or if a new DVD is needed. I won't post as resolved just yet.

---

### Post by logos34 on 2007-12-22
> **Ampi said:**
> Cd's do work! But DVD's still don't, you can choose the DVD and push "play" but then it just does nothing...

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
[B]# /dev/hdb1
UUID=2596ce7d-0a93-4975-a56c-14b9bf57272e / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb5
UUID=3969b0e6-6281-4940-9964-7c28b8721607 none swap sw 0 0[/B]
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

/dev/hda1 /mnt/fedora ext3 defaults 0 0
[COLOR="Red"]/dev/hdb1 /media/hdb1 ext3 defaults 0 0
/dev/hdb5 /media/hdb5 swap defaults 0 0[/COLOR]


Ampi,

I just noticed that you have conflicting entries in fstab, which can't be helping anything.  Open it as root 

gksudo gedit /etc/fstab

and take out the lines in red.

---

### Post by Leo the Lion on 2007-12-22
logos34, here's my output for cat /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d6f5da88-a112-4446-8fdb-c2f1a454d209 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=259b5c3b-90b8-49d4-bc39-22f2f9676ee0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by logos34 on 2007-12-22
> **Leo the Lion said:**
> logos34, here's my output for cat /etc/fstab:

fstab isn't your problem...dvds are playing but with a scrambled screen.  try a different video driver.

---

### Post by genfly on 2007-12-23
Hi, i'm having a similar problem and i am wondering if you could help please.

I keep gettnig an 'Unable to mount media' error every time i put in a dvd rw or dvd r disk. 

my fstab
-----------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ed1cb487-3e72-42d3-9b99-ba48b921138e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=917315f8-f78e-4691-adbb-5adfb70d595e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

----------
genfly@genfly:~$ ls -l /dev | grep dvd*
lrwxrwxrwx 1 root   root           3 2007-12-23 10:15 dvd -> hdc
lrwxrwxrwx 1 root   root           3 2007-12-23 10:15 dvdrw -> hdc

-----------

Blockdevice:    /dev/hdc
Generic device: 
Vendor:         TOSHIBA
Description:    DVD-ROM SD-R6012
Version:        1M31
Write speed:    3324
Profiles:       DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, CD-ROM, CD-R, CD-RW
Read Cap:       DVD-ROM, DVD-R, DVD-R Sequential, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, CD-ROM, CD-R, CD-RW
Write Cap:      DVD-R, DVD-R Sequential, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, CD-R, CD-RW
Writing modes:  SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R96R, Restricted Overwrite
Reader aliases: /dev/hdc
--------

Any ideas? i put in disks that have stuff on it. no luck. tried burning to empty disks. no luck. it always says unable to mount, probably no media in the drive. I'm running gutsy gibbon and i'm using a laptop.

Thanks in advance!!!

---

### Post by Leo the Lion on 2007-12-23
> **logos34 said:**
> fstab isn't your problem...dvds are playing but with a scrambled screen.  try a different video driver.
The picture I posted was on another machine. I think I need to get codecs for that problem. The problem I'm referring to now is with another machine, a Dell Inspiron 4000. It has a CD-R/CD-RW/DVD player. CDs will play just fine, but DVDs won't mount and the light for the drive will just blink.
Sorry for the confusion.

---

### Post by mc4man on 2007-12-23
I think it would be interesting to know (cause I don't) if it's solely a drives responsibility to detect type of media, (cd vs. dvd ) or if there's some interaction between drive and Os in this regard.

---

### Post by dsimpson on 2007-12-23
I don't know if there is a problem i.e iteraction between drive and OS due to something in the Gutsy upgrade but I didn't seem to have this problem in Dapper. I could believe that maybe my drive has worn out, but it seems that this problem is popping up pretty regularly in this forum. There must be some developer out there that has looked at this problem and might have an opinion on it. I would like to get this resolved if possible.

---

### Post by dsimpson on 2007-12-26
Bumping back to see if I can get resolved. I don't want this problem to drift into the area of unanswered posts and disappear when there might be an answer out there. I know that many are like me, a little of knowledge, enough to get our system working but needing help with the really technical problems, and I also know there are some proficient techies out there that may not have looked at this post. I can only hope. HELP!

---

### Post by mc4man on 2007-12-26
Solely on my somewhat related experience I'd say 90% drive and 10% ubuntu/linux. This is only based on what I saw, not know. The fact that the issue disappeared immediately upon installing new drives points to the drives. The fact that they still worked in xp, and that the fix for my issue (inserting, mounting, ejecting a cd) only lasted till a reboot points to some limited issue in the os, hal, whatever with aging optical drives.
I wouldn't hold out for any resolution other then the obvious though what i never did try was removing the drive, booting up, shutting down, reinstalling drive, ect.  You never know...

---

### Post by dsimpson on 2007-12-26
When I am trying to start  VLC from terminal I get the following;

eaglesoldier@eaglesoldier-desktop:~$ vlc dvd://
VLC media player 0.8.6c Janus
[00000293] stream_out_standard private error: no access _and_ no muxer (fatal error)
[00000292] main stream output error: stream chain failed for `std{mux="",access="",dst="X11"}'
[00000290] main input error: cannot start stream output instance, aborting
[00000281] main playlist: nothing to play

Any ideas what that is trying to tell me? It seems to find the dvd player but not loading or finding any media in there, am I correct? what is access and what is muxer as related to reading/playing the dvd

---

### Post by mc4man on 2007-12-26
@dsimpson  did you clip the error message?, there's nothing there associated with an attempt access a dvd device or dvd playback. 
for instance setting up some error situations
```
doug@doug-desktop:~$ vlc dvd://
VLC media player 0.8.6d Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/scd0 with libdvdcss.
libdvdread: Can't open /dev/scd0 for reading
libdvdnav: vm: faild to open/read the DVD
[00000282] dvdread demuxer error: DVDRead cannot open source: /dev/scd0
[00000280] main input error: no suitable access module for `dvd://'
[00000271] main playlist: nothing to play
[00000271] main playlist: stopping playback     # no media present
```

 ```
doug@doug-desktop:~$ vlc dvd://
VLC media player 0.8.6d Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: Can't seek to block 32
libdvdnav: Unable to find map file '/home/doug/.dvdnav/.map'
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
[00000282] dvdread demuxer error: DVDRead cannot open source: /dev/scd0
[00000280] main input error: no suitable access module for `dvd://'
[00000271] main playlist: nothing to play
[00000271] main playlist: stopping playback    # blank media present

```
```
doug@doug-desktop:~$ vlc dvd://
VLC media player 0.8.6d Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat 
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000282] dvdread demuxer error: DVDRead cannot open source: 
[00000280] main input error: no suitable access module for `dvd://'
[00000271] main playlist: nothing to play
[00000271] main playlist: stopping playback   # replacing dvd-rom with cd-rom
```

and so on.Your error is related to streams

---

### Post by dsimpson on 2007-12-27
No, there is nothing cropped, that is all that was posted as a message while trying to start VLC from the terminal. I notice yours had libdvdreads and libdvdnavs and it was looking in dev/scd0 while my printout has none of that. Is it likely in the codecs? I downloaded everything from medibuntu in package form to get all the codecs that I might need. Followed all the steps in installing them. And it says I already have the latest version available.  What do you suppose could be the problem?

---

### Post by soltanis on 2007-12-27
I get this same problem!

I throw in the DVD, but Totem and VLC can't play it, no matter what I do. I installed all the codecs and the CSS and everything, but I get this:

```
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdnav: DVD Title: RUSH_HOUR_3
libdvdnav: DVD Serial Number: 37490248
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/soltanis/.dvdnav/RUSH_HOUR_3.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: ifoRead_VOBU_ADMAP vtsi failed - CRASHING
```

Why, why, why...

I think this is a different error than dsimpson, though. Don't know--what the heck is wrong with this thing?

---

### Post by mc4man on 2007-12-27
@dsimpson  i still think you need a new drive but that error message has got me very curious. i can't find any conditon that results in a similar error when running that command. All of them (8 - some off the wall ) always start with libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
For the hell of it why don't you do a complete removal/ reinstall of vlc (and ck. for those libs)
You might also glean some useful info from your system logs - check messages and debug

---

### Post by dsimpson on 2007-12-28
Hi Mc4man,
    Did as suggested and have a little more to post, it did change some but still failed to load. Here is what came up after remove/Add procedure on VLC.

r@eaglesoldier-desktop:~$ vlc dvd://
VLC media player 0.8.6c Janus
[00000297] stream_out_standard private error: no access _and_ no muxer (fatal error)
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Could not open /dev/hdd with libdvdcss.
libdvdread: Can't open /dev/hdd for reading
libdvdnav: vm: faild to open/read the DVD
[00000299] dvdread demuxer error: DVDRead cannot open source: /dev/hdd
[00000302] vcd access error: could not read TOCHDR
[00000302] vcd access error: no movie tracks found
[00000302] access_file access error: file /dev/hdd is empty, aborting
[00000302] cdda access error: could not read TOCHDR
[00000302] cdda access error: no audio tracks found
[00000290] main input error: no suitable access module for `dvd:///dev/hdd'
[00000281] main playlist: stopping playback


Do I need to reinstall the codecs from medibuntu after Adding VLC again? Any other suggestions to try, i am open to anything..:)

---

### Post by mc4man on 2007-12-28
I vote for new drive - sorry

---

### Post by mc4man on 2007-12-30
@dsimpson
out of curiosity i reinstalled the drive that was giving me issues over the summer, it now works fine. 
The only changes from then to now were new Os (fiesty> gutsy) and the fact that it was physically removed, reinstalled.If you haven't resolved your issue(s) maybe you should try it. If so for the hell of it ck. that the cable position/jumper settings make sense

---

### Post by dsimpson on 2007-12-30
Thanks, that might be worth a try, it's cheaper than a new drive.lol! I will check the jumpers but offhand don't know what it should be, hopefully it is one the housing somewhere.:)

---

### Post by blehman419 on 2007-12-30
dsimpson, I was having the same problem as you minutes ago.  I went to:

gnome-volume-properties

and unselected the 3rd option in storage.  My disc is no loading fine, and the only other thing I have done was up the drive and close it again (which I had already done to no avail).

Maybe my problem just solved itself, but it wouldn't hurt to try what I did.  I hope this helps.

---

### Post by dsimpson on 2007-12-30
blehman - tried your suggestion, not working for me. Still trying willing to try all fixes until I find the one that will do the trick. Thank you!

---

### Post by blehman419 on 2007-12-30
Did you eject the DVD and reinsert it after you unselected the third option?

---

### Post by dsimpson on 2007-12-30
yes I did, still nothing , just - Unable to Mount Media, there is probably no media in the Drive. That seems to be all I can get so far. I have also rebooted tried livecd and still nothing works.

---

### Post by blehman419 on 2007-12-31
I had all the same symptoms as you.  I wish I could help more, but I am just a beginner.  Hope everything works out.

---

### Post by dsimpson on 2007-12-31
Thank you for trying, I am calling it a night and will hit it again tomorrow evening. I am going to try disconnecting and reconnecting with a reboot in between tomorrow to see what happens, maybe it will pick it up and reset the defaults or something.[-o<

---

### Post by dsimpson on 2008-01-02
Back again with the same issues but with a few more testing done..I have disconnected the cable to the cd/dvd player and reconnected with a new boot done each time with no positive results, I can put an audio cd into the players (both cdrw and dvd) and play music files, but when I put a data cd into either it makes the icon for the disc disappear when I check under Places/Computer and it will not reappear until I remove the disc. Anyone have any ideas what could cause this? They will not play, or even be recognized as being in there, and I cannot click on the icon to open the cd/dvd player, Strange...Also when blank cd's- dvd's are inserted they are not recognized and I get the message that it is Unable To Mount..same as before...I see many posts similar to mine, there must be someone out there that has gotten this to work or someone who has knowledge on how Linux deals with the mounting of media under Ubuntu.  Someone HELP!  Please.. :(

---

### Post by Ampi on 2008-01-06
thanks a lot for the help! I installed the libdvdread-dev and now vlc works perfectly!

---

### Post by dsimpson on 2008-01-08
I am still wondering how I can have some play,( Audio,) and there is no mounting of any other media, ie, movies or graphics dvd's. I have a dvd player that seems to work but it cannot find the disc that is inserted in the drive. I am glad that others have been helped by my post but could someone please help me.

---

### Post by dsimpson on 2008-01-10
C'mon now, I see multiple instances of the related issues of DVD and CDROM read topics and it seems that not one really is answered to get to the RESOLVED classification, is the problem really unsolvable? Does this mean that there is nobody out there that is willing to tackle the issue? HELP!!!

---

### Post by mc4man on 2008-01-10
> I have a dvd player that seems to work 
can you describe in what ways it does work

---

### Post by dsimpson on 2008-01-11
Whenever I insert an Audio cd in it will display and play the music files without problems, but when I try to play video or dvd discs it comes back with a Unable to Mount Media, there is probably no media in the Drive. What would cause one type of cd to play and not another? It will do everything that it is supposed to do when it mounts an Audio file, the disc icon displays and it automounts etc. but nothing happens when any other type of file is inserted. On another aside, I am having the same symptoms with my CdRW player, it will do exactly the same thing, so I really doubt that I have 2 drives that failed in the same exact manner. I think it is somewhere in the code, just don't know if it is Linux or Ubuntu related, but my thoughts are it is 7.10 Gutsy problem, as I never had this happen when I used Dapper 6.06

---

### Post by mc4man on 2008-01-11
@  soltanis
if you happen to wander back  - that title is one of the very few that won't play back with open source players - though it will with the one closed source linux player. Another that won't play is hairspray

---

### Post by Ampi on 2008-01-22
Okay, so a couple of threads ago I happily announced to the world that my vlc player works, now I am here to tell you that that isn't entirely true! :(
Apparently some dvd's still aren't recognized by my vlc. The annoying thing is that this particular dvd IS regocnized by my old Fedora 4 (which I want to get rid off.... but not recognized by my new Ubuntu!
How can this be? How can I fix this?

---

### Post by Talako on 2008-01-22
OK, I've been searching for a fix for pretty much this same problem for a few weeks now, no one seems to know. It is not an encryption problem (I tested it on a DVD a friend burned for me).
Here is the errors (from the terminal)
```
~$ vlc
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Could not open /dev/hda with libdvdcss.
libdvdread: Can't open /dev/hda for reading
libdvdnav: vm: faild to open/read the DVD
[00000292] dvdread demuxer error: DVDRead cannot open source: /dev/hda
[00000295] vcd access error: could not read TOCHDR
[00000295] vcd access error: no movie tracks found
[00000295] access_file access error: file /dev/hda is empty, aborting
[00000295] cdda access error: could not read TOCHDR
[00000295] cdda access error: no audio tracks found
[00000290] main input error: no suitable access module for `dvd:///dev/hda'
[00000281] main playlist: nothing to play

```

Here is the printout from my fstab:
```
~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=2af76d0d-264a-4ca1-becf-743e20d7c895 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=d96112ed-c009-4a21-8c13-9afe1f952101 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

Here is the grep printout:
```
~$ ls -l /dev | grep dvd*
lrwxrwxrwx 1 root   root           3 2008-01-16 23:04 dvd -> hda

```

And finally, here is the lshw printout:
```
~$ sudo lshw -C disk
[sudo] password for mariot:
IDE                       
  *-cdrom          
       description: DVD reader
       product: JLMS DVD-ROM LTD-166S
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: DS08
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio dvd
       configuration: status=ready
     *-disc
          physical id: 0
          logical name: /dev/hda
  *-disk
       description: ATA Disk
       product: IBM-DTTA-351010
       vendor: IBM
       physical id: 1
       bus info: ide@0.1
       logical name: /dev/hdb
       version: T5CCA76B
       serial: WF0WFFA2759
       size: 9541MB
       capabilities: ata dma lba iordy smart pm partitioned partitioned:dos
       configuration: mode=udma2 smart=on

```

     The only difference between this setup and others i've done is that the optical drive and HDD are on the same IDE ribbon, which shouldn't matter, but i've heard weirder. It is indeed a slightly aged DVD reader, but I don't think it's that old. My laptop (Sony VAIO PCG-K13) works fine, no issues with DVD playback, encrypted or not.
     Hopefully the more information we can gather in one place about this problem, the more attention we can grab for the problem. I do have a new(ish) DVD burner that I bought about 2 years ago, gotta snag it from my brother's machine (gave it to him a while ago) will update you guys on what that brings.
Peace,
Talako

---

### Post by Talako on 2008-01-22
One diagnosis step I may suggest, see if you can get hold of a friend/coworker/family member sympathetic to your cause, with a working DVD player, try plugging it in and see what happens, just to rule out hardware. Just a thought.

---

### Post by sanddgroper on 2008-01-23
> **dsimpson said:**
> C'mon now, I see multiple instances of the related issues of DVD and CDROM read topics and it seems that not one really is answered to get to the RESOLVED classification, is the problem really unsolvable? Does this mean that there is nobody out there that is willing to tackle the issue? HELP!!!

It would appear so.I have a system with a removable hard drive bay and I can use 6.06,7.04 and 7.10 on the same machine and get different results with each version.
The problem for me seems to only affect DVD's I have burnt myself.

Cheers
Sandy

---

### Post by dsimpson on 2008-01-23
Talako,
I like your idea about gathering as much ideas in one place, I have been trying all the posts and now forgot all the changes, fixes that I have tried because I have been so many places in which others had the same or similar problem. Your error message is almost like mine, fstab,grep etc, so I am inclined to think this isn't hardware related, unless we all are experiencing the same failure. Welcome sandgroper to our effort.=D>

---

### Post by sanddgroper on 2008-01-23
dsimpson
There is an extended thread here

[http://ubuntuforums.org/showthread.php?t=182415&page=14](http://ubuntuforums.org/showthread.php?t=182415&page=14)

Also for those that want to read an extended version of the trouble
shooting I did on my machine.

Maybe we could get a sticky put up so the same subject is not raised
in a slightly different form every few days.
If you have a look at the above thread it is nearly two years old and if
you look in launchpad this problem has been reported many times.
The reason I had never had this problem before is that I had only
burned CD's it was only when I burned DVD's that I noticed the problem.

Cheers
Sandy

---

### Post by dsimpson on 2008-01-23
I am wondering if any of the Developers ever look at these issues, if they do, I think this problem should go to the top of the list of items to be resolved by the release of the next Distro.  In the meantime, I guess we keep trying to find a fix to our problems as they pertain to our individual systems. I see more and more related issues each day on these forums with very few resolved. Here's hoping we will find an answer!!:(:(:(

---

### Post by Nebutron on 2008-01-26
> **dsimpson said:**
> I am wondering if any of the Developers ever look at these issues, if they do, I think this problem should go to the top of the list of items to be resolved by the release of the next Distro.  In the meantime, I guess we keep trying to find a fix to our problems as they pertain to our individual systems. I see more and more related issues each day on these forums with very few resolved. Here's hoping we will find an answer!!:(:(:(

I know you are still hoping to resolve this without new hardware, but if it turns out you need I new drive, I would recommend ordering through Newegg.com.  Saves you the trip to the computer store and will probably be cheaper.  Good luck!:)

---

### Post by Zuuswa on 2008-01-26
I've had the same problem with my drive since before dapper, It won't read any dvds, it will read most cds and will burn a cd, but nothing else.  After as much testing as described here, and more, I stand resolved that its a hardware problem.  I know how you hate to hear it, but yours is probably the same situation.  There are alot of bunk dvd drives out there from what I hear.

---

### Post by sanddgroper on 2008-01-26
> **Zuuswa said:**
> I've had the same problem with my drive since before dapper, It won't read any dvds, it will read most cds and will burn a cd, but nothing else.  After as much testing as described here, and more, I stand resolved that its a hardware problem.  I know how you hate to hear it, but yours is probably the same situation.  There are alot of bunk dvd drives out there from what I hear.
You maybe right but if I was to have a guess I would say it is the way linux is writing to the DVD's.As I have said on other posts on this subject I have 3 versions of Ubuntu and each handle home burnt DVD's differently on the same hardware.An interesting thing I have noticed on 7.04 and 7.10 when you insert home burnt DVD's in the drive the drive icon disappears in Places>Computer and the only way to get it back is to reboot the computer or insert a commercial DVD in the drive.I also get a lot of drive not ready warnings in dmesg and syslog when using home burnt DVD's.
My question is why does the same hardware have no problems with commercial DVD's or
any CD's but only with linux burnt DVD's.I have also noticed this problem is not confined to Ubuntu.Other distro's are suffering the same problem.The thing is the problem is not affecting the great majority or it would have been fixed two odd years ago when it first appeared.
Anyway I have a new DVD rw I might put in the machine and see if that changes anything.

Cheers
Sandy

---

### Post by dsimpson on 2008-01-27
I see that for a quick fix, the common answer is to purchase a new dvd driver. If that is the only way to remedy the problem, how long will the problem be resolved before we again have to replace that with another, I think the best solution would be to find the error, fix it to work in all versions of ubuntu or if necessary, Linux and then we could play video's in the same manner that owners of Microsucks and Mac are able to apparently do. 
    Okay, if I am to buy a new dvd player, the question now becomes, which one or ones are the best to work with Ubuntu? I certainly wouldn't want to buy one that wouldn't last with Ubuntu, now would I, so if there are some name brands that work please let me know.
    For Sandgroper, I hope you find the answer in your replacement, if you do, let me know and I will try that route also. I am also unable to open cd that I have burned, but commercial ones won't work also, except for the audio ones, that is all I can get out of my player is music.

---

### Post by sanddgroper on 2008-01-28
Hi dsimpson

Well I fitted the new PIONEER DVD-RW DVR-115D and lo and behold the DVD's I had burnt with
 the LG HL-DT-ST DVDRAM GSA-4163B mounted normally in both 7.04 and 7.10,havn't tried
6.06 yet,but then I tried to burn a DVD with K3b on 7.04 and it crashed with an error then I
tried on the 7.10 version and the burn finished successfully but was very slow,write speed
between 1.0X and 2.0X.There is reports of slow write speeds so I guess I need to read up
on them.
So it seems we are back were we started.
It can be a hardware problem(one reads but won't write(on 7.04) and on writes but won't read).
It could be software(K3b or DVDtools).LG works with K3b but the pioneer not so well.
It could be Ubuntu.As I get different results on three different versions
Or a combination of all of the above.
So dsimpson if I was you I would have a shop around some of your mates and see what
DVD rw's they are using.If you can only get music out of your drive I think you have a bigger
problem than I do.But before you go out and actually  buy another drive I would see if I could find one that works with your system.But as you said it might break on the next
version.

Cheers
Sandy

---

### Post by dsimpson on 2008-01-28
Thank you for the post Sandy, I guess I will go and shop for a new dvd drive next weekend, I am 120 miles from the nearest compusa which is the best place for me to buy one. So glad you are having positive results now but if anything happens similar to what we have been discussing then feel free to repost on this issue. Duane

---

### Post by Nebutron on 2008-01-28
> **dsimpson said:**
> Thank you for the post Sandy, I guess I will go and shop for a new dvd drive next weekend, I am 120 miles from the nearest compusa which is the best place for me to buy one. So glad you are having positive results now but if anything happens similar to what we have been discussing then feel free to repost on this issue. Duane

dSimpson.  I see that you have tried a lot of various fixes with no success yet.  I have read in a couple of places that the xine player is better than totem.  Don't know if you have tried it.  For my system, I uninstalled all other movie players, installed xine, and then went to the medibuntu site and followed the directions to add the respository and install libdvdcss2.  Everything worked for me after that.  Hope you find your answer.  Good luck!:)

---

### Post by dsimpson on 2008-01-28
Hi Nebutron,
    I am willing to try that, is it xine under Totem player? I have tried VLC, Qxine, Helix, Mplayer, and Xine with no luck, I have no problem trying out your suggestion though. If this works it will be worth it. You said you went to the medibuntu site and installed all the repositories, does that mean that you uninstalled all the codecs before you went to medibuntu or just reinstalled them all. I get the message that all codecs are the current codecs and I was wondering if I should remove then add these also or go with what I have on now? Or do they need to be added after the Xine player is installed?

---

### Post by Nebutron on 2008-01-28
> **dsimpson said:**
> Hi Nebutron,
    I am willing to try that, is it xine under Totem player? I have tried VLC, Qxine, Helix, Mplayer, and Xine with no luck, I have no problem trying out your suggestion though. If this works it will be worth it. You said you went to the medibuntu site and installed all the repositories, does that mean that you uninstalled all the codecs before you went to medibuntu or just reinstalled them all. I get the message that all codecs are the current codecs and I was wondering if I should remove then add these also or go with what I have on now? Or do they need to be added after the Xine player is installed?

I installed just Xine by itself.  No totem.  Don't know if it will make a difference.  I know you are really grasping at straws here and suspect this may not make the difference for you.  But, like you said, it's worth a try.  Attached instructions for what I did in case that saves you any trouble.  Again, good luck!  [ATTACH]57893[/ATTACH]

---

### Post by Talako on 2008-01-28
Well, after a day of hardware fiddling/upgrading and OS upgrading (64 bit 7.10 oorah!), I have found that my DVD drive is shot, for whatever reason, they play just fine in my DVD writer drive, but aren't even recognized in the DVD reader drive, only CDs work in that drive, and those sporadically. Seems like the hardware is indeed the problem, sorry I can't bring better news.
Talako

---

### Post by dsimpson on 2008-01-29
Nebutron - I tried your suggestion and still something isn't right. I am posting the errors I got when I went to medibuntu and downloaded the codecs.

Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy/free Packages                           

  302 Found

Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy/non-free Packages                       

  302 Found

Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy/free Sources                            

  302 Found

Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy/non-free Sources                        

  302 Found

Fetched 333kB in 18s (17.7kB/s)

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/gutsy/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/gutsy/free/binary-i386/Packages.gz)  302 Found

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/binary-i386/Packages.gz)  302 Found

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/gutsy/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/gutsy/free/source/Sources.gz)  302 Found


Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/source/Sources.gz)  302 Found

Reading package lists... Done

W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_gutsy_free_binary-i386_Packages)

W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_gutsy_non-free_binary-i386_Packages)

W: You may want to run apt-get update to correct these problems

E: Some index files failed to download, they have been ignored, or old ones used instead.


Also on the  libdvdcss2
; I got this message,  about no longer required  packages.

sudo apt-get install libdvdcss2

Reading package lists... Done

Building dependency tree       

Reading state information... Done

libdvdcss2 is already the newest version.

The following packages were automatically installed and are no longer required:

  libdc1394-13 libwxgtk2.6-0 libsvga1 libdvbpsi4 libavformat1d libxosd2

  libvlc0 libggi2 libgii1 libwxbase2.6-0 zlib1g-dev libfreetype6-dev

  libgii1-target-x libiso9660-4 libmozjs0d libslang2-dev libtar libvcdinfo0

  libebml0 libmatroska0 libsdl-image1.2 libungif4g

Use 'apt-get autoremove' to remove them.

0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.


Any ideas as to the relevancy of the errors and installed packages?

Finally, when I try  to open Xine to  view the dvd I get this message.

-xine engine error-

there is no input plugin available to handle dvd:/
maybe MRL syntax is wrong or file/stream source doesn't exist

and; in another box this error message

the source can't be read
 maybe you don't have enough rights for this, or source doesn't
contain data (e.g: not disc in drive) . (/dev/dvd)

All of this also affects the cursor, it hangs up and when I move it around the screen it will move sometimes and sometimes not, so there is resources being used that affects more then just Xine. Any ideas or suggestions on what is going on and what I can do to fix this problem? 

When I go to Places/computer/cdrom/dvdrom I get the following message;
And: also the disc doesn't autoload. 

Unable to mount media. There is probably no media in the drive.

It seems that I am back to square one again, pleading for help with my problem! LOL!:-k

---

### Post by sanddgroper on 2008-01-29
Hi dsimpson
From what I understand you can't play any video at all and I dont know
what you have loaded on your system but if you have some non encrypted
video try to get that to play.If you can't get normal video to work all the codecs
in the world is not going to help.I use mplayer without much problem.
Just as a matter of interest can you see things like movie trailers on the net.
I maybe wrong but if you were missing codecs for xine I might have thought
it would say so but as I don't use xine I don't know.

Hope this helps

Cheers
Sandy

---

### Post by Nebutron on 2008-01-29
> **dsimpson said:**
> Nebutron - I tried your suggestion and still something isn't right. I am posting the errors I got when I went to medibuntu and downloaded the codecs.

Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy/free Packages                           

  302 Found

Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy/non-free Packages                       

  302 Found

Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy/free Sources                            

  302 Found

Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy/non-free Sources                        

  302 Found

Fetched 333kB in 18s (17.7kB/s)

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/gutsy/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/gutsy/free/binary-i386/Packages.gz)  302 Found

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/binary-i386/Packages.gz)  302 Found

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/gutsy/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/gutsy/free/source/Sources.gz)  302 Found


Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/source/Sources.gz)  302 Found

Reading package lists... Done

W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_gutsy_free_binary-i386_Packages)

W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_gutsy_non-free_binary-i386_Packages)

W: You may want to run apt-get update to correct these problems

E: Some index files failed to download, they have been ignored, or old ones used instead.


Also on the  libdvdcss2
; I got this message,  about no longer required  packages.

sudo apt-get install libdvdcss2

libdvdcss2 is already the newest version.

The following packages were automatically installed and are no longer required:

  libdc1394-13 libwxgtk2.6-0 libsvga1 libdvbpsi4 libavformat1d libxosd2

  libvlc0 libggi2 libgii1 libwxbase2.6-0 zlib1g-dev libfreetype6-dev

  libgii1-target-x libiso9660-4 libmozjs0d libslang2-dev libtar libvcdinfo0

  libebml0 libmatroska0 libsdl-image1.2 libungif4g

Use 'apt-get autoremove' to remove them.

0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.


Any ideas as to the relevancy of the errors and installed packages?

Finally, when I try  to open Xine to  view the dvd I get this message.

-xine engine error-

there is no input plugin available to handle dvd:/
maybe MRL syntax is wrong or file/stream source doesn't exist

and; in another box this error message

the source can't be read
 maybe you don't have enough rights for this, or source doesn't
contain data (e.g: not disc in drive) . (/dev/dvd)

All of this also affects the cursor, it hangs up and when I move it around the screen it will move sometimes and sometimes not, so there is resources being used that affects more then just Xine. Any ideas or suggestions on what is going on and what I can do to fix this problem? 

When I go to Places/computer/cdrom/dvdrom I get the following message;
And: also the disc doesn't autoload. 

Unable to mount media. There is probably no media in the drive.

It seems that I am back to square one again, pleading for help with my problem! LOL!:-k

Well,  this is probably beyond my level of knowledge.  I find a couple of things interesting though about this which I suspect you have already thought about.  The repository is failing to load due to errors.  Don't know what the "302 found" means.  Also with the packages no longer needed, I wonder if the "not needed" packages are causing a conflict with the new packages you are trying to use.  Thirdly, the failure to mount disc message seems to again point to a hardware issue.  Sorry no firm answers here.  My approach (not really the best) would be to do a fresh install to get rid of all the junk and start fresh.  If I come across any additional info, will pass it on.  Again, good luck!

---

### Post by dsimpson on 2008-01-29
Okay, here is where I am now. 

Did the suggested apt-get autoremove of the packages that were no longer needed.
Removed all video players, reinstalled VLC. Chose VLC because most posts on this forum seem to suggest it is the best for video, and also the fact that it doesn't cause my system to freeze up during use, as it did trying Xine.    Still no play - message -  "No MRL"
What the heck is an "MRL" and how does one go about installing the needed item to get your video to play?


Answer for sandgroper - as far as streaming video, I have no problem, I can view video on the net, movie streamers, youtube etc. without problems, just nothing from either my cdrw or dvd players.

The absolute last option, and one that I am not considering yet, is the complete fresh install, simply because I have pictures on my computer and data that is not yet saved to cd, AND not being able to open my cdrw or dvd players, I cannot save them and I don't want to lose them, so it will be the absolute last thing I will consider for now. If I do a fresh install then all my data on my harddrive will be lost.

---

### Post by sanddgroper on 2008-01-29
Hi dsimpson
Have you got a live disk that you can boot off. That should give you a chance
of seeing if you can play a DVD using a different OS without having to reinstall
your hard disk.
Also could you tell me if you can play the Experience Ubuntu.ogg file that is in thr
Examples folder inside your Home folder. You should be able to play this with the
base system.

Cheers
Sandy

---

### Post by dsimpson on 2008-01-30
Booted off the live cd ok, able to play the ogg file without any problems.

Why would I be able to boot from a cd and have a functional live cd but not be able to boot any other media when I am operating out of Gutsy?

---

### Post by sanddgroper on 2008-01-30
Hi dsimpson
Ok now you can boot off a live CD can you get any video to run from the DVD
while using the live disk.
I am correct that you have a CD and a separate DVD player in the machine?.
What I am trying to say is boot off the live CD in the CD player and then try to
put a video disk in the DVD player.

Cheers
Sandy

---

### Post by dsimpson on 2008-01-30
Tried that, no change, it gave me the same message about "Unable to mount media"," there is probably no media in the drive". :confused:

---

### Post by Nebutron on 2008-01-30
> The absolute last option, and one that I am not considering yet, is the complete fresh install, simply because I have pictures on my computer and data that is not yet saved to cd, AND not being able to open my cdrw or dvd players, I cannot save them and I don't want to lose them, so it will be the absolute last thing I will consider for now. If I do a fresh install then all my data on my harddrive will be lost.

Just a thought about your pics and data you want to keep.  If you have or can borrow a flash drive, that would do it.  Or, you can email the pics (probably only a couple at a time) to yourself and open after your fresh install.........if it comes to that.

---

### Post by sanddgroper on 2008-01-30
Hi dsimpson
Ok when you boot off the live CD(I presume it is 7.10) can you run the
file I mentioned above that is in the Examples folder on your live CD
Desktop.Also can you boot off both the CD and DVD drives.If so can you
boot off one drive and mount a CD(not DVD) with video on it in the other drive.
My guess would be you have a dud DVD drive.

Cheers
Sandy

---

### Post by dsimpson on 2008-01-30
thanks for the ideas, I tried to boot off both drives, can boot off the cdrw but not off the dvd player, so that may be the culprit. I can view the contents of the cd on the dvd though, so that is strange. and yes I was able to run the ogg file that is in examples. well, I guess I am off to buy a new dvd soon, as soon as the snow stops and it is safe to travel again. in the meantime I will try to save my pictures and data to a flash drive if nothing changes. Again thanks for all the help.

---

### Post by dsimpson on 2008-02-04
I finally got out of the mountains and to town to buy a new dvd player and hooked it up and now am ready to close this thread. Thanks to Mc4man, Sandgroper, nebutron, and others who posted to this thread to help me with my problems. It was after all the drive I had in that was the issue, a new one was needed and now is working. Thanks all!!!

---

### Post by Nebutron on 2008-02-04
Glad to hear you are back in business with DVD's.  :)

---

### Post by sanddgroper on 2008-02-05
Hi dsimpson

Glad it all worked for you.Still think there is unresolved issues with DVD's

Cheers
Sandy

---

### Post by Doc Guitar on 2008-07-17
Hello, I have been reading this thread hopeing to find an answer to my DVD wont play problem, to no avail. My DVD player plays audio OK but when I insert a full length DVD I get the message "No disc in drive E". When I insert a DVD with multiple episodes of say a TV programme it plays fine. The DVD's that I am trying to play are commercial DVD's of the Poirot TV programmes. 5 episodes OK, 4 episodes OK, 3 episodes OK, 2 and 1 episode, No disc in drive E.
Heeeeelp.

---

