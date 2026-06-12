---
title: "ffmpeg gone awry after update"
date: 2011-04-21
forum: Multimedia Software
---

### Post by sn0m on 2011-04-21
Ubuntu team, is it possible to terminate the person who changed messed up ffmpeg in the last update.
I use this code: ffmpeg -i file1.flv -f mp4 -vcodec libxvid -s 640x360 -b 768kb -r 25 -aspect 16:9 -acodec libfaac -ab 96kb -ar 44100 -ac 2 file1.mp4
to convert flv files to mp4 files so I can play them in my nokia 5800.
Well everything has been working fine till last update a few days back.
Now ffmpeg doesn’t do the conversion anymore.....
So can you tell me where is this trouble maker so we can terminate him....
reg
sokol

---

### Post by andrew.46 on 2011-04-21
Hi sokol,

With FFmpeg in particular I have always found it is better to build your own, preferably from git but there are some recent releases available from FFmpeg itself and soon from libav if you prefer a more 'stable' source.

Andrew

---

### Post by FakeOutdoorsman on 2011-04-21
> **sn0m said:**
> 
Well everything has been working fine till last update a few days back.
Now ffmpeg doesn&#8217;t do the conversion anymore.....
You provided the command which is useful, but the FFmpeg output is just as important. It's hard to diagnose the problem or duplicate the error without the actual output.

However, I would guess that your issue can be resolved by [Re: FFmpeg stoped working after reinstall](http://ubuntuforums.org/showpost.php?p=10680471&postcount=2).

---

### Post by sn0m on 2011-04-22
Hi Andrew, I'm not very good when it comes to compile from source. I guess this will be a learning curve for me. I'd appreciate if you have any good links to follow kind of step by step compile from source?
Thanks
Sokol

---

### Post by andrew.46 on 2011-04-22
The gentleman who has posted above you has the definitive Ubuntu guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

and this makes the whole process very easy :)

---

### Post by sn0m on 2011-05-02
hallelujah, ffmpeg is back working ok.
Can the person who does security thing and messes up before any new release to kindly not to mess it up again.
thank you

---

