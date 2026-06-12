---
title: "using ubuntu to create h.264 html5 videos"
date: 2011-01-09
forum: Multimedia Software
---

### Post by adamSpline on 2011-01-09
Hi all,

I just installed ubuntu 10.04 and I am new to the video options.  I would like to create some videos that are html5 compatible.  Creating ogg with Pitivi is no problem  :)

But, how do I create a H.264 video?  I see that in Pitivi there are many options for container, audio and video, etc.  Does anyone know an option that is good for H.264?

Or can I install something that will allow a terminal (or mencoder) command to convert an ogg to H.264?  Any ideas will be great

-Adam

ps.  Yes I am new to this, so I am sorry if this is a simple task.

---

### Post by marl30 on 2011-01-09
I'm just getting into video editing myself. So far Pitivi is just for basic editing. It doesn't really do very advance stuff. You may want to take a look at Openshot, and most likely you'll find what you are looking for in Kdenlive.

---

### Post by marl30 on 2011-01-09
Add Handbrake to that list. I'm currently preparing a video in Hanbreak for Youtube in h.264.

---

### Post by lovinglinux on 2011-01-10
I would recommend not converting to h.264, because not all browsers support h.264 html5. The recommended html5 format is webm, which can be played by Firefox 4, Opera 11 and the stable Chrome.

You can do that by following the instructions at [http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289](http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289)

It will allow to convert to webm and h.264 as well.

Here is the command for webm conversion:

```
ffmpeg -i originalvideo.ogg -threads 4 outputvideo.webm
```

Keep in mind webm conversion is really slow, one of the reasons it hasn't been widely implemented yet.

---

