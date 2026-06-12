---
title: "Can't get Xine to play dvds"
date: 2008-07-19
forum: Mythbuntu
---

### Post by Meph1st0 on 2008-07-19
I used to use Xine as my dvd player in 7.10.  Haven't been able to get it to work correctly since I upgraded to 8.04.  I'm using the following command:

```
xine -pfhq --no-splash dvd:/
```

It will play the first title which is usually just the copywrite infringement message and then it'll just die and quit back to the frontend.

I ran that code in a terminal and I got the following messages:

```
jbrown@mythbuntu:~$ xine -pfhq --no-splash dvd:/
This is xine (X11 gui) - a free video player v0.99.6cvs.
(c) 2000-2007 The xine Team.
libdvdread: Using libdvdcss version 1.2.9 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000002be
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000d00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001c40ef
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001d154f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001e0694
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
libdvdread: Can't seek to block 1851623
libdvdread: Invalid IFO for title 2 (VTS_02_0.IFO).
xiTK received SIGSEGV signal, RIP.
Aborted
```

for some reason it can't go to the next title.  I've tried several different DVDs all of which work fine in a set top player as well as on my wife's laptop running windows.

Anybody got any ideas on what the dealio might be?

---

### Post by AusIV4 on 2008-07-19
Sounds like something may be wrong with libdvdcss. You might try re-installing it, especially if you're still running on a pre-upgrade version.

---

### Post by Meph1st0 on 2008-07-19
hmmm.  well that didn't do it for me. :(  I reinstalled it two different ways.  first I went to synaptic package manager and marked it for reinstallation.  That didn't seem to fix it and so then I went to the mythbuntu control center and unchecked the "Enable Medibuntu Proprietary Codec Support" as well as the all the other codecs; w32codecs, libdvdcss2, ffmpeg.  Clicked apply and waited for it to remove everything.  I then reselected it all again and clicked apply and it still did the same thing.  I got the same messages in my terminal when I ran it.

---

### Post by Meph1st0 on 2008-07-19
Well I think I might have solved it.  I had two DVD drives in my computer.  What I did is I created a sybolic link in my dev directory to point /dev/dvd to /dev/scd1.  Before it was sect to point /dev/dvd to /dev/scd0.  Using my other dvd drive appears to be fix it.  So it seems my other dvd drive is bad.  Which is kind of crappy since it's supposed to be like 100 times better than the other one....,....and I paid a lot for it.

Anyway, thanks for your help.

---

### Post by Meph1st0 on 2008-08-01
OKay, so I take this back.  It's still not working very well at all.  I haven't watched a full length DVD movie yet.  Every movie I try to watch will play for a while but then crap out.  It's at different times.  It seems that the either DVD drive is far too stringent on disk flaws or something.  I'm just assuming here but, I'm wondering if it comes accross the very first scratch on the disk and then just gives up.

I find it hard to believe that both of my dvd drives are bad.  One thing I did notice yesterday is that in Mythbuntu control center I had MythArchive unchecked.  I rechecked it and I've found that importing DVDs is working better but playing DVDs still sucks.  Is there anyone else having this problem?  Or unreliable DVD play?

---

### Post by ahood on 2008-08-01
I recently was working on a friends mythbuntu system and had trouble playing DVD's using Xine. I had a hard time figuring out which device in /dev to point xine to....

We solved the problem by launching the program VLC. VLC was able to play a DVD, which told us that the DVD player and system is working. 

Near the bottom of the VLC screen is the path of the device that VLC uses to play the dvd. It was something like dvd:///dev/sdc0

We took that as a clue to use for xine. So, we used the dvd:///dev/sdc0 for xine and xine was able to play DVD's. 

> xine -pfhq --no-splash dvd:///dev/sdc0

I am certain that the path will be different for your system, but I might try playing the DVD with VLC and then using the path that VLC uses with the Xine application.

I hope this tip works for you.

With kind regards,

Al

---

