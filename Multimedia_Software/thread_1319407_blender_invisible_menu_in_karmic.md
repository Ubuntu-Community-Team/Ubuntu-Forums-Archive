---
title: "blender invisible menu in karmic"
date: 2009-11-08
forum: Multimedia Software
---

### Post by stupiduser on 2009-11-08
hi
i'm having a problem with blender, it doesn't show the menu,
the menu exist somehow, i can click it, but they are invisible 
[IMG]http://www.pasteall.org/pic/show.php?id=54[/IMG]

i'm using blender 2.49a+dfsg-0ubuntu2(karmic)
Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller(graphic card)

i'm able to show the menu by using "LIBGL_ALWAYS_SOFTWARE=1 blender"
**but is there any other way? **because i heard using "LIBGL_ALWAYS_SOFTWARE=1 blender" will make the game mode slow

thank you for your time

---

### Post by JevonPenguin on 2009-11-08
I have been having similar problems, but with parts of blender completely disappearing.
[http://ubuntuforums.org/showthread.php?t=1319338](http://ubuntuforums.org/showthread.php?t=1319338)

How did you do that LIBGL_ALWAYS_SOFTWARE=1 blender ? Maybe that would solve my problems, as I never use the game mode

---

### Post by stupiduser on 2009-11-09
just type "LIBGL_ALWAYS_SOFTWARE=1 blender" in the terminal

another note, if you want to create shortcut of the command you must use the shell script, ordinary launcher command won't work

---

### Post by JevonPenguin on 2009-11-10
Not a perfect solution, but it worked!

You can also add -LIBGL_ALWAYS_SOFTWARE=1 to the command in the menu like:
/location of blender executable -LIBGL_ALWAYS_SOFTWARE=1 
and it works fine. As you mentioned, a little slower on the overall performance, but a vast improvement over refocusing the screen every two seconds. Hope this helps out other blender users as well.

---

### Post by stupiduser on 2009-11-11
hi JevonPenguin,
found out today that my intel, dri, and etc etc driver are still using the ppa jaunty version(stupid me :p).
so i downgrade all of them to the karmic default version, and my invisible menu has became visible again, so happy :p.
hope it could also fix your problem

---

