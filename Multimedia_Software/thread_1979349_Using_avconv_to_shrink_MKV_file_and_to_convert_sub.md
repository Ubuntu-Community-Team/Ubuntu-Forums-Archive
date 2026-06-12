---
title: "Using avconv to shrink MKV file and to convert subtitles"
date: 2012-05-13
forum: Multimedia Software
---

### Post by timov on 2012-05-13
Hi all,

I have a large selection of .mkv files that I want to shrink down a bit (don't need full DVD quality for some of the stuff I have).

I can split the files into their component arts (video, audio and subtitles), but I'm having issues reducing the video donw, and I'm confused how to use avconv to do so.

The subtitle files are in DVDsub format, but I need them in another format, however when I use avconv, it tells me it can't find  suitable output file.

Can anyone point me in the right direction so I can start sorting my files?

thanx

---

### Post by shantiq on 2012-05-13
use [**handbrake**]("http://handbrake.fr/downloads.php") for this task [avconv possibly not best tool for this]

it will do all of this .....   change bitrate on video to change size of file see image below   [mkv or mp4]


[ATTACH]217862[/ATTACH]

---

### Post by flemur13013 on 2012-05-13
Or try "avidemux" - it's in the repositories.

---

### Post by timov on 2012-05-13
As the box is headless, handbrake becomes a bit of a pain. Also all my latest attempts with handbrake, have resulted in media my Android devices refuse to play (and I've tried every combination possible there!)

The man pages for avidemux show there isn't an option to sort the subtitles :-(, but I'll give it a play to see if I can get my MKVs a bit smaller.

thanx

---

### Post by Prescilla on 2012-05-13
Yes avidemux. It's easy to use.
I've been using it to convert mkv and mp4s with x264/.h264 codecs.
So can also hardcode the subtitles, crop, rescale, and remove unwanted frames of the video.

---

