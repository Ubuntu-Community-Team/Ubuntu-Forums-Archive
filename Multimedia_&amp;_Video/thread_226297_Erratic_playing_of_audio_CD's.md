---
title: "Erratic playing of audio CD's"
date: 2006-07-31
forum: Multimedia &amp; Video
---

### Post by oblivious on 2006-07-31
Hello,

 I have a problem when attempting to play audio CD's: The playing starts, but the sound pauses every couple of seconds while the drive struggles to read, like it is too slow to read audio data.

 The problem seems to be player-independent, Xfmedia, Mplayer and Goobox all suffer from this. When attempting to encode an audio CD to OGG for example using Goobox, the drive stops responding while apparently reading continuously.

 All the rest of the drive functions are ok. I can read data, audio and video files from data DVD's and CD's, can play DVD movies, but can't listen to nor encode from audio CD's.

 There's a tip on the forums somewhere to speed up the drive enabling DMA. I tried that and it didn't work.

 My system is a Toshiba Satellite laptop with a DVD-ROM drive (can't find the model number anywhere), and I'm running Xubuntu 6.06.

 Any help would be greatly appreciated. If there is any other information I need to supply, please ask.

 *Edit: The drive is a Toshiba DVD-ROM SD-C2402*

---

### Post by oblivious on 2006-08-10
*bump*

---

### Post by oblivious on 2006-08-11
Progress report...

 I started messing around with the options in cdparanoia, and I've managed to fix the encoding problem. There's a "-s" option to search exhaustively for a drive (it keeps searching even if it finds /dev/cdrom).

 Running this:

```
cdparanoia -vsQ
```

 (verbose, search and disc info) just once seems to have fixed the encoding problem, now cdparanoia runs smoothly even if I don't provide the "-s" option.

 I guess this should give some clues as to what might be causing the read problem. I've tried doing similar things with the command line players but nothing seems to work... any ideas?

 :confused:

---

### Post by oblivious on 2006-08-14
Installing Grip has solved the problem. It seems to interact with the drive better than any other program. Playing of audio CD's is now uninterrupted and encoding is a breeze. Highly recommended.

---

### Post by finferflu on 2006-08-15
Thanks for that! it's been useful.

I had the same problem and Grip has solved everything. 

I wonder why excellent players like VLC failed to do their job. I would like to know if there is any option I have to deal with, but there are so many options that I get very confused...

---

