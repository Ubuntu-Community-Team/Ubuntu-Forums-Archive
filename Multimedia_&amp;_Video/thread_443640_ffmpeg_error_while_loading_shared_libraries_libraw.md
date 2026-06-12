---
title: "ffmpeg: error while loading shared libraries: libraw1394.so.5: cannot open shared obj"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by applez on 2007-05-14
hey hey hey 

Yes this issue is a pain in the *** I am a linux noob but happy to be as I have discovered an awesome world with ubuntu but enough *** kissing.

This problem I came across since upgrading to the edgy eft not just for flv files but any 

Its a pain in the *** a lot of forums seem to have people talking about this problem but no one seems to have an answer apart from making ffmpeg yourself with different options.

The package ffmpeg is chasing libraw1394.so.5 is listed in synaptic but can u download it no no no its obsolete

Also  tovid fails as it waits for its audio.ac3 which it cant have because ffmpeg is to scared to look for libraw1394.so.8 

So checking google for an hour I find the only real answer is to make my own ffmpeg which looks quite heavy for a beginner  there is surely an easier option 

So I checked the folder where libraw1394.so.8 resides usr/lib I notice it says link to shared library 

I dont know what a link to a shared library is but I am now thinking what is I just copy the file and rename the copied file to libraw1394.so.5 

goto usr/lib in naughtylis pick view pick view as list find libraw1394.so.8, right click pick copy, pick view, pick  
right click on libraw1394.so.8 pick copy, pick view as icons, scroll down to bottom of list in space at bottom right right click and pick paste

it will paste a copy of libraw.1394.so.8 with copy in the title right click it pick rename, then in its box type libraw1394.so.5 
hit enter

run your prog that uses ffmpeg happy days!

therefore its linking to whatever its linking to it tricks ffmpeg into thinking its reading what it thinks its reading which encodes mah file and we can all go home early so I make a copy rename it and I think there is now way its going to work but fook me it did!
Yes I am elite and super cool or at least I feel like after pissing around for 2 hours but whahey lateral thinking pays dividends everyones happy bobs your aunties husband! jobs done see you next time for my next top tip.

---

