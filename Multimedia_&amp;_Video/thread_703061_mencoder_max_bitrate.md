---
title: "mencoder max bitrate"
date: 2008-02-20
forum: Multimedia &amp; Video
---

### Post by samuraix51 on 2008-02-20
Does anyone know what the max bitrate that mencoder can do for video?
I'm trying to run some comparison tests with it and I can't get anything over 4228.3 kbps.


I've tried setting bitrate=5000 to see what the file size is.
Then I set bitrate=9800, which is what the DVD was, to compare what the File sizes would be.

When I play them using mplayer, it shows it as 4228.3 kbps as the bitrate for both of them.

Here's my script that I use to encode with it.
```

#Dump to vob file
mplayer -dvd-device file.iso dvd://1 -dumpstream -dumpfile file.vob;

#Pass 1
mencoder -v file.vob -ovc x264 -x264encopts subq=4:bframes=4:b_pyramid:weight_b:pass=1:psnr:bitrate=5000:turbo=1:threads=auto -aid 128 -oac copy -ofps 24000/1001 -o /dev/null;

#Pass 2
mencoder -v file.vob -vf spp,hqdn3d=2:1:2 -ovc x264 -x264encopts subq=5:partitions=4x4:8x8dct:frameref=3:me=hex:bframes=4:b_pyramid:pass=2:psnr:bitrate=5000:threads=auto -aid 128 -oac copy -ofps 24000/1001 -o file.avi;

```

---

### Post by eye208 on 2008-02-21
> **samuraix51 said:**
> Does anyone know what the max bitrate that mencoder can do for video?
It depends on the movie and the codec. H.264 encoding will be lossless with the option "-x264encopts qp=0". If you want to increase the bitrate even more, encode with "-x264encopts qp=0:keyint=0". This will result in a lossless H.264 encode with I-frames only (useful for video editing).

---

### Post by samuraix51 on 2008-02-21
The original source is a DVD, I was just trying to do some comparison tests with it.

I am looking to encode the movie with x264 video and AC3 audio at DVD quality with a file size of 2-3GB.

Any ideas of what options / command to use to get this?
I'm using mencoder currently

Thanks

---

### Post by eye208 on 2008-02-25
If you are looking for constant quality regardless of the type of movie, use constant quantizer/rate factor encoding. If you are looking for a particular file size, calculate the target bitrate and use 2-pass encoding.

I think 2-3 GB is an insane file size for an H.264 encoded movie in DVD resolution. If you are so concerned about quality loss, why not just copy the original MPEG-2 streams and forget about re-encoding?

---

### Post by samuraix51 on 2008-02-25
Ok, I just started trying this, so I don't know what exactly I should be using, for bitrate and such.  What would you recommend to use for doing the DVD quality h264?

any suggestions would be much appreciated.  thanks

---

### Post by justsomedude on 2008-02-25
I suggest you get rid of the black borders first:

```
mplayer file.vob -vf cropdetect
```

Let the video play a bit and copy the values for crop=...


You can try this script:

```
# First pass
mencoder -v\
         file.vob\
        -vf crop=720:560:0:8,scale=704:400,harddup\
        -ovc x264 -x264encopts subq=6:partitions=all:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b:bitrate=1500:threads=auto\
        -oac copy\
        -of rawvideo\
        -o file.264

# Second pass
mencoder -v\
         file.vob\
        -vf crop=720:560:0:8,scale=704:400,harddup\
        -ovc x264 -x264encopts subq=6:partitions=all:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b:bitrate=1500:threads=auto\
        -oac copy\
        -of rawvideo\
        -o file.264
```

-Copy the values for crop you determined in step 1 into the script (1st & 2nd pass)
-Adjust aspect ratio in scale=... (1st & 2nd pass)
-If you don't have a dual core processor, delete "threads=auto" from the script (1st & 2nd pass)


IMO, these settings are already overkill but since you wrote you wanted very good quality...

I suggest you experiment with some smaller clips first, to find settings that suit you.

NOTE: This script is for video only. I suggest you encode audio seperately.

Also, don't use the .avi container for h264. ;)

---

