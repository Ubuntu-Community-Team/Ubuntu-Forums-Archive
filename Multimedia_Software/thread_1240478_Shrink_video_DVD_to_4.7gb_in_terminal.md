---
title: "Shrink video DVD to 4.7gb in terminal"
date: 2009-08-14
forum: Multimedia Software
---

### Post by Charlotte18 on 2009-08-14
I'm using the method described here to make ISOs of DVDs:

[http://johnbokma.com/mexit/2008/11/28/burning-vob-bup-ifo-to-dvd.html](http://johnbokma.com/mexit/2008/11/28/burning-vob-bup-ifo-to-dvd.html)

 The problem is that I want to make the ISO so that it will burn to a 4.7Gb DVD.

I know some gui software will do this (DeVeDe, etc.). I want to do it in the terminal.  How do I do this?

---

### Post by Charlotte18 on 2009-08-18
bump

---

### Post by ron999 on 2009-08-18
Hi
If you really want to use the command line then I think that the command you need to use is '**tcrequant**'.
But you'll have to research it yourself because I can't explain it to you, it involves arithmetic.

When I'm doing this job I use K9copy.

---

### Post by Charlotte18 on 2009-08-18
Thanks. You led me to what I wanted.  Here's a site that explains it all:

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/DVD9_to_DVD5_guide](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/DVD9_to_DVD5_guide)

---

### Post by ron999 on 2009-08-18
> 4) To requantize (shrink like DVDShrink on Windows) your movie so it will fit on a single DVD-R (4.7) do as such:

tcrequant -i movie.m2v -o shrink ed.m2v -f 1.5

The 1.5 at the end is the shrink factor if you like. 1 keeps the movie the same (just a reference) and 2.0 would reduce it to 50% of its size. So 1.5 seems reasonable as it equals 75% of the original size once processed.

If you prefer you can calculate the exact factor yourself with this formula:

requant_factor = (video_size / (4700000000 - audio_size)) * 1.04

If you are including more than one audio stream or a subtitle stream, those file sizes must also be subtracted from the maximum dvd image size.

All sizes are in bits.


That's the arithmetic, go for it. :)

---

### Post by ron999 on 2009-08-18
Hi
There's a typo in your command above
> tcrequant -i movie.m2v -o shrink ed.m2v -f 1.5


'shrink ed' should be all one word.
Like this:-
> tcrequant -i movie.m2v -o shrinked.m2v -f 1.5

---

### Post by Charlotte18 on 2009-08-18
Also, the "demux" stage seems to say that the two commands for audio and video should be put into terminal simultaneously, but "will run one after the other."  This doesn't sound right.  

Can't two the commands just be typed in and run one after the other separately? 

> 3) You now have 1 VOB file. We need to demutliplex it and get the M2V and AC3 files out of there. From the folder, again using the console run:

tcextract -i movie.vob -t vob -x mpeg2 > movie.m2v
tcextract -i movie.vob -a 0 -x ac3 -t vob > movie.ac3

They will run one after the other, don't worry and will produce an M2V and an AC3 file.


---

### Post by ron999 on 2009-08-18
> **Charlotte18 said:**
> 

Can't two the commands just be typed in and run one after the other separately?

Yes, I would do it with two separate instructions.

---

### Post by stinger30au on 2009-08-18
k9copy will do this on its head from gui, i bet theres a shell command to make it work 2

---

