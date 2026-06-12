---
title: "FFmpeg help encoding xvid!"
date: 2010-06-14
forum: Multimedia Software
---

### Post by tROOP4H on 2010-06-14
Hey! I'm not really sure where to post this tread, since i'm new here.. And it's a big forum!
Anyway, here it goes!

I'm trying to make a simple script for eather flv video or xvid (mpeg4). I seem to constantley run into truble, this that i've done wrong and so on..

The requiremets is that the script can be streamed within 5-6mbps. But still have exelent quality! (tough one it seems).

My try was eather someting like this:
```
exec("ffmpeg -i '.$uploadfile.' -vcodec mpeg4 -vtag xvid -s 1280x720 -aspect 16:9 -r 30 -b 6000k -ar 44100 -threads 8 ".$new_mp4."");
```
And i tryed with flv (but i believe that the quality is better on mp4 (pr. MB)
```
exec('ffmpeg -i '.$uploadfile.' -f flv -s 1280x720 -aspect 16:9 -r 30 -b 6000k -ar 22050 '.$new_flv.'');
```

I wish to be able to play videos in full screen without any big visual loss. It worked Okay with the flv-video, but i think it can be done better, with xvid, or some tweaking.. 
I don't know mutch about ffmpeg, as you might understand, maybe it would be better to user qmax? (i've tryed -qmin 1 -qmax 2, ended up lagging while streaming in a browser, but superb quality!)

If someone might help me out some. To be true to my self i wish that the bitstream should be less than 4-5mbps. 
It dosn't mather how it should be done, but i don't have acess to x264 just so you know.


- troopeR

---

### Post by FakeOutdoorsman on 2010-06-15
I can help you with a FFmpeg command, but I'm not totally sure what you are trying to do. Can you explain a little more? What version of Ubuntu are you using? Why don't you have access to x264? Can you show some information about your input video?  You can do that with:
```
ffmpeg -i input.foo
```

---

### Post by tROOP4H on 2010-06-15
Im using a php script to execute ffmpeg, from my ffmpeg host. 
Since x264 is not actually free, it's not implemented in their hosting-plan.

The inputfile is always changing, because it's supposed to work as a "youtube"-style script. Where ppl can upload vids to my site, with as good as possible quality..

EG: ```
exec('ffmpeg -i my_file.avi -f flv -s 1280x720 -aspect 16:9 -r 30 -b 6000k -ar 22050 output.flv');
```

- $uploadfile, is usually mp4, wmv or avi.. (but alot of more types is allowed.)
- $new_flv, is the output file, eater mp4 or flv, witch format i'm going to use is to be settled here. (I hope)

The reason i need top quality is because the script is goin' to be used as a "game"-tube. Where ppl upload trailers, gamingmovies/fragmovies, and that reqires really high quality, but i also wish that ppl overall won't have to wait 15 mins before playing it.. (HD but as low as possible bitrate) 

EDIT: And so i see now, that Xvid is not supported by flash, so it would not be playable in the browser... 
So all i got left is the standard mpeg4 and, flv i believe.. Does anyone know a better way to reach HD with max 5-6mbps streaming?

> And I quote BounceWeb (my host)
-FFmpeg
-FFmpeg-PHP
-Mplayer
-Mencoder
-Flvtool2
-Lame
-Libogg
-Libvorbis
-Xvid
-Theora
-FAAC 

Hope that helps.

---

### Post by FakeOutdoorsman on 2010-06-15
You're only going to get what you want if you encode H.264 with x264 (or libx264 via FFmpeg) into a MP4 or FLV container.  There is no reason for them to not include x264.  What's not "free" about it? If they are following such logic, then they should also remove FAAC because it does not have a "free" license.

Another option is VP8/WebM, but I doubt this host is up to date enough to encode to that with FFmpeg.

Ask them to allow you to encode with x264.

---

### Post by andrew.46 on 2010-06-15
Hi tROOP4H,

> **tROOP4H said:**
> Since x264 is not actually free, it's not implemented in their hosting-plan.

It is actually h264 which has a few *potential* problems rather than x264. Some details here:

[http://alien.slackbook.org/blog/google-open-sources-vp8-codec/](http://alien.slackbook.org/blog/google-open-sources-vp8-codec/)

Andrew

---

