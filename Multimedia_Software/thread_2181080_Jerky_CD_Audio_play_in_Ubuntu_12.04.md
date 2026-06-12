---
title: "Jerky CD Audio play in Ubuntu 12.04"
date: 2013-10-16
forum: Multimedia Software
---

### Post by jeanbate on 2013-10-16
Hi,
after seraching google and this forum, I resolved to ask the community.
I have a problem with audio CD playing in Ubuntu 12.04.
When I insert the CD, and  try to play it in Rythmbox, the music starts and then plays in a jerky way, it is like watching a video stream with a slow connection : 12 s of music, 5 seconds of player excited, trying to figure what part of the CD goes next.
The problem does not seem to be hardware : I have a dual boot with Windows (urgh...) and it plays perfectly fine there.
When I try to play the CD with vlc, it is worse, the music simply never start.
When I navigate to the CD folder with Nautilus, I can very well copy paste the contents to my hard-drive, with a reasonnable speed.

So I don't get it : 
 - when I try to read 1x, the buffers gets filled in 5 s and music stops
 - when I read it full speed, no problem.

Can you guys help me?
That would be a treat, thanks.

PS : I am fairly used to unix command, but I don't know them all. So if you need further details, like the contents of a logfile, please specify the file's location.

---

### Post by andrew.46 on 2013-10-17
Try the following:

```

mplayer -cache 2048 -cache-min 80 cddb://

```

It might be interesting to see if this is trouble free on your system...

---

### Post by jeanbate on 2013-10-22
Thanks for the reply,

If I understand well, it tells mplayer to load 80 min of music in the cache.
In the first messages appearing, I have : 
```
Playing cddb://.
No cache found.
```

Loading the cache was burdensome, it took a little while, with many errors of the type :
```
Cache fill: 74.86% (1568784 bytes)   scsi_read error: sector=674 length=1 retry=0
                 Sense key: 3 ASC: 11 ASCQ: 5
                 Transport error: Medium reading data from medium
                 System error: Input/output error
```
at various sectors on the cd.
In the end, this message:
```
Cache not responding! [performance issue]

```
just before the mplayer audio decoder header.
No music, only 1s or so at the very beginning, and these messages :
```
scsi_read error: sector=744 length=1 retry=0% 
                 Sense key: 3 ASC: 11 ASCQ: 5
                 Transport error: Medium reading data from medium
                 System error: Input/output error
A:   9.4 (09.4) of 2142.4 (35:42.4)  0.0% 0% 
Cache empty, consider increasing -cache and/or -cache-min. [performance issue]
scsi_read error: sector=772 length=1 retry=0
                 Sense key: 3 ASC: 11 ASCQ: 5
                 Transport error: Medium reading data from medium
                 System error: Input/output error
scsi_read error: sector=772 length=1 retry=1
                 Sense key: 3 ASC: 11 ASCQ: 5
                 Transport error: Medium reading data from medium
                 System error: Input/output error
Cache empty, consider increasing -cache and/or -cache-min. [performance issue]
Cache empty, consider increasing -cache and/or -cache-min. [performance issue]
Cache empty, consider increasing -cache and/or -cache-min. [performance issue]

```
I then tried to increase the value of the cache size (not the cache-min) to 3072 (mplayer -cache 3072) and got a full 8s of music. Wouhou!!
Quite frustrating.
Any suggestion as to the result of this experiment?

---

### Post by Yellow Pasque on 2013-10-22
Make sure the drive's firmware is updated, and try a different cable or SATA port.

---

### Post by jeanbate on 2013-10-22
Unfortunately, the problem arises on a laptop, and it is not that easy to change the SATA port.
Anyway, it works perfectly fine when I boot Windows.

Concerning the driver firmware, I don't see no reason why it would be outdated.
I don't know how to check that, however.
If you can give me a hint as to how I can assert the driver status?

---

### Post by Yellow Pasque on 2013-10-23
> Concerning the driver firmware, I don't see no reason why it would be outdated.
I don't know how to check that, however.

```
sudo lshw -sanitize -C disk
```

---

### Post by jeanbate on 2013-10-23
Thanks!
Here is the output of lshw:
```
  *-cdrom
       description: DVD-RAM writer
       product: DVD RW AD-7580S
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: FX20
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
```

---

### Post by jeanbate on 2013-10-30
Any suggestion anyone?
Please :D

---

