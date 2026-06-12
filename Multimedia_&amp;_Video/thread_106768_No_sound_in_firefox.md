---
title: "No sound in firefox"
date: 2005-12-21
forum: Multimedia &amp; Video
---

### Post by Marle on 2005-12-21
I'm getting no sound at all in firefox. :( 

I get sound in every other application I've tried, and I've installed every codec I've ever heard of.  Videos play just fine, they just have no sound.  I've tried flash games, quicktimes movies, other types of movies, and just websites that have background sound and I hear nothing.  It's been this way since I upgraded to breezy a couple weeks ago and I just can't figure out why.  Can anyone help me?  :confused:

---

### Post by sciurus on 2005-12-24
This worked for flash sound in firefox for me:
open ~/.mozilla/firefox/rc
Add the line:
FIREFOX_DSP="none"

As an alternative solution, in a terminal enter
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

---

