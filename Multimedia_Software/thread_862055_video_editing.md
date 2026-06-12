---
title: "video editing"
date: 2008-07-17
forum: Multimedia Software
---

### Post by harryliddic on 2008-07-17
What is the best open source video editor for linux(debian) for editing dvds
and then burning them?

---

### Post by pmlxuser on 2008-07-17
visit
[http://cinelerra.org/](http://cinelerra.org/)
[http://www.kinodv.org/](http://www.kinodv.org/)
[http://vivia-video.org/](http://vivia-video.org/)

vivia looks promising but you can make your own decision :;

---

### Post by stitchmysmile93 on 2008-07-17
I use devede...

---

### Post by harryliddic on 2008-07-17
> **stitchmysmile93 said:**
> I use devede...

I download devede and ran install.sh but it just froze. How do you install devede?

---

### Post by Erlander on 2008-07-17
> **harryliddic said:**
> How do you install devede?

Use either Synapatic Package manager or Add/Remove programs.

Rob

---

### Post by dominiquec on 2008-07-17
For simple editing jobs (selecting segments), I use avidemux.

For something a little extra (basic effects), I use kino.

Both are in the repositories.

---

### Post by anderber on 2008-07-17
You can also use Blender for simple editing and adding After Effects like effects to it.

---

### Post by mateuszbaranski on 2008-09-11
> **anderber said:**
> You can also use Blender for simple editing and adding After Effects like effects to it.

I doubt that guy who needs just cut & paste some video could learn Blender in reasonable short time...

You asked for OpenSource - there is no "best OS editor for linux" one is best for some task and other for other task. If you look for complete solution from capturing video, editing, rendering, dvdauthoring - use Windows - sad but true.
I personnally stoped using windows 3 years ago and successfully finished couple of movies from DV to DVD. Tools that I use are as follows:
1) Kino for capturing DV from camcorder (Cinellerra usually hangs up by capturing so I don't even try to find solution)
2) Cinelerra for NLVE and rendering to YUV stream (pipe)
3) GIMP for preparing Titles for cinelerra (format TGA), and for qdvdauthor (format JPG)  
4) mpeg2enc for external coding of YUV stream
5) qdvdauthor for making menu for DVD
6) dvdauthor for dvdauthoring
7) k3b for burning (you can use growiso ofcourse or other program)
 

I admit - it's a path of pain. Every small step you want to do is a pain, and takes many hours spend by your favorite linux. 
But I can tell you - it is possible to do professionally looking DVD (even with background audio music in DVD menu, and 3 different music tracks in movie).

I wish much determination.

---

