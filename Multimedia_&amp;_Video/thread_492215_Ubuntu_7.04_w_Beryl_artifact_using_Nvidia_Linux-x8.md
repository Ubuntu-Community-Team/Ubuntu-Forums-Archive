---
title: "Ubuntu 7.04 w/ Beryl artifact using Nvidia Linux-x86 100.14.11 on a 6800GTO"
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by SGI on 2007-07-04
I have 6 Horizontal Virtual Size (Hexagon) in Beryl ... except on the "main" desktop window, all my other virtual desktop is showing artifacts (see picture below) whenever I move/minimize... or even when I open the Application/Places/System menu etc.   I always have some artifact from the previous previous frames (it appears that the video card didn't redraw the background)

[IMG]http://i194.photobucket.com/albums/z20/emailsgi/artifact.png[/IMG]

If any guys can offer any help, it will be great.  Thanks.


-=SGI=-

---

### Post by SGI on 2007-07-05
Hi all,

I'm answering my own question now since I got it to work and to help others who might run into this problem.   The reason for the ghosting images that is shown in the picture in my initial post was that I had no wallpaper (except for the first "desktop") and I had set the Transparency to 100 for Opacity When Not Moving under Desktop Cube.  The way to fix it was to simply change the Opacity When Not Moving to 99 or lower!  

(Do I smell a bug here in Beryl? - No Wallpaper on the "Virtual Desktops" with Opacity When Not Moving set to 100 will not let the video card "redraw" itself in "virtual desktops" when you have moving image which will end up with a ghosting effect)

Anyway, I have since added a skyview and the same wallpaper to all the desktops by turning off "Desktop manager supports viewports" options under the General Options (I guess GNOME doesn't support multiple viewports/wallpapers) - if anyone know how to do it otherwise, please let me know.  :)


-=SGI=-

---

