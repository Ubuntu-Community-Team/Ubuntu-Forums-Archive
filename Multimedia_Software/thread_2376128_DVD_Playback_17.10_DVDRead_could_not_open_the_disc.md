---
title: "DVD Playback 17.10 DVDRead could not open the disc &quot;/dev/sr0&quot;."
date: 2017-10-30
forum: Multimedia Software
---

### Post by gingerbob on 2017-10-30
Hi,

I have developed a problem with my DVD playback.  It was working fine under 16.04, until it suddenly threw up crazy errors.  I tried the usual fixes and nothing, so have reinstalled with 17.10.

I have followed all of the usual instructions including installing
 libdvdread4 libdvdnav4 ubuntu-restricted-extras gstreamer1.0-ugly gstreamer1.0-bad libdvd-pkg

I have checked there is a symlink pointing /dev/dvd to /dev/sr0

I have run sudo dpkg-reconfigure libdvd-pkg

Nothing can see a DVD movie.  I have tried several different disks.  It can see Data DVDs (it allowed an install of Ubuntu!) and CDs.  As far as the system is concerned, there appears to be no disk in the drive despite there definitely being one.

lshw shows:
```
*-cdrom
             description: DVD-RAM writer
             product: DVD+-RW TS-T633C
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvd-old
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: D500
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
```
lsblk gives:
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0  83.1M  1 loop /snap/core/3247
loop1    7:1    0   115M  1 loop /snap/vlc/4
sda      8:0    0 298.1G  0 disk 
&#9500;&#9472;sda1   8:1    0  92.8G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9500;&#9472;sda3   8:3    0 201.4G  0 part /data
&#9492;&#9472;sda5   8:5    0     4G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom  
```
 Running $ dpkg -l | grep dvd    gives:
```
ii  libdvd-pkg                                 1.4.0-1-2                                   all          DVD-Video playing library - installer
ii  libdvdcss-dev:amd64                        1.4.0-1~local                               amd64        library for accessing encrypted DVDs - development files
ii  libdvdcss2:amd64                           1.4.0-1~local                               amd64        library for accessing encrypted DVDs
ii  libdvdnav4:amd64                           5.0.3-3                                     amd64        DVD navigation library
ii  libdvdread4:amd64                          5.0.3-2                                     amd64        library for reading DVDs
ii  lsdvd                                      0.17-1                                      amd64        read the content info of a DVD

```

Everything seems to be in place as far as I can see but no joy.  Every other thread I can find has not helped.  Please tell me you can!

Many thanks

gingerbob

---

### Post by mc4man on 2017-10-30
software (codec, libdvdcss2, ect) is irrelevant if the drive is being seen as empty.. hoping 17.10 would resolve wouldn't do much either.
Generally it would be a hardware error, the fact it can read data dvds is somewhat complicating that idea (but not completely discounting as it's possible commercial encrypted dvds need to be read at different position or level of lens resolution to be seen.

Have you tried multiple dvds?
Have you tried booting up with dvd in the drive?

If thinking 16.04.x itself caused initial issue then I'd try going backwards, 14.04.5 or initial [16.04.1 release]("http://old-releases.ubuntu.com/releases/16.04.1/"),  rather than forwards (17.10) to test that idea.

---

### Post by gingerbob on 2017-10-30
Thanks for your reply.

I have tried both multiple DVDs and booting up with the DVD in the drive.

It did work under 16.04 before until the other night.  I am reluctant to go back to previous versions unless I have to - the only reason I moved off the LTS version was to try to solve this problem.  I take your point about the potential differences between data and commercial DVDs but am somewhat skeptical.  Does anyone else have any ideas?

---

### Post by coldraven on 2017-11-01
> **gingerbob said:**
> Thanks for your reply.

 Does anyone else have any ideas?

Yes, clean the lens in the DVD drive. Even if it looks clean it may have a film of dirt on it or even just a cat hair. (if you have a cat!)
I once had three brand new DVD movies that would not play. After cleaning the lens two of them would play. I had to clean the lens again before the third one would play. 
If like me you smoke and have pets the lens will need a clean.

When cleaning **do not put any pressure on the lens**, it sits in a very delicate spring mount and can easily be broken. I just use a cotton bud with some methylated spirit on it and very carefully just drag the bud over the lens. You may also use spit (Spit contains dirt eating enzymes!) or maybe some variety of LCD screen cleaner.

---

