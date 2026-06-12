---
title: "Cinelerra Render Settings"
date: 2010-02-25
forum: Multimedia Software
---

### Post by merlync70 on 2010-02-25
Hello,

I have 2 machines.  My desktop is a Quad Core processor with 4 GB RAM, and about 2 yrs old.  My laptop is a Dell Inspiron 1420 (3 yrs old).  

I am running Cinelerrasv-smp on both machines and am using the same settings.  I have been youtube-ing tutorials that helped me configure settings, etc. and everything works great. 

The issue that I am having is that I added my endcredits.png file to the project, pasted it to the timeline, used keyframes to do the scrolling action, and rendered the project.
My desktop takes about 3 minutes to render and the output is excellent.  Smooth scrolling motion.
My laptop takes 11 seconds to render exactly the same thing.  The output on it is very choppy.  It doesn't scroll, so much as jumps.  It does so in very even methodical movements, so it seems like its not filling in the motion.  It seems as if the line from keyframe A to key frame B is not a smooth line, but rather a stairstep (hopefully that makes sense).

I suspect that Cinelerra is scaling down the rendering to match my laptop.  I would have expected my laptop to take much longer to process and give the same quality of finished product... but it is not.  It renders much faster with much worse results.

What settings do I need to make higher quality renders on my laptop?

---

### Post by wildhostile on 2010-02-27
Hi merlync70,

That's weird but interesting.
As this is not directly related to ubuntu (I think), I would suggest you to ask the question on the CinelerraCV maillinglist ==> [http://cinelerra.org/mailinglists.php](http://cinelerra.org/mailinglists.php) .

Roland.

---

