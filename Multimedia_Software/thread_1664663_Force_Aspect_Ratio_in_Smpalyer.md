---
title: "Force Aspect Ratio in Smpalyer"
date: 2011-01-11
forum: Multimedia Software
---

### Post by linuxyogi on 2011-01-11
Hi, I want Smplayer to display all videos in 16:9 aspect ratio.

I searched at google & found a solution here [http://ubuntuforums.org/showthread.php?t=863779]("http://ubuntuforums.org/showthread.php?t=863779"). 

Its working, with Gnome Mplayer but not with Smplayer. 

Smplayer still displays all videos in their default ARs.

Suppose I arrange multiple videos in Smplayer's playlist I need to get up from my seat & change the AR, every time a new track starts playing. This is really tiresome.

Please help

---

### Post by no2498 on 2011-01-11
see if setting it in totem helps

---

### Post by linuxyogi on 2011-01-11
> **no2498 said:**
> see if setting it in totem helps

Thanks for your reply.

Since most of my videos are high definition, vdpau is something I can't do without. Previously vlc was the only player I used but since it is not yet capable of using vdpau efficiently I only use Smplayer & Gnome Mplayer.

A) Settings in Totem doesn't allow to specify AR 
&
B) I just played a 1080 video in Totem. The cpu usage was in the 50s.

---

### Post by linuxyogi on 2011-01-14
If someone is sure of the fact that forcing aspect ration in not possible in Smplayer, kindly reply.

---

### Post by linuxyogi on 2011-01-14
If someone is sure of the fact that forcing aspect ratio is not possible in Smplayer ...... please reply.

---

### Post by SeijiSensei on 2011-01-14
Try these:

Preferences > Advanced > Monitor Aspect > 16:9

or maybe

Video > Aspect Ratio > 16:9

You can also try passing mplayer options via 

Preferences > Advanced > Options for MPlayer

try adding "-monitoraspect 16:9" in that box, though I'm guessing the "Monitor Aspect" setting does the same thing.  

See "man mplayer" for more possibilities.  Anything mplayer supports can be utilized via smplayer by adding the appropriate options to "Options for MPlayer."

---

### Post by linuxyogi on 2011-01-14
> **SeijiSensei said:**
> Try these:

Preferences > Advanced > Monitor Aspect > 16:9

or maybe

Video > Aspect Ratio > 16:9

"

**Preferences > Advanced > Monitor Aspect > 16:9**

was already selected.

**Video > Aspect Ratio > 16:9**

Works. But doesn't change the AR permanently. 

> **SeijiSensei said:**
> 
Preferences > Advanced > Options for MPlayer

try adding "-monitoraspect 16:9" in that box, though I'm guessing the "Monitor Aspect" setting does the same thing. 



Just tried that. Didn't work.  

> **SeijiSensei said:**
> 
See "man mplayer" for more possibilities.


Working on it.

Thanks.

---

### Post by linuxyogi on 2011-01-14
Just found this using man mplayer.

```
mplayer **aspect=16/9 **filename.avi
```

It works from the command line. 
But doesn't work when used in the "mplayer options" in Smplayer.

---

### Post by linuxyogi on 2011-01-24
Guys .............Please :cry:

---

### Post by Theredbaron1834 on 2011-05-18
This won't make them all 16/9, but I think it will do for you. Go to Preference's, Advance, and in the space where it says "Run the following....." put aspect_none. That will make the video stretch to full screen. However, if you are watching from a video it does still change the size you need to turn off auto resize for that.

I know it is a bit late, but I saw this post while search for it myself, and thought who knows, maybe you havn't found a fix yet.

---

### Post by linuxyogi on 2011-05-24
> **Theredbaron1834 said:**
> This won't make them all 16/9, but I think it will do for you. Go to Preference's, Advance, and in the space where it says "Run the following....." put aspect_none. That will make the video stretch to full screen. However, if you are watching from a video it does still change the size you need to turn off auto resize for that.

I know it is a bit late, but I saw this post while search for it myself, and thought who knows, maybe you havn't found a fix yet.

That's a great workaround. Tried that & it worked. 

Thanks.

---

### Post by linuxyogi on 2011-07-03
**_[B]Solution**_

Smplayer > Preferences > Advanced > Options for Mplayer > Options > add  

[COLOR=DeepSkyBlue]-aspect 16:9[/COLOR].

 
[/B]

---

### Post by linuxyogi on 2011-07-03
But sadly Smplayer is pretty useless for me as it fails to open files.

[http://ubuntuforums.org/showthread.php?t=1790983](http://ubuntuforums.org/showthread.php?t=1790983)

Read posts 1 -4. The later posts deal with a different issue which is now solved by installing mplayer2.

---

