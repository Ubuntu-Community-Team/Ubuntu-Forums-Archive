---
title: "Cinelerra playback to slow"
date: 2011-11-09
forum: Multimedia Software
---

### Post by drumanart on 2011-11-09
Hello.
I'm editing a video with **Cinelerra 2.1.5CV**. My problem is , if I put some keyframes and make any changes to the timeline, (playing with the occupancy for example), the video runs in slow motion after passing the first keyframe. 
The video is 6 minutes long. I converted the original file with **ffmpeg** and tried the extensions **mov, avi.dv, mpeg**. 
My computer has an **Athlon X2 Dual Core Processor** with a memory of **4Gb (DIMM, DDR2)**.

After rendering, the video runs correct, but it is quite irritating to edit the video in slow motion.
Martin

---

### Post by drumanart on 2011-11-09
I found the soltion myself;
Following this threat:
[http://g-raffa.eu/Cinelerra/HOWTO/settings.html](http://g-raffa.eu/Cinelerra/HOWTO/settings.html)
solved my problem
Martin

---

### Post by streamsanddragonflies on 2012-05-19
Hello Drumanart!

I don't know if you will see this post since you answered your own question a while ago, but I was having a problem with playback in the compositor as well.  I did NOT have it set to *play every frame* but as soon as I added a couple of effects and keyframes, playback was jerky. 

I needed to see the movement as smooth as possible but not in slow motion either. So I finally figured how to successfully render part of my project with the right settings so i can add the rendered file to say, an alpha video track and the composite can play smoothly.  So far the videoforlinux wrapper with RGBa float & 2 pass audio worked for me.  

Later, I will try to properly render an effect on a specific track.  I tried quickly but had some YUV codec and it didnt have an alpha channel which I need so next time I will use the RGBa codec instead.  So looks like you have to choose your setting carefully to get the desired results.

---

