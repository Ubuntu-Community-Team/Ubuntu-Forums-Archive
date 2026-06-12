---
title: "Converting mythtv nuv files to avi? (Lucid)"
date: 2011-08-17
forum: Multimedia Software
---

### Post by pdwerryhouse on 2011-08-17
Hi all,

What's the accepted method for converting Mythtv's nuv files to avi files now?

I ask this because nuvexport seems to be unsupported these days. The last released version removed support for using transcode to convert the files. This leaves only mencoder and ffmpeg, and these have the following problems:

1) mencoder is much, much too slow. It takes about five times as long to convert a file as transcode ever did.
2) Ubuntu's ffmpeg is crippled, and doesn't work. I realise that there are instructions for installing a version of ffmpeg that works, but as this does not provide any method for creating Debian packages of it, I do not wish to pollute my filesystem with a mish-mash of manually installed software.

Is there any way to convert nuv files with transcode?

Thanks.

---

### Post by pdwerryhouse on 2011-08-22
Ok, for what it's worth, I've started using handbrake to convert files. It's faster than anything else I've encountered.

---

### Post by BicyclerBoy on 2011-08-22
I didn't think MythTV uses nuv nupplevideo for anything..?
Recordings are commonly mpeg2-ts encoded with mpeg2 or mpeg4/10 H264.

MythTV 0.24 comes with mythffmpeg, which does work.

Don't put any H264 video, or anything for that matter, into avi container.

---

### Post by 4partee on 2011-08-22
> **BicyclerBoy said:**
> I didn't think MythTV uses nuv nupplevideo for anything..?
Recordings are commonly mpeg2-ts encoded with mpeg2 or mpeg4/10 H264.


Really!
$ ls -lh /var/lib/mythtv/recordings/*.nuv
-rw-r--r-- 1 mythtv mythtv 2.5G 2011-08-21 06:00 /var/lib/mythtv/recordings/7033_20110821050000.nuv
-rw-r--r-- 1 mythtv mythtv 2.7G 2011-08-21 07:00 /var/lib/mythtv/recordings/7033_20110821060000.nuv
-rw-r--r-- 1 mythtv mythtv 2.6G 2011-08-21 08:00 /var/lib/mythtv/recordings/7033_20110821070000.nuv
-rw-r--r-- 1 mythtv mythtv 2.5G 2011-08-18 21:00 /var/lib/mythtv/recordings/7034_20110818200000.nuv
-rw-r--r-- 1 mythtv mythtv 2.5G 2011-08-18 22:00 /var/lib/mythtv/recordings/7034_20110818210000.nuv
-rw-r--r-- 1 mythtv mythtv 2.6G 2011-08-18 23:00 /var/lib/mythtv/recordings/7034_20110818220000.nuv
-rw-r--r-- 1 mythtv mythtv 103M 2011-08-22 17:02 /var/lib/mythtv/recordings/7034_20110822170000.nuv
-rw-r--r-- 1 mythtv mythtv 1.9G 2011-08-20 09:30 /var/lib/mythtv/recordings/7044_20110820090000.nuv
-rw-r--r-- 1 mythtv mythtv 1.8G 2011-08-20 10:00 /var/lib/mythtv/recordings/7044_20110820093000.nuv
-rw-r--r-- 1 mythtv mythtv 1.8G 2011-08-20 10:30 /var/lib/mythtv/recordings/7044_20110820100000.nuv
-rw-r--r-- 1 mythtv mythtv 1.8G 2011-08-20 11:00 /var/lib/mythtv/recordings/7044_20110820103000.nuv
-rw-r--r-- 1 mythtv mythtv 5.7G 2011-08-19 23:15 /var/lib/mythtv/recordings/7063_20110819210000.nuv
-rw-r--r-- 1 mythtv mythtv 6.6G 2011-08-21 19:00 /var/lib/mythtv/recordings/7063_20110821163000.nuv
-rw-r--r-- 1 mythtv mythtv 6.2G 2011-08-22 01:15 /var/lib/mythtv/recordings/7063_20110821233000.nuv
-rw-r--r-- 1 mythtv mythtv 4.4G 2011-08-22 06:30 /var/lib/mythtv/recordings/7063_20110822050000.nuv

---

### Post by BicyclerBoy on 2011-08-23
Sorry should have said:
I didn't think MythTV uses nuv nupplevideo for anything..except for software encoded capture cards.

[http://www.mythtv.org/wiki/Unofficial_Plugins](http://www.mythtv.org/wiki/Unofficial_Plugins)

nuv2avi
avi files suffer badly from a/v sync etc.

---

### Post by 4partee on 2011-09-06
> **BicyclerBoy said:**
> http://www.mythtv.org/wiki/Unofficial_Plugins[/url]

nuv2avi
avi files suffer badly from a/v sync etc.

Yep.  I had just re-started with Mythbuntu and had dragged an old card off the shelf.  You are so right re the a/v sync.  It is like watching an old Godzilla movie with English.

I bought some pvr-150 cards off fleabay.

---

