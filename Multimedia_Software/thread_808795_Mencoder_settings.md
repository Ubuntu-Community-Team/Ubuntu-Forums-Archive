---
title: "Mencoder settings"
date: 2008-05-26
forum: Multimedia Software
---

### Post by tylersontag on 2008-05-26
Mencoder keeps cropping off the edges of my video files, heres how im using it

```
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:aspect=16/9:acodec=ac3:abitrate=192 -ofps 30000/1000 -o your_video.mpg Input_vid.avi

```

I'm wanting it in NTCS (N. American) widescreen format, any thoughts?

---

### Post by Technobabel on 2008-06-24
You may want to try this one out:

DVD (with timestamps on every frame, if possible):

-of mpeg -mpegopts format=dvd:tsaf

DVD with NTSC Pullup:

-of mpeg -mpegopts format=dvd:tsaf:telecine -ofps 24000/1001

This allows 24000/1001 fps progressive content to be encoded at 30000/1001 fps whilst maintaining DVD-compliance.

Can be found in the mplayer [help docs]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-vcd-dvd.html")

CU
Chris

---

### Post by anindya_m on 2008-06-24
Btw I find ffmpeg very easy to use in this case (avi -> DVD). Maybe give it a try?

---

### Post by eye208 on 2008-06-24
> **tylersontag said:**
> I'm wanting it in NTCS (N. American) widescreen format, any thoughts?
Add this to your command line:
```
-vf expand=:::::16/9,scale=::::::ntsc,harddup
```
This will expand the frame size to fit a 16/9 aspect ratio, then scale it to 720x480 (anamorphic widescreen).

---

### Post by eye208 on 2008-06-24
> **Technobabel said:**
> DVD with NTSC Pullup:

-of mpeg -mpegopts format=dvd:tsaf:telecine -ofps 24000/1001

This allows 24000/1001 fps progressive content to be encoded at 30000/1001 fps whilst maintaining DVD-compliance.
The telecine/ofps combination will yield ugly results if the input material is not 24000/1001 fps because -ofps will drop frames. I recommend using tele_src/tele_dest instead. This will generate pulldown patterns for any input framerate (23.976, 24, 25), so you can omit the -ofps option.

---

### Post by jessebean on 2008-06-25
Hi all --

I'm also trying to use ffmpeg to convert avi to mpg.  I once had a decent solution, but I've lost the script.

original entry

> nice mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:aspect=16/9:acodec=ac3:abitrate=192 -ofps 30000/1000 -o your_video.mpg Input_vid.avi

I got a million of these "duplicate frame" errors, and the video is halting -- like once per second it halts, seemingly.  I'm not avid for video / audio conversion, don't understand the options.  I just need to convert avi to mpg to ntsc dvd using ffmpeg / mencoder, dvdauthor, mkisofs.  Also, it would be super awesome to merge two movies onto one single layer disc! (starting from 700mb avi files)

> Pos:6794.6s 162908f (100%) 226.37fps Trem:   0min 1055mb  A-V:0.011 [1075:192]
1 duplicate frame(s)!
Pos:6794.7s 162912f (100%) 226.37fps Trem:   0min 1055mb  A-V:0.007 [1075:192]
1 duplicate frame(s)!
Pos:6794.8s 162914f (100%) 226.37fps Trem:   0min 1055mb  A-V:0.006 [1075:192]
Flushing video frames.
Writing index...

---

### Post by jessebean on 2008-06-25
Now I am unable, upon checking, to forward (by clicking the progress bar in the totem player) -- unable to forward past about 20-25 minutes into the movie (which came out at 1G from the 0.7G avi file, and the total in the current time / total time keeps changing, flickering.  Your help is greatly appreciated.  This mpg problem has proven to be the most tedious task for me.

---

### Post by jessebean on 2008-06-25
the script argument settings don't work for me, but following all the steps in the heart of it is exactly what I was looking for :-)

[http://ubuntuforums.org/showpost.php?p=3641194&postcount=15]("http://ubuntuforums.org/showpost.php?p=3641194&postcount=15")

It converts avi to mpg to dvd iso :KS

---

