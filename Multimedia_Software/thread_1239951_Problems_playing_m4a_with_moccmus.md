---
title: "Problems playing m4a with moc/cmus"
date: 2009-08-14
forum: Multimedia Software
---

### Post by thebrian on 2009-08-14
I am running jaunty and have a bunch of music files in m4a format. I tried playing them in moc with no luck. They show up in the player but when i hit play, it skips right through them to the next song. No sound. I have the moc-ffmpeg-plugin installed.

Determined to find a console music player that works with m4a, i tried cmus. I also cannot get it to work. the files don't even show up in the browser, even in file-browser mode. i have libmp4v2 and libfaad installed.

any help is greatly appreciated. thank you!

---

### Post by matthewbpt on 2009-08-14
m4a files work great for me in Rhythmbox, Amarok, Totem, vlc ... though m4a is just a container, it usually contains the aac codec, but maybe yours is different, are these downloaded from the iTunes store?

---

### Post by thebrian on 2009-08-14
no they aren't itunes. i was running crunchbang 8.10 and using moc on that, and it played the files fine. but i decided to switch to jaunty and stopped working.

and they play fine in rhythmbox, so i really have no clue.

---

### Post by matthewbpt on 2009-08-14
I tried installing moc and all the relevant packages, ffmpeg, moc-ffmpeg-plugin etc but like you it didn't work, I can see the m4a files but when it tried to play them it says "Can't get decoder for /my/m4a/file.m4a" . So it doesn't seem to support the aac codec. Googling I found this page [http://moc.daper.net/node/255](http://moc.daper.net/node/255) it says that debians ffmpeg is compiled with aac disabled, maybe this is the case in ubuntu too?

---

### Post by thebrian on 2009-08-14
i don't know. it's frustrating because it worked in crucheee (ubuntu 8.10).

at first it gave me the "decoder" error, but if i did a "killall mocp," there was no error, but it just plays through the files as if they were 0 seconds long.

---

### Post by thebrian on 2009-08-16
i've decided it's a pulse audio issue. i downgraded to 8.10 and it works great.

---

### Post by noffle on 2009-10-01
Does anyone know if m4a's work in Karmic through moc and cmus?

---

### Post by amx401 on 2011-01-05
Is there a way to "fix" cmus so that it plays m4a files?  For some odd reason, it's my favorite media player.

Thank you.

---

### Post by BicyclerBoy on 2011-01-05
cmus has dependencies on some ffmpeg dynamic loaded libraries.

AAC decode is non-free.

These (7) of so ffmpeg libraries (libavformat etc)are stripped in standard *buntu.

Install ubuntu-restricted-extras
add medibuntu repository.
install libavformat-extra52   avutil  avcodec avdevice     etc   etc...

This should fix the AAC codec problem.

---

### Post by Junkieman on 2011-03-04
Same problem here. I added the Medibuntu repo, and installed libavformat-extra52 without any success. 

I did compiled cmus myself, and that m4a support probably needs to be configured in.

Does anybody know how if this is the case? Or how I can fix this? :confused:

---

