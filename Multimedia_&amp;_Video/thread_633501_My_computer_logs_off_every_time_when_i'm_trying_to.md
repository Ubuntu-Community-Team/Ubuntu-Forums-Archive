---
title: "My computer logs off every time when i'm trying to do some rendering"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by 8_Ball on 2007-12-06
Hy!I have ubuntu 7.10 installed on my laptop (dell inspiron 1520) and i have a GeForce 8600 M GT video card.The problem is that every time I try to do some rendering (hit F12 in Blender) my computer logs off without any messages or warnings.I have compiz fusion installed and I am using the nVidia restricted driver.
Any help will be appreciated.(I don't want to use Blender on Windows)

---

### Post by 8_Ball on 2007-12-09
Hmmmm....nobody knows nothing? :(( So i must use Blender for Windows...:(

---

### Post by Whiffle on 2007-12-09
That tends to happen when your graphics drivers aren't working right.  But, you say compiz is running so that is where I get stumped.  Does glxgears work okay?

---

### Post by 8_Ball on 2007-12-11
Yep yep...compiz is working just fine...but I don't know how to test glxgears.

---

### Post by Red Moose on 2007-12-11
I would disable compiz while rendering.  You would probably get faster renders anyway.
Type glxgears in a terminal to test it.

---

### Post by 8_Ball on 2007-12-12
Thanks for your reply.

Ok...I've typed glxgears in terminal and it was ok....

$ glxgears
48937 frames in 5.0 seconds = 9784.480 FPS
58682 frames in 5.0 seconds = 11721.771 FPS
60774 frames in 5.0 seconds = 12137.530 FPS
59920 frames in 5.0 seconds = 11964.797 FPS
61041 frames in 5.0 seconds = 12195.509 FPS
X connection to :1.0 broken (explicit kill or server shutdown).

But still...trying to do some rendering in Blender logs off my computer..:(

---

