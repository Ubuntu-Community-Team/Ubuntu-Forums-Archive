---
title: "Help for creating a split screen video."
date: 2008-04-23
forum: Multimedia Software
---

### Post by darkice on 2008-04-23
I have two video files recorded simultaneously. I want to edit them into one video file with non-standard resolution and a split screen view which, two videos can be seen together. I tried kdenlive but i was unable to change the output resolution.

Can anyone suggest me an application that i can edit a non standart resolution video file with split screen.

Thanks for your time.

---

### Post by marufaberlin on 2008-04-23
avidemux:

apt-get install avidemux

---

### Post by hellocatfood on 2009-11-23
> **marufaberlin said:**
> avidemux:

apt-get install avidemux

Do you know how to do this using avidemux?

---

### Post by cotcot on 2009-11-23
Blender VSE. 
Load both clips and use the [[COLOR="Red"]transform effect[/COLOR]]("http://wiki.blender.org/index.php/Doc:Manual/Sequencer/Effects") to scale them to the size you want. You can offset horizontally and/or vertically with the same transform effect. Google on blender wiki VSE for good tutorials on starting with the video sequence editor.

If you do not want to use blender, then search for PIP (picture in picture) effects in other editors.

---

