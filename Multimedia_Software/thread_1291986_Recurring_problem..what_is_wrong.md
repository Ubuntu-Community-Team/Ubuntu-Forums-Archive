---
title: "Recurring problem..what is wrong"
date: 2009-10-15
forum: Multimedia Software
---

### Post by vipulkelkar on 2009-10-15
Suddenly the size of the fonts and icons has gone bigger..I started my pc and it was all in big fonts like a resln less than 800x600
I am using 9.04
I faced the similar problem on 8.04 a few days back..It was working fine a few hours back

What is the problem

I am not able to set the resolution also

When i go to the prefernces->display   it says that the graphics driver does not support necessary extension

and when i press yes it opens nvidia x server settings

I am using GeForce 6150 card with driver version 180 installed

Please help me out

---

### Post by vipulkelkar on 2009-10-15
It is saying monitor not detected..if i go in the regular DISPLAY tool

---

### Post by Niko Johnson on 2009-10-15
try to run this command as root ```
 nvidia-xconfig 
``` then log out and back in to see if it worked it should change your /etc/x11/xorg.conf file accordingly

---

### Post by vipulkelkar on 2009-10-15
i changed the resolution...no changes have occurred...
9.04 graphics have totally been screwd..

---

