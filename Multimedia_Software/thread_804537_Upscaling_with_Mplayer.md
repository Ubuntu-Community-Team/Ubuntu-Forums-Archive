---
title: "Upscaling with Mplayer"
date: 2008-05-23
forum: Multimedia Software
---

### Post by doubledouce on 2008-05-23
Hi!

I'm using freevo as a media center and I'm trying to get Mplayer to upscale my "sub" 720p material. Is it possible to have Mplayer upscale everything that is lower than 720p up to 720p and leave everything else (higher than 720p) alone?


thanks

---

### Post by aeiah on 2008-05-23
mplayer will scale to the size of its window, or in fullscreen, the size of your resolution

---

### Post by aeiah on 2008-05-23
im not sure about freevo, but you could say, make mplayer apply smooth post processing to anything that is avi and leave anything that is .mkv alone, i suppose. this should seperate most normal def from hd. or you could write a script that detects the resolution and applies the mplayer option flags you want depending on the resolution of the video

---

### Post by doubledouce on 2008-05-23
> **aeiah said:**
> mplayer will scale to the size of its window, or in fullscreen, the size of your resolution

So when I set the resolution to 1920x1080, Mplayer will automatically upscale the lower resolutions??

I like the idea of setting post prosessing to everthing else but .mkv. Do you know what I need to put in my Mplayer config to do this?


Thanks for the reply :)

---

### Post by aeiah on 2008-05-23
have a look here:
[http://tivo-mplayer.sourceforge.net/docs/mplayer-man.html#sect4](http://tivo-mplayer.sourceforge.net/docs/mplayer-man.html#sect4)

the -autoq -vop pp option might be a good one.

the way id do it in ubuntu (you say you're using freevo?) would simply be to take advantage of the 'always open with this application' option when you go to a .avi's properties. instead of selecting mplayer (which is actually gmplayer) enter a custom command (perhaps gmplayer -autoq -vop pp). whenever you open avis it'll open them with this command instead of a normal gmplayer command

there are other ways using a script like this (this is in pseudocode)
```


if filename.extention = mkv
     gmplayer 
else
     gmplayer -autoq -vop pp file

```


but remember: upscaling cant invent any info that isnt there. a low quality video will never look amazing. mplayer will by default try and smooth out the nasty bits but a 700mb avi film will never look good compared to a 4.4GB 720p mkv. a 1.4GB avi film *maaay* look ok but really you need the source material to be of dvd quality for it to still look good compared to HD

---

### Post by doubledouce on 2008-05-23
Thanks man!

I know a low bitrate file won't be amazing, but some smoothing is better than nothing. :)

Now I gotta make this work.

---

