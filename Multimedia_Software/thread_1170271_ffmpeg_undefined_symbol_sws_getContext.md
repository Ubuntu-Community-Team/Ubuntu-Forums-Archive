---
title: "ffmpeg: undefined symbol: sws_getContext"
date: 2009-05-26
forum: Multimedia Software
---

### Post by sekoica on 2009-05-26
hello, i try to compile ffmpeg for make a video to 3gp from mpeg

configure :

./configure --enable-libmp3lame --disable-mmx --enable-shared --enable-libamr-nb --enable-libamr-wb --enable-nonfree  --prefix=$HOME

i have amr library installed

after make i do

install -c -m 755 ffmpeg ffserver /home/mon_user/bin

after when i launch ffmpeg

./ffmpeg -i /home/my_user/Bureau/Vido000.3gp -ab 56 -ar 22050 -b 500 -s 320x240 video0.mpg

next errors is : 

./ffmpeg: symbol lookup error: ./ffmpeg: undefined symbol: sws_getContext

i have compiled ffmpeg version ffmpeg-0.5 with the last svn of 25/05/2009

ffmpeg do not compile thanks you for help

---

### Post by FakeOutdoorsman on 2009-05-26
The *--enable-shared* command sometimes causes issues.  You usually don't need this option unless you are compiling other software that uses FFmpeg's shared libraries.  If you want *--enable-shared*, you should run *sudo ldconfig* after FFmpeg installation to update the links to the shared libraries.  Also, FFmpeg 0.5 and FFmpeg SVN are separate.  There is no reason to use FFmpeg 0.5 over FFmpeg SVN.  The 0.5 was created to satisfy distros that require "stable" releases, but it isn't any more or less stable than most SVN releases.  I assume most netbooks use the Intel Atom CPU and I believe these support MMX.  You may find this guide useful:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by andrew.46 on 2009-05-26
Hi sekoica,

> **sekoica said:**
> 

```
./ffmpeg -i /home/my_user/Bureau/Vido000.3gp -ab 56 -ar 22050 -b 500 -s 320x240 video0.mpg
```



If you are trying to convert *from* mpg *to* 3gp you have the order reversed here. Should be:

```
ffmpeg -i myfile.mpg myile.3gp
```

My apologies if I have misunderstood your post :-).

Andrew

---

