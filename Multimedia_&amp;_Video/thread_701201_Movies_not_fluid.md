---
title: "Movies not fluid"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by Fatal1ty on 2008-02-19
Hi guys....this is my first post here...
I'm new using ubuntu...and I need some help, here is the problem:
I installed the xvid/divx codec for totem, but when I play the movie if the windows is not maximized the movie is fluent...but when I maximize the windows to "all the screen" it's not fluet, it lose frames...
Anyone can help me?
Thx...
sorry for the bad english!

---

### Post by aeiah on 2008-02-19
what are your computer specs? do you have the restricted drivers for your video card? have you tried other video players? (like vlc)

---

### Post by Fatal1ty on 2008-02-19
My pc is an AMD 3500+,1024 Mb ddr, x1950xt 
I've tried with totem, mplayer and vlc...with the same result...
I've got the restricted driver installed...(compiz work properly)
any suggestion?

---

### Post by aeiah on 2008-02-19
do videos run smoothly with compiz turned off? there are settings in each one to use opengl / xgl / whatever for videos to get them running well in compiz, but its easier to see if compiz is the culprit by just turning it off to test

---

### Post by Fatal1ty on 2008-02-19
I've tried turning off compiz by going in system->preference->aspect->visual effect>none
but it doesn't change anything!
is the method of turning compiz off right? or should I do it in another way?

---

### Post by aeiah on 2008-02-19
im not sure if that truly turns it off or just turns the effects of compiz off. if you're using the gnome desktop (ie, ubuntu instead of xubuntu or kubuntu) then you can do

metacity --replace

and to turn compiz back on do

compiz --replace

---

