---
title: "videos with no audio on ipod nano"
date: 2010-03-26
forum: Multimedia Software
---

### Post by 80aless on 2010-03-26
Hi, 
I used this code 
```
ffmpeg -i video.flv -r 12.5 -s 320x240 -vcodec mpeg -ar 22050 -ab 128k -acodec ac3 out.mp4
```
for converting a flv to mp4. The output is all right, but in the ipod nano 3g 4GB it has no sound. What's wrong? Maybe I put the wrong -acodec ac3 options? 
```
-acodec libfaac
``` OR ```
-acodec aac  
```
gives me
```
Unknown encoder 'libfaac'
```
Thanks

---

### Post by andrew.46 on 2010-03-26
Hi 80aless,

I don't know a lot about these devices but I suspect you are probably after *aac* rather than *ac3 *and thus you need to fit your copy of FFmpeg out for aac encoding. You don't mention your version of Ubuntu but all are catered for here:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

Do these devices take h264? This might be a better option than your existing video codec, hopefully an ipod nano user can comment here :).

All the best,

Andrew

---

### Post by nothingspecial on 2010-03-26
This works for me -

```
ffmpeg -i input -acodec libfaac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 -flags +4mv -trellis 2  -cmp 2 -subcmp 2 -s 320x180 -metadata title=X output.mp4
```

change the X after title= to the title you want otherwise all your videos will be called X on your ipod.

---

### Post by 80aless on 2010-03-26
Thanks,
Point C of in the link you sent me, i.e. reinstalling ffmpeg from Medibuntu 
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)
makes the option 
-acodec libfaac 
work.
All the best

---

### Post by andrew.46 on 2010-03-26
Hi 80aless,

> **80aless said:**
> Point C of in the link you sent me, i.e. reinstalling ffmpeg from Medibuntu 
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)
makes the option 
-acodec libfaac 
work.

Great news :). Perhaps at some future stage you might have a look at the svn FFmpeg which I believe has a few x264 presets for ipod devices. But again I have to admit that I have not experimented with these, not having such a device...

All the best,

Andrew

---

