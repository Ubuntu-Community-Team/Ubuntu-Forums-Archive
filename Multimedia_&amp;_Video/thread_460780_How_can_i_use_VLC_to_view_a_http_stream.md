---
title: "How can i use VLC to view a http stream"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by yinglcs2 on 2007-06-01
Hi,

I am trying to use VLC to view a http stream from 'youtube'.
Here is the url 'http://lax-v76.lax.youtube.com/get_video?video_id=egJR3K6UIJY'.

And when I open the stream using the 'Open stream' menu in vlc, i see nothing.
But when I enter that same url in firefox, i can download the flv file and view it using vlc.  

So how come I can't see the http stream using vlc directly?

---

### Post by steeleyuk on 2007-06-01
Heres my output from trying to open that file.

> VLC media player 0.8.6 Janus
[00000292] access_http access error: failed to read answer
[00000292] access_http access error: seek failed
[00000292] access_http access error: cannot connect to lax-v76.lax.youtube.com:80
[00000292] access_http access error: seek failed
[00000292] access_http access error: cannot connect to lax-v76.lax.youtube.com:80
[00000292] access_http access error: seek failed
[00000292] access_http access error: cannot connect to lax-v76.lax.youtube.com:80
[00000292] access_http access error: seek failed
[00000292] access_http access error: cannot connect to lax-v76.lax.youtube.com:80
[00000292] access_http access error: seek failed
[00000295] ffmpeg demuxer error: av_find_stream_info failed
[00000295] ps demuxer error: cannot peek
[00000289] main input error: no suitable demux module for `http/://lax-v76.lax.youtube.com/get_video?video_id=egJR3K6UIJY'
[00000280] main playlist: stopping playback

---

### Post by yinglcs2 on 2007-06-01
[http://lax-v76.lax.youtube.com/get_video?video_id=egJR3K6UIJY](http://lax-v76.lax.youtube.com/get_video?video_id=egJR3K6UIJY)

but when I try 'http://lax-v76.lax.youtube.com/get_video?video_id=egJR3K6UIJY' at my firefox, it starts downloading the file. Any idea?

---

### Post by yinglcs2 on 2007-06-04
Hi,

I tried this url again:

$ ./vlc [http://sjl-casing1.sjl.youtube.com/get_video?video_id=XaXz-dryqLg](http://sjl-casing1.sjl.youtube.com/get_video?video_id=XaXz-dryqLg)

It takes 'vlc' more than 3 minutes before start displaying the content.  Does vlc support http streaming?

---

### Post by Scunizi on 2007-06-04
I don't know why but vlc downloads the file to play it locally on a http stream.  3 minutes represents the amount of time it takes your connection to download it.

---

### Post by yinglcs2 on 2007-06-04
I have tried to do the same on vlc on a windows xp machine. But it starts showing the content in 5 seconds.
I am using the same machine (dual boot) same network. Why there is such a big difference?

Thank you.

---

### Post by abakker on 2007-06-13
As already mentioned at:
[http://ubuntuforums.org/showthread.php?p=2790697](http://ubuntuforums.org/showthread.php?p=2790697)

The cause appears to be Feisty's version of ffmpeg which VLC uses to play Flash video. It seems there is a bug in reading the flash video header. Apparently the Windows version is compiled against a newer ffmpeg that does not have this problem.

I've found no quick solution for this, you could upgrade ffmpeg as per
[http://po-ru.com/diary/bleeding-edge...ubuntu-feisty/](http://po-ru.com/diary/bleeding-edge...ubuntu-feisty/)

and then do something similar for VLC, as that has to be recompiled too.

---

