---
title: "Xine-Based Apps Producing Weird Picture"
date: 2006-12-13
forum: Multimedia &amp; Video
---

### Post by BarfBag on 2006-12-13
When I watch a DVD or play a video clip in Xine-based players, the picture is all weird.  Nothing major (sure bothers me, though).  It's so hard to describe too.  Let me try and capture it with a screen shot...

...done!

[[IMG]http://img237.imageshack.us/img237/8792/weirdlines2on8.th.png[/IMG]](http://img237.imageshack.us/my.php?image=weirdlines2on8.png)

See the lines?  Those appear like that whenever there's movement such as walking, running, or simply the person doing something fast.

DMA is enabled, and this happens with everything.  In VLC, it's fine.

---

### Post by tbroderick on 2006-12-13
Have you tried using a different video driver?

---

### Post by BarfBag on 2006-12-13
> **tbroderick said:**
> Have you tried using a different video driver?

No.  I'm just using the last stable nVidia driver.

---

### Post by tbroderick on 2006-12-13
Open your xine based player like gxine. Go to File -> Configure -> Preferences. First you have to change the 'experience level' setting to something other then Beginner. Advanced will do nicely. This will allow you to see more configure options. Specifically a 'video' tab. Click on the 'video' tab. You should then see an option to change the video driver. By default it should be on 'auto'. Try changing to 'opengl' or 'opengl2' if you are using XGL.

---

