---
title: "OpenGL error"
date: 2011-02-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by taotree on 2011-02-11
If you have ghc installed, you can run this to reproduce the problem:

curl [http://ix.io/1t6](http://ix.io/1t6) > Stroke.hs; ghc --make Stroke.hs; ./Stroke

It flashes a window and then closes with:
"unknown GLU entry gluOrtho2D"

According to one guy, this example has worked for 15 years and works on two other systems tested.

---

### Post by taotree on 2011-02-11
I'm guessing it's because I just upgraded to natty, and I didn't upgrade nvidia drivers (I'm using the ones downloaded from nvidia.com). And when I try to installed the nvidia ones, X wouldn't start anymore. I saw something about an error about incompatible ABI?

---

### Post by cariboo on 2011-02-11
Check out [this]("http://ubuntuforums.org/showthread.php?t=1675614") thread.

---

