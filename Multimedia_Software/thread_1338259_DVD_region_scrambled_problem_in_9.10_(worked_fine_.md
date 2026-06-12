---
title: "DVD region scrambled problem in 9.10 (worked fine in 8.04)"
date: 2009-11-26
forum: Multimedia Software
---

### Post by ItalOz on 2009-11-26
Hi all,
I just installed 9.10 on a USB disk to check if everything was working ok.
Most of it does but I cannot play a DVD from another region anymore, the video looks scrambled. It was like this once in 8.04 than I fixed it.

I still have my previous 8.04 installation in the disk, so I checked and the DVD plays beautiful with VLC.

I somehow managed to make it work for 8.04 and I have tried to replicate the procedure for 9.10 by following [[COLOR="Blue"]this guide[/COLOR]]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

I think I have installed all the restricted drivers and stuff,
Anyone can give me a hand on where and what to check? Because I figure that if it works in 8.04 I cannot be that far from having it working in 9.10

Thanks

EDIT

I've run and re-run all the commands thousand times, nothing, I have installed gxine and by running it tells me
libdvdread: Using libdvdcss version 1.2.10 for DVD access
[..]
libdvdnav: DVD disk reports itself with Region mask 0x00f70000. Regions: 4
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.

libdvdread: Attempting to retrieve all CSS keys
[..]

and then I get a window with the message:
"Media stream scrambled/encrypted"

---

### Post by ItalOz on 2009-11-26
I have booted into the old 8.04 and run vlc from terminal to get all the messages, with 8.04 it works fine and says

```
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: StrangerThanFiction
libdvdnav: DVD Serial Number: c9cf5299        
libdvdnav: DVD Title (Alternative): StrangerThanFiction
libdvdnav: Unable to find map file '/home/fabrizio/.dvdnav/StrangerThanFiction.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f70000. Regions: 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000144
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00012d73
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000335cd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00267526
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0026752f
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
[00000344] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:224000
[00000376] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
```

then I tried with 9.10 and I get the scrambled video with the following message

```
VLC media player 1.0.2 Goldeneye
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: StrangerThanFiction
libdvdnav: DVD Serial Number: c9cf5299        
libdvdnav: DVD Title (Alternative): StrangerThanFiction
libdvdnav: Unable to find map file '/home/fabrizio/.dvdnav/StrangerThanFiction.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f70000. Regions: 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000144
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00012d73
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000335cd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00267526
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0026752f
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
[0x7f3fa8003c18] main input error: ES_OUT_RESET_PCR called
[0x7f3fa8003c18] main input error: ES_OUT_RESET_PCR called
[0x7f3fa800cd78] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:224000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x2c653e8] pulse audio output: No. of Audio Channels: 2
[0x7f3fa8003c18] main input error: ES_OUT_RESET_PCR called
[0x29d5268] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x29d5268] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x7f3fa8003c18] main input error: ES_OUT_RESET_PCR called
[0x29d5268] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x29d5268] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x7f3fa8003c18] main input error: ES_OUT_RESET_PCR called
[0x7f3fa8003c18] main input error: ES_OUT_RESET_PCR called
[0x7f3fa800cd78] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
[0x2c653e8] pulse audio output: No. of Audio Channels: 6
[0x29d5268] libmpeg2 decoder error: invalid picture encountered
[0x29d5268] libmpeg2 decoder error: invalid picture encountered
fabrizio@Dell:~$ [0x29d5268] libmpeg2 decoder error: invalid picture encountered
[0x29d5268] libmpeg2 decoder error: invalid picture encountered
[0x29d5268] libmpeg2 decoder error: invalid picture encountered
[0x29d5268] libmpeg2 decoder error: invalid picture encountered
```

And it seems that I have all the latest releases of everything

Any idea anybody...:( please

---

### Post by ItalOz on 2009-12-01
bump! :confused:

---

### Post by mc4man on 2009-12-02
There's a small possibility that it's the structure protection on that title, which has a bit of a history.
( though I can open it here in vlc, a Region 1 

In the 8.04 I see your using a xine based player
>  Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
while in 9.10 your using 
> libdvdnav: Using dvdnav version 4.1.3
and seeing this from vlc, which the title does contain as part of the protection
> libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture

A couple of things to try...

You could try gxine again but first go in and delete the .dvdcss folder in your home folder. (hidden

If that doesn't work then open the .dvdcss folder and you'll see a folder inside ' Stranger_Than_Fiction.....'

Delete it and than copy the same folder from your 8.04 install and put it inside the 9.04 .dvdcss folder. Then try gxine again.

With the proper key folder in .dvdcss, try vlc again, but go Media -> Open Disk -> No Dvd Menus, then play.

---

### Post by ItalOz on 2009-12-02
Hey thanks for the answer,
:P
I'll try that as soon as I go home and I'll post the results

---

### Post by ItalOz on 2009-12-02
YOU ARE MY MAN!!!!

I just needed to delete the folder in the corresponding 
```
.dvdcss/
```
directory and when I launched back it worked like a charm.

So it looks like that folder was left there by the program when I launched and after I installed 9.10 and then when I updated the all thing it did not get cancelled

Thanks a lot I can mark this thread as solved :KS

but first let me say: Thumbs up Ubuntu!
because I tried so hard to view my DVDs under windows, this thing of the DVD zones obtained with me is that I will never again buy an original DVD, I happen to travel and I carry my laptop, I come from Europe and now I live in Australia, the alliance DVD distributors + windows + hardware producers don't want me to enjoy my DVDs with just one computer right? I should buy how many of them? And if I go to China for work I cannot rent or buy a DVD?

Sorry for that but how much energy to obtain such a poor result

---

### Post by mc4man on 2009-12-02
Just so you know the mechanism here

All unlicensed software players that use libdvdcss will first look in .dvdcss for a folder matching the volume label of the disk.

If found, then the keys inside will be used, even when incomplete or inaccurate, in which case playback or playback of some of the titles on the disk will fail.

Opensource, unlicensed players don't enforce region coding so for most titles with a region mismatch you should get playback.

In the rare case you can't, then acquiring the key folder for that title from an install that has the proper folder ( whether from cracking the keys better or having a matching region drive) and replacing will allow playback
.....................................

In this case you got corrupted or improper keys for some reason, removing the folder forced the player to re-aquire, which it did properly

---

### Post by ItalOz on 2009-12-03
well what can I say, clearer than that...

thanks again I'll make treasure of your comprehensive explanation

---

### Post by usererror on 2010-01-03
THANK YOU! Deleting ~/.dvdcss folder also worked for me!

I just did a fresh install of 9.10 after formatting my hard drive from 9.04 (I don't do in place upgrades, ever).

And dvd playback has been a pain for the last hour.

I verified I had all the dvd decoders, plugins, etc. tried changing my Region back to 1 with **regionset**, but i have NO IDEA why that would have been changed!  But still no dice.

Then googled for "libmpeg2 decoder error: invalid picture encountered" that I was seeing with VLC.  And found this post.

---

### Post by fbeleznay on 2010-01-10
Hi, I did what suggested in this thread and some of my DVD's work now, but I still have a problem that the system does not even recognize some others. When I put them in the DVD player, the DVD icon disappears from the file system and gxine cannot find it either. There is no entry for them in the .dvdcss directory. Can you suggest some solution?

---

