---
title: "VLC problems"
date: 2009-05-14
forum: Multimedia Software
---

### Post by bossa on 2009-05-14
Hi All

I have a couple of problems with VLC after installing the skins file from the VLC site . Worked ok for a while and then after changing a skin things started to go wrong. VLC invariably launches two instances also I cannot edit the preference ( they wont open) . Cant do full screen and a number of other options.I have tried purging and re installing and that does not fix it .Also looking in home with hidden files there is no VLC folder.Tried deleting the Skins file but that dont work either.Also if after closing the two VLC's,looking in system monitor ther are usually one or two instances of VLC sleeping.
Any ideas ?

---

### Post by bossa on 2009-05-15
Just in case anyone else found themselves in my predicament this i what I used to fix the problem 

Very simple fix, in a terminal
vlc --reset-config

I think this will fix all manners of problems that one might get into when tweaking VLC, just to get you back to the start
Cheers ;)

---

### Post by binbash on 2009-05-15
for two instances : [http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html](http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html)

---

