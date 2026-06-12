---
title: "AVI to MPG for VCD"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by dburnett77 on 2007-06-05
I am trying to convert some video I shot with a Canon A460 digital camera.
With ffmpeg, I can convert the video, but the sound is not encoded right.  I use the following command:

ffmpeg -i _file_ -target ntsc-vcd _out.mpg_

The video transcodes well, but the sound is not.  In some players, I get silence, in others, it is squeaky.

The recorded audio is pcm_u8, mono, 88 kb/s.  Does anyone know the accurate way to invoke ffmpeg so the audio is placed properly in the .mpg file.

Thanks.

---

### Post by dburnett77 on 2007-06-06
Found the answer to my problem in another post:

tovid
todisc

are a couple of programs that run well on my system, and get the job done.
On the tovid web site, there's instructions on how to add the source to the repository, so that all dependencies and the program are installed correctly.

---

### Post by dburnett77 on 2007-10-29
Actual author???

Probably the guy that told me I didn't know what I was doing when trying to find out, and is now currently  --  unwinding..

---

