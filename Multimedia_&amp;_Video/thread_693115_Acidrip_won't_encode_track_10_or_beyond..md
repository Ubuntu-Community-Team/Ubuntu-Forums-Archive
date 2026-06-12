---
title: "Acidrip won't encode track 10 or beyond."
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by Keith_Beef on 2008-02-10
I'm trying to rip some DVDs to play on a Cowon personal media player when we go on long trips.

These are DVDs I bought a while ago, and are episodes from children's TV programs from the 1970s.

Each disc has around 13 to 15 episodes.

Here are the instructions for mencoder that acidrip builds from the options I selected:

```
unlink frameno.avi 2> /dev/null
mencoder dvd://10 -dvd-device /dev/dvd1  -alang English   -info srcform="DVD ripped by acidrip.sf.net" -oac mp3lame -lameopts cbr:br=128  -ovc xvid -xvidencopts bitrate=487:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg:pass=1 -vf pp=de,crop=688:576:20:0,scale=325:-2    -o "/dev/null"
mencoder dvd://10 -dvd-device /dev/dvd1  -alang English   -info srcform="DVD ripped by acidrip.sf.net" -oac mp3lame -lameopts cbr:br=128  -ovc xvid -xvidencopts bitrate=487:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg:pass=2 -vf pp=de,crop=688:576:20:0,scale=325:-2    -o "/home/dvduser/Desktop/For_Cowon/trumpton_10.avi"
unlink divx2pass.log  2> /dev/null
eject /dev/dvd1 2> /dev/null
```

Acidrip will happily encode the first nine, but stops at the tenth with this message in the debug window:

```
AcidRip message - Encoding film, 1st pass...
MEncoder 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
There are 14 titles on this DVD.
There are 1 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: unknown aid: 128.
number of audio channels on disk: 1.
number of subtitles on disk: 0
success: format: 0  data: 0x22482800 - 0x4723c000
No matching DVD audio language found!
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...
AcidRip message - Clearing 3 remaining playlist items
AcidRip message - Mencoder interrupted by user
```


Any ideas why this is happening, of a workround?

K.

---

### Post by jenast on 2008-06-10
I also have this problem. However, the problem also pops up when I launch the mencoder script in terminal so it does not seem to be acidrip's fault. Same behaviour with mplayer. 

for example, with a dvd iso mounted at /media/temp :

 mplayer dvd://1 -dvd-device /media/temp -chapter 14-15

Does not play beyond chapter 14.

while

 mplayer dvd://1 -dvd-device /media/temp -chapter 3-5

plays chapter 3 through 5.

Is this a bug in mplayer/mencoder or is the syntax wrong?

/jenast

---

### Post by jenast on 2008-06-10
I realise we might have different issues after all. I was speaking about chapters within titles and breaking them up and encode to separate files. I had problems with double digit chapter names, at least the ending chapter. 
For instance, say your dvd has 15 chapters. "-chapter 10-15" does not work but "-chapter 10" does, meaning that it will play from chapter 10 to 15.

Still and strangely, for example "-chapter 3-4" works, meaning it will play chapter 3 and 4.

/Jenast

---

