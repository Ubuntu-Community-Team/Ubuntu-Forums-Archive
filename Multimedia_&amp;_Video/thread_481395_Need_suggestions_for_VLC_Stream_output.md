---
title: "Need suggestions for VLC Stream output"
date: 2007-06-22
forum: Multimedia &amp; Video
---

### Post by Medieval_Creations on 2007-06-22
I've been playing around with recording streams with VLC lately and am curious as to which combination of options would produce the best output.  I'm really looking to backup some of my DVDs but loosing 4-8 GBs per doesn't make sense to me.  By just recording the movie will save a lot of space...

I've tried a few combinations of different settings produce the best quality without the file getting to bloated and maybe some differances between MPEG TS, MPEG PS, MPEG 1, MP4, MOV.

---

### Post by pgroudas on 2007-06-22
I don't personally backup my dvds with vlc (I use handbrake) but I've tinkered with it.  If you want decent backups with smaller size, I believe you're going to want to use the .mp4 or .avi container, and ffmpeg, xvid, or x264.  With these codecs you can use a relatively low video bitrate (<1000) for decent quality.  x264 will give you the best video for a particular bitrate, but it is sloooooow to encode.

---

### Post by Medieval_Creations on 2007-06-24
Thanx fo the tip.  I'll take a look at handbrake.  I noticed that there isn't a gui for the linux version, that kind of bites... oh well just have to read up on the commands.

Thanx!

By using the basic command "HandBrakeCLI -i VIDEO_TS -o movie.mp4 -e x264 -b 2000 -B 192" does it record just the movies or all the other stuff on the DVD as well.
I'm really only interested in recording just the actual movie?  I don't need/want all the extras & menus.

---

### Post by Medieval_Creations on 2007-06-24
Working in ansering my one question... :) thanx to Caenim's guide. figured out how to scan the DVD and determine whch title is the movie, basically by length.

Any suggestions to lessen th elearning curve would be appreciated though.

---

### Post by pgroudas on 2007-06-24
It just backs up the main movie by default, although you may want to point it to the enclosing dvd folder, not the VIDEO_TS folder (but it may work just as well).  After experimenting a lot, heres the script I run to use handbrake.  It prompts for the input device (which can be folder, dvd drive, anything handbrake takes), and an output filename.  In this case the output file must be .avi because its the only one that supports AC3 passthrough for sound (I like my 5.1 :)).  ```

#!/bin/bash
echo Enter Input Device
read dvddevice
echo Enter name for file
read name
HandBrakeCLI -v -i $dvddevice -t 1 -o $name -f avi  -e x264 -2 \
-E ac3 -x subq=6:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b:psnr:bit$

```

You'd probably want to change ac3 to lame or faac to downmix to a lower bitrate stereo.  Also, all the options after -x are x264 specific.  If you don't want to spend a lot of time reading up, they're pretty good defaults, but plan on the encodes taking place over night (takes ~8 ours on my 1.7 GHZ intel core duo.

---

### Post by pgroudas on 2007-06-24
One more thing, handbrake can also use ffmpeg, which will give really almost as good video quality, but encode 2-3 times faster.

---

### Post by Medieval_Creations on 2007-06-24
Kool!   thanx alot for the script... I've been playing with handbrake alot last night.  I've got it down to about 2 & 1/2 hours to encode 1 movie using "HandBrakeCLI -i <drive> -o <movie>.mp4 -e x264 -b 2000 -B 192".  I have no problems with the vid quality.

Aside from the time it takes to encode, all-in-all I must say Handbrake does it's job well.

---

### Post by pgroudas on 2007-06-25
Cool, I'm guessing that it only takes 2 1/2 hours because you only do one pass of encoding.  2 makes it better (like any codec, really), but if its good enough then why not?  How big are the files you're getting?

---

### Post by Medieval_Creations on 2007-06-25
Between 1.5 & 2 GB so far.  I'm still playing around with some of the options... How big are the files typically with the options that you use? 
I'm just now testing with the options you use in your script.  I'm guessing that the -2 after the x264 is the 2 passes?

The only thing I took out was the avi part, since I've been saving them as mp4s.

HandBrakeCLI -v -i $dvddevice -t 1 -o $name -e x264 -2 -E ac3 -x subq=6:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b:psnr:bit$

---

### Post by pgroudas on 2007-06-25
They're between 1.3 and 1.4 usually, but that includes the Dolby Digital 5.1 audio track which is 448 kbits/s (as opposed to mp3 or faac which is usually around 128 kbits/s).  This equates to 393 MB in a 2 hour movie.

---

### Post by Medieval_Creations on 2007-06-25
Well I did Hackers last night with my command and am doing it again today with you script for a comparison.
It'll just take me some time tinkdering with it to find the options that work best for me.  But your script and help definately put me farther ahead than I would have been reading up on it my self.

---

