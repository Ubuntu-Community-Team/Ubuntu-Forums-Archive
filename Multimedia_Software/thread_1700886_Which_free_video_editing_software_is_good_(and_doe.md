---
title: "Which free video editing software is good (and doesn't take ages to render)?"
date: 2011-03-05
forum: Multimedia Software
---

### Post by nauru on 2011-03-05
I'm a beginner with video editing, and mainly what I'm interested in doing at this point is placing clips one after another in order, and then outputting the compilation to a high quality video file of some sort (could be mp4, mkv, avi, doesn't really matter too much).

I've tried Pitivi Video Editor and it's quick and easy to manipulate video clips, which is good.  However for a 75 minute video (720p) composed of three 25 minute clips, it is taking more than 4 full hours to render.  I have not even used any effects or made adjustments to the file, I'm simply connecting 3 separate clips into one longer clip. 4+ hours to render a 1 hour and 15 minute movie is too slow. Is there a program which can do it faster?  I have an i7 quadcore with 6gb of ram here, so my feeling is that the problem is not my hardware.

Thanks.

---

### Post by no2498 on 2011-03-06
try traGtor
it may be faster for you
hope it helps you

---

### Post by rayj on 2011-03-06
Cinelerra can be used to edit a lower-definition 'working' video file as a placeholder...then you can use the excellent batch processing feature to point it at the real file and render it headlessly. I haven't actually done this myself, but it is a documented feature. I have run Cinelerra batch renders, and they use the hardware very efficiently. I think it's an underestimated tool in general.

6 gigs of memory might not be helping you as much as you think. I'm hoping to set up a server with a bit of ram to help process HD material in a timely fashion, but my intent is to use a different OS (probably AVLinux...) - 32bit, but it uses PAE extensions, which actually allow you to use more/all of your ram. I think. This way, whenever I need to process real video files, I can farm the processing out through the server as well. Check out the renderfarm feature on Cinelerra as well.

---

