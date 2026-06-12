---
title: "ffmpeg and vhooks"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by xpavement on 2007-05-26
I'm trying to add some overlay text to the video I am recording with ffmpeg on Fiesty. I can record fine, but when I try to use the vhook options as outlined here, I get errors:

[http://ffmpeg.mplayerhq.hu/hooks.html](http://ffmpeg.mplayerhq.hu/hooks.html)

My test command line:
```
ffmpeg -vd /dev/video0 -s 320x240 -r 29.97 -b 975 -an -vcodec mpeg1video -t 00:02:00 -deinterlace -vhook '/usr/lib/vhook/imlib2.so -c white -F usr/share/fonts/truetype/freefont/FreeMono.ttf/12 -x 0 -y 0 -t %A-%D-%T' /extra_drive/sec_vid/test.mpg
```

My error:
```
/usr/lib/vhook/imlib2.so: undefined symbol: imlib_free_image
```
I also tried the drawtext.so vhook as well and it got a different undefined symbol error:
```
/usr/lib/vhook/drawtext.so: undefined symbol: FT_Set_Pixel_Sizes
```

Any ideas on what I can check to get one ofthese working? I assume this ubuntu package version of ffmpeg has vhooks enabled, but maybe not?

---

### Post by shaggly on 2007-05-26
I'm afraid that I can't give you any advice on this, old chap.

What I can tell you is that I've spent about the best part of the last 4 hours fiddling with correcting problems compiling ffmpeg from the svn version. The only reason I'm doing that is Flash 8....and I hate being beaten by anything proprietary :p

The final stumbling block is vhooks, and it's quite a headache. In fact I th

I hope someone posts some help for you. I tend to do most of my research myself, but it can cause major brainache at times.... :frown:

---

### Post by xpavement on 2007-05-26
Thanks, have you seen this guy's blog post?:

[http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/](http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/)

It may help you out, maybe not since I don't see and --enable-vhooks in there, I really don't want to have to compile my own version to get this to work, it's weird the package would come with the vhooks themselves and not be able to use them...

---

### Post by xpavement on 2007-05-27
I went ahead and followed the link's guide to building a newer version of ffmpeg, and now the video hooks are working fine. I had to change my command line a bit to get it to work since things have changed with this new version, but now it actually displays a timecode on the video using the imlib2 vhook.

---

