---
title: "locked drive plays all regions in 7.10"
date: 2009-05-08
forum: Multimedia Software
---

### Post by hanenming on 2009-05-08
I have expired the number of region changes allotted to me in windows (5) on my dual boot system; however, ubuntu still lets me play all regions of DVD.  Can anyone explain to me why if the firmware was locked on my DVD drive to region 1 that I am still able to play anything in ubuntu?

Of course, I am very happy about this, but I'd like to understand it.

I found the following thread, but that didn't offer a real explanation:

[http://ubuntuforums.org/archive/index.php/t-237111.html](http://ubuntuforums.org/archive/index.php/t-237111.html)

---

### Post by mc4man on 2009-05-08
That thread was right and not right.

It's all about aquiring the keys.

In linux  open source players (read unlicensed) use libdvdcss to acquire the keys and when there is a region mismatch will attempt using up to 3 different methods and usually are successful.

Factors that can come into play are the type of region coding on the disk and the drive itself.

Some drives, most notably matshita laptop drives, will not allow access to the drive if there is a region mismatch, in which case playback and or ripping is impossible. (with any Os ,app or prog

using vlc as an example, on a R4 with a R1 drive
In linux (clipped, red is mine

> 
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdcss debug: opening target `/dev/scd1'
libdvdcss debug: using libc for access
libdvdcss debug: disc is scrambled
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: [COLOR="Red"]authentication established  <- what matshita prevents[/COLOR]
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: decrypting disc key [COLOR="Blue"]xxxxxxxxx[/COLOR]
libdvdcss debug: trying player key [COLOR="Blue"]xxxxxxxxx[/COLOR]
libdvdcss debug: decrypted disc key is[COLOR="Blue"] xxxxxxxx[/COLOR]
libdvdcss debug: [COLOR="Red"]using CSS key cache dir: /home/doug/.dvdcss/HERO-2004121517021700-000004ea8f/  <- where the keys will be stored for future use[/COLOR]

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient


libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000032af
libdvdcss debug:[COLOR="Red"] getting title key at block 12975 the classic way[/COLOR]
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: [COLOR="Red"]ioctl ReadTitleKey failed (region mismatch?)[/COLOR]
libdvdcss debug: GetASF not authenticated, ASF=0
libdvdcss debug: lost ASF requesting title key
libdvdcss debug: [COLOR="Red"]resetting drive and cracking title key[/COLOR]
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: decrypting disc key [COLOR="Blue"]xxxxxxxx[/COLOR]
libdvdcss debug: trying player key [COLOR="Blue"]xxxxxxxx[/COLOR]
libdvdcss debug:[COLOR="Red"] decrypted disc key is xxxxxxxx[/COLOR]
libdvdcss debug: [COLOR="Red"]cracking title key at block 12975[/COLOR]
libdvdcss debug: successful attempts 1/1, scrambled blocks 2/5
libdvdcss debug: vts key initialized
libdvdcss debug: title key is [COLOR="Blue"]xxxxxxxx[/COLOR]
Ect., ect. .......

Now in windows on the same disc and drive vlc is unable to acquire the keys (maybe only tries 1 method, running progs on windows from command prompt is too much of a hassle to ck.
Also on a windows with a different disc (R2 this time) vlc can aquire the keys and will playback so the disc itself can be a factor.

If you still dual boot and have vlc on windows  you can test this and or give vlc the ability to playback all mismatches by copying the disc's folder containng the keys from /home/.dvdcss to the dvdcss folder in windows
( typically in documents and settings > your name > application data

---

