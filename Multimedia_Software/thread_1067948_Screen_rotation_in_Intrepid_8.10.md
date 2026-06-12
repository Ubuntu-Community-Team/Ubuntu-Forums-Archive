---
title: "Screen rotation in Intrepid 8.10?"
date: 2009-02-12
forum: Multimedia Software
---

### Post by oldsoundguy on 2009-02-12
Has anyone been able to accomplish this?  This is the one thing I really NEED to be able to use and have been blocked at every turn (pun intended).  Using NVidia cards (various) on several machines and NONE able to rotate anymore.  (resolution is fine!) They worked fine in 7.10 and I hear they work in 8.04, so may step back to that version If I can not solve the issue.
Does the new 180 driver address the issue?  (other than the rotation, hate to mess with something that works "just to find out".)
Thanks.

---

### Post by jpeddicord on 2009-02-12
This thread or post has been moved from the Desktop Effects & Customization forum as the posted content is considered off-topic.

Desktop Effects & Customization is a forum for discussing:
[LIST]
[*]Compositing managers such as Compiz
[*]Themes (window themes, widget themes, backgrounds, etc)
[*]Appearance preferences
[/LIST]
Your post did not fit any of these categories, so it has been moved.

Common types of off-topic threads include:
[LIST]
[*]GNOME/KDE/XFCE help in general
[*]Hardware problems not directly related to compositing
[/LIST]

Thanks,
Jacob

---

### Post by roshanjose on 2009-02-12
try this:

[http://ossarchives.blogspot.com/2008/12/desktop-effects.html](http://ossarchives.blogspot.com/2008/12/desktop-effects.html)

---

### Post by oldsoundguy on 2009-02-12
jacobmp92 .. thanks was not sure where this would go .. but for all of those that have no IDEA what I am talking about .. it has nothing to do with rotating a cube or any of the screen tricks such as with compiz.
It has to do with changing the orientation of the monitor from Horizontal (landscape) to Vertical (portrait)(you have to have both a card and a monitor that is capable of doing so .. I have such.)
RandRotate worked in earlier versions .. all you had to do was add the line to the xorg .. does not work now!

---

### Post by 5BallJuggler on 2009-02-12
Have you tried using the Screen Resolution function in "Preferences"?

---

### Post by oldsoundguy on 2009-02-12
yea .. it lets me turn the image upside down.

I was hoping that somebody had been able to accomplish this in 8.11 ... I know that IF I blow that off and go to 8.04 it is SUPPOSED to work there because EnvyNG works on that build.  They gave up on 8.11 it appears.

---

### Post by accabrown on 2009-03-01
I can get it to change if I fiddle with xorg.conf and add "Rotate" "CCW" -- this is odd, since my screen actually rotates clockwise, but the direction has to be specified back-to-front. HOwever, I can't then change it from withinn screen preferences when gnome is running.

---

### Post by oldsoundguy on 2009-03-01
for me, I solved it .. by the way I mentioned.  Removed 8.10 and installed 8.04 and had the rotate working as soon as I added the "object RandRRotate yes" to the xorg.  Could not do that in 8.10.  
Really too bad the developers neglected that feature.

---

