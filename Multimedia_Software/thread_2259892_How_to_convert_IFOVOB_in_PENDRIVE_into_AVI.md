---
title: "How to convert IFO/VOB in PENDRIVE into AVI"
date: 2015-01-07
forum: Multimedia Software
---

### Post by rmlazzari on 2015-01-07
Hi, this is my first post in this forum, so... my name is Renato and I'm a 56 y.o. brazilian guy just arriving from Windows to Ubuntu 14.04.):P


I have a pendrive (or flash drive) with the follow folder structure:

Showname1/VIDEO_TS/(some IFO and BUF files)
Showname2/VIDEO_TS/(others IFO and BUP files but the same names as the previous)

I'd like to convert these files into just 2 files: Showname1.avi and Showname2.avi.

After a search, I've installed Acid DVD Ripper, as it seems to me as a graphic interface to MEncoder. But using this Acid I didn't find a way to navigate to the pendrive. I've tryied to paste the address "/media/renato/PENDRIVE/Home for Christmas/VIDEO_TS/VIDEO_TS.VOB" in the field "Path" (default /dev/dvd) but the program can't find the VOB files.

Some questions:

1 - Is that Acid Ripper the program I need to do this convertion? If yes, can somebody help me using it? If not, what is the adequate for do this conversion?

2 - With that Acid do I have to convert one by one the VOB files? But what to do to join the AVIs? Is there a program tha "understand" the files have an order, exclude the menus and convert only the movie?

Thanks!

---

### Post by TheFu on 2015-01-09
Remove the spaces in the path as a first fix.  Also - copy the files off the flash drive onto faster media. Slow media will make the transcoding painfully slow.

If you can live with mp4/h.264 video, **handbrake** is much easier.  Lots of youtube videos for using it, but you probably don't need any. It is that simple.
Otherwise, I don't have any recommendations for transcoding with any GUI tools. Back when I used AVI and xvid for codecs, I did it all with mencoder or ffmpeg.  These days, internet media is h.264/aac and handbrake makes it easy.

Oh - I see you don't want the menus?  Use **vobcopy** to only copy the part you want to the HDD.  Lots of how-tos for that program too.

---

