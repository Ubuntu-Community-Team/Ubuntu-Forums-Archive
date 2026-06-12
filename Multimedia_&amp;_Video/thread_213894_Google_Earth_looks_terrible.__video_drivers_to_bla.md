---
title: "Google Earth looks terrible.  video drivers to blame?"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by jbm222 on 2006-07-11
Google Earth worked fine on my laptop when i had windows installed.  It's pretty much worthless now.  It renders everything correctly when I first load it, but then I start getting ghosts of previous images that don't go away, and the navigation control overlays get all messed up.  so about 1/2 of the screen still shows video correctly.

Could this be a video card issue?

---

### Post by Raistlin355 on 2006-07-11
> **jbm222 said:**
> Google Earth worked fine on my laptop when i had windows installed.  It's pretty much worthless now.  It renders everything correctly when I first load it, but then I start getting ghosts of previous images that don't go away, and the navigation control overlays get all messed up.  so about 1/2 of the screen still shows video correctly.

Could this be a video card issue?

Kinda sounds like it to me, out of curiosity what video card do you have?

---

### Post by jbm222 on 2006-07-11
Honestly, i'm not complete sure.  Integrated w/ the mobo (laptop).  It's a peice of junk, but i've never really had problems with it until now, so i never looked.

lspci gives me this:

0000:00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphi cs Device (rev 01)

is that useful?

---

### Post by Raistlin355 on 2006-07-12
First I believe that you are having a driver issue if you haven't try installing the drivers at:
[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=922&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=922&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

I would download the first driver on the list as its the latest, you'll have to compile it ubt they come with instructions, so it's pretty easy.

I am curious if your card supports OpenGL and is still trying to use DirectX to render Google Earth.  You might see if you can change the renderer to OpenGL instead of DX.

Ok so, I did a little searching in the forums based on the video card you have and found 22 threads that mention it:

[http://ubuntuforums.org/search.php?searchid=6698946](http://ubuntuforums.org/search.php?searchid=6698946)

You might search around that a little and see if you can find a solution.

Hope I've been able to point you in the right direction!!

---

