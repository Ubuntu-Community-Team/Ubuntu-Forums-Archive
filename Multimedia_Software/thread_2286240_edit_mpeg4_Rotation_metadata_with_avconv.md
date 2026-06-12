---
title: "edit mpeg4 Rotation metadata with avconv"
date: 2015-07-10
forum: Multimedia Software
---

### Post by josh144 on 2015-07-10
Hi community,

I am struggling with changing metadata namely Rotation by avconv with least CPU intensive way. First of all, I do not know if this is feasible with this tool - just change metadata without touching video/audio. 

Secondly, if this is feasible, I thought the following option will do, but what I found is that converted does not contain Rotation. I checked with mediainfo.

avconv -i original.mp4 -metadata:s:v:0 rotate=90 converted.mp4

I have spent hours to sort things out but I am still unclear about understanding the problem. I am totally new to this domain... 

Any insight/comment/advice is appreciated.
- Josh

---

### Post by mc4man on 2015-07-10
Forget avconv, no idea if it'll change rotation, ffmpeg will 
Easiest - grab a static build from link below, extract. Then path to the extracted ffmpeg binary   your command
(or just drop the ffmpeg binary into a terminal, then return to terminal focus,  add command,  ect.
[http://johnvansickle.com/ffmpeg/](http://johnvansickle.com/ffmpeg/)
pick either the current git or release for your arch, pretty much the same

Then use a command like - 
```
ffmpeg -i original.mp4 -c copy -metadata:s:v:0 rotate=90 converted.mp4
```

Example here using the static binary extracted in Downloads - 
```
:~$ /home/doug/Downloads/ffmpeg-2.7.1-64bit-static/ffmpeg -i  '/home/doug/Videos/Amy Winehouse - Back to Black.mp4' -c copy -metadata:s:v:0 rotate=90 sideway.mp4
```

If you decide to use ffmpeg a lot then you can put the ffmpeg in a bin dir. in your $PATH to eliminate having to to go /path/to/ffmpeg command or use a ppa version of ffmpeg if on 14.04 or 15.04 has ffmpeg included now ..

---

### Post by josh144 on 2015-07-11
Hi mc4man,
I tried ffmpeg and everything worked as expected. I also confirmed ffmpeg is available on Ubuntu 14.04 and apt-get it fine. 
Million thanks,
- Josh

---

