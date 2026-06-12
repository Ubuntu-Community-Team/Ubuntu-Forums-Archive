---
title: "Need to convert H.264 MP4's into something less onerous"
date: 2010-01-27
forum: Multimedia Software
---

### Post by abelundercity on 2010-01-27
I work for a nonprofit, so professional and personal hardware upgrades are unlikely in the near future in this time of budget cuts.

We plan to post some YouTube videos to help raise awareness of our programs, but the camera we got only records in H.264 MP4 format, which our aging machines doesn't like.  Video is choppy at best, though the audio remains intact.

So basically what I'm asking is, what is the best method for converting H.264 into a format friendlier to older machines?  And just what format is that, please?

Thank you for your time.

---

### Post by sports.car.guy on 2010-01-27
The video being on you tube shouldn't make it's format a concern more then the current hardware on the systems you are referring to being able to use Flash. Flash can be a pig, especially in Linux, and that needs to be looked at more then video format.

If you are looking to convert it and edit it still, Kdenlive is a very powerful and flexible piece of editing software.

---

### Post by ron999 on 2010-01-27
@ abelundercity
Hi
Like sports.car.guy said above, once the files are on YouTube they will be viewed in your browser as flash.
In the meantime, if you want to convert the files into something less onerous to view on your PC you could try converting them to avi files using ffmpeg.
A command like this should be ok:-
```
ffmpeg -i whatever.mp4 -vcodec msmpeg4 -acodec libmp3lame whatever.avi

```
Use your own file names obviously!
If this is OK then you can use a program called WinFF which is a GUI for ffmpeg.
From here:-[http://winff.org/html_new/]("http://winff.org/html_new/")

---

### Post by abelundercity on 2010-01-27
Thanks to you both.  The YouTube upload wasn't so much the concern as the fact that the choppiness was making the videos damn hard to work with on the editing side of things.

---

