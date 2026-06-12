---
title: "Mencoder options"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by ahaslam on 2007-10-24
Just wondering what options you guys pass when ripping a dvd, especially if you've found a benefit of some sort from them.

Here's 2 that I use:
```
mencoder dvd://1 -chapter 2-40 -aid 128 \
-oac mp3lame -lameopts abr:br=160:vol=3 \
-ovc xvid -xvidencopts fixed_quant=2 \
-vop scale -zoom -o movie.avi
```
```
mencoder dvd://1 -chapter 2-40 -aid 128 \
-oac mp3lame -lameopts abr:br=128:vol=3 \
-ovc xvid -xvidencopts fixed_quant=2 \
-vop scale -zoom -xy 720 -o movie.avi 
```
Both encode quickly & give good quality, though the first can be too large at times, scaling it down seems to give better results than higher quantizers.

:popcorn:

---

### Post by ahaslam on 2007-11-10
How about:
```
mencoder ~/media/dh4_hd_trail.mov -ss 00:05 -oac mp3lame -lameopts abr:br=192 -ovc x264 \
-x264encopts threads=2:bitrate=3690:subq=7:trellis=2:partitions=all:8x8dct:me=esa:me_range=64:frameref=7:psnr \
-vf scale=720:304 -o x264_vhq_3600.avi
```
I'll warn you, it's slow, but psnr is excellent.

Com'on, share your knowledge ;)

---

### Post by disturbedite on 2007-11-10
ewwww, use something other than mp3...like ogg or flac...

---

### Post by ahaslam on 2007-11-12
You've got a point, as long as compatibility is not a concern, vorbis is better.

Could anyone help me with this, my encodes give 50kbps, even though mencoder's default is 224 & I specified 160 :-k
> -oac lavc -lavcopts acodec=vorbis:abitrate=160 

PS. It turns out that vorbis is known not to play ball with mencoder. Apparently this was addressed a day or two ago in svn, though it's largely untested. I may try it out, but as far as stable releases go there's no decent vorbis support as of yet. 

So I guess I'll be using 'copy' or mp3 for a while longer. ;)

---

### Post by disturbedite on 2007-11-12
i've never had a problem with vorbis & mencoder.
shouldn't that be acodec=vorbis abitrate=160 not acodec=vorbis:abitrate=160?
i've been using ffmpeg lately and with ffmpeg its -ab for your audio bitrate...

---

### Post by ahaslam on 2007-11-12
No, all codec options should be separated by a colon, with no spaces. If I try it your way I get, "Failed to open abitrate=160".

You must be one of the lucky few, unless Ubuntu's patched mencoder specifically. I'll check it out on Ubuntu tomorrow, if it works I'll do some digging. ;)

My current favorite settings:

Fast (120fps):
```
mencoder dvd://1 -oac mp3lame -lameopts vbr=2:q=3 \
-ovc lavc -lavcopts threads=2:vqscale=3 -vf scale -zoom -xy 720 -o lavc.avi
```
VHQ (12fps):
```
mencoder dvd://1 -chapter 1-23 -oac mp3lame -lameopts vbr=2:q=2 -ovc x264 \
-x264encopts threads=2:qp=20:subq=6:trellis=2:partitions=all:8x8dct:me=umh:frameref=6 \
-vf crop=720:544:0:16,scale=720:384 -o x264_qp20.avi
```

VBR all the way ;)

PS. I checked Ubuntu, it's the same. My way it encodes with no errors, your way it encodes with the above error, both resulting in 50kbps. It is strange how ubuntu's version carries on encoding with an incorrect command line, maybe it's a difference between rc1 & rc2 :-k

Anyhow, let's continue with our preferred settings, not my problems ;)

---

### Post by disturbedite on 2007-11-13
whenever i do a dvd rip i do it at even higher quality.

i don't touch the resolution or framerate and use x264 lately (used to use xvid until i found its development is practically afaict).
as far as audio is concerned i leave it in its native ac3 format.  (is there any good reason to change it??)

---

### Post by ahaslam on 2007-11-13
I always specify '720' for the horiz res, otherwise (for me at least) it up-scales to 1024. The crop is simply to remove the black bars, which also improves quality. If you have a surround sound system, then there is no good reason to change the audio.

I'm interested to see what your higher quality settings are & how long it takes.

Do you find using x264 in 2-pass mode over-smooths the image (the main reason I go vbr)?

;)

---

### Post by disturbedite on 2007-11-13
i don't do file size mode, just vbr target like you do.
and i don't know what you mean by saying it upscales it 1024?  (if it does that, it may be cuz you're not properly setting the aspect ratio).
and cropping doesn't necessarily improve quality.
and the less compression and messing around with the source you do the less time it takes to re-encode the source.

---

### Post by ahaslam on 2007-11-13
Upscaling was the wrong word. PAL DVD's are 720×576, they're then scaled by the player to suit the aspect ratio (afaik). Cropping should improve quality, otherwise br is wasted on the shades of gray in the borders.

I'm still interested to see what you use & its speed. x264 really makes me want a quad-core ;)

---

### Post by disturbedite on 2007-11-13
i just told you what settings & formats i use.  but as far as time, i haven't done any benchmarks.  and to be honest, i haven't done a lot of x264 encoding yet.

---

