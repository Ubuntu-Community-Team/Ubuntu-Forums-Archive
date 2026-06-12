---
title: "krandr causes blank screen"
date: 2009-11-19
forum: Multimedia Software
---

### Post by ismoore999 on 2009-11-19
I use krandr screen utility with my laptop quite often as for some reason the key sequence for CRT/LCD does nothing.

Recently after a meeting and on a flight, I started my laptop only to see a momentary glimpse of the screen at login followed by the screen going blank. 
I at first assumed it was still trying to display on the external monitor but connecting a monitor later made no difference.
I edited the kderesources to stop this being started at login and that worked but I observed two things 
1) that all of the existing applications were now very small (the windows being little bigger than the top corner of the icon)
2) that as soon as I started krandrtray, all went blank and there was nothing I could do.
Eventually tracking down the resource file in
~/.kde/share/config/krandrrc, the Rect parameter of the screens had been set to 0,0,0,0 (screen at 0,0, size 0,0)
I changed this to Rect=0,0,1024,768, logged in, and the screen was back to normal.

As this took a lot of time to find, if anyone else gets a similar issue, then perform the following:

1) log into a terminal session (CTRL + ALT + F1)
2) edit the file ~/.kde/share/config/krandrrc
3) you will see sections related to the screens you have
4) identify the problem screen and change the Rect= parameter to something sensible. To avoid issues, I set it to Rect=0,0,800,600 just to avoid refresh rates etc being an issue but if you know that is not a problem you can set it to whatever you want.

---

