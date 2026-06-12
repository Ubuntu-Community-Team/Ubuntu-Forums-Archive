---
title: "Any ideas and howtos for ripping audio (mp3) from video clip?"
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by kazuya on 2006-07-27
Is there a way and how do I take a video and copy certain parts of its soundtracks or audio not the video into mp3?

I have heard of audacity and ardor and Rosengarden? Are these or are there some easy ways to rip the sounds off a movie clip to use for mp3 or sound file?

Any ideas and howtos for ripping or creating audio (mp3) from video clip?

---

### Post by whatever on 2006-07-27
mplayer -dumpaudio

---

### Post by kazuya on 2006-07-28
Isn' that the commandline>? Not bad, but how do I execute the command on a file in my home directory for example or from CD if the file name was genso.mpg stored in /home/oris/Desktop and I wanted to create an avi file from it.

Would I say :

mplayer -dumpaudio /home/oris/Desktop/genso.mpg

---

### Post by nbv4 on 2007-07-30
I'm trying to do this too but I'm having problems. I tried 

mplayer -dumpaudio [file]

but all it did was give me a file called "stream.dump" which none of my media players could play. (totem, amarok, audacity, mplayer, etc)

then I tried using VLC's transcoder found here: [http://www.edsupport.cc/mguhlin/blog/archives/2006/03/entry_1246.htm](http://www.edsupport.cc/mguhlin/blog/archives/2006/03/entry_1246.htm)

but the files it spat out couldn't be played by any of my media players either...

any other ideas?

---

### Post by momo07 on 2008-06-23
Bump

---

### Post by vambo on 2008-06-23
Try something along these lines in terminal.

 ```
mplayer <file_name> -ao pcm:file=%length_of_wav%out.wav -vc dummy -vo null
```

Where <file_name> is the video (or audio) file
The gottcha might be the %length_of_wav%out.wav bit
The output file name here is out.wav, which has 7 chars, hence here
the values would be %7%out.wav.
The -vc dummy and -vo null effectively disable video decoding.

The mplayer man page gives far more info.
Hope it helps.

---

