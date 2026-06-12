---
title: "OpenGL problem, likely due to my graphics driver"
date: 2008-02-12
forum: Multimedia &amp; Video
---

### Post by GreaterCore on 2008-02-12
I have tried running Wine for quite a while with no success. My guess is that there is something wrong with the OpenGL libraries. I recently compiled an OpenGL program and my suspicions were confirmed.

I am getting the following error after successfully compiling the OpenGL program downloaded from [http://nehe.gamedev.net/data/lessons/lesson.asp?lesson=03](http://nehe.gamedev.net/data/lessons/lesson.asp?lesson=03).

This is the error message I am getting.

> Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
freeglut (./lesson3):  ERROR:  Internal error <Visual with necessary capabilities not found> in function fgOpenWindow
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  4 (X_DestroyWindow)
  Resource id in failed request:  0x0
  Serial number of failed request:  24
  Current serial number in output stream:  27


It appears I am still pretty screwed over by the ATI drivers that I am using. I am currently running an ATI Mobility 9000 (M9) graphics card on my laptop. It is extremely unlikely that I can change it.

Will running the free drivers allow me to use OpenGL while maintaining the dual screen feature?

---

### Post by hardyn on 2008-02-12
allways helps to read late and great with the Radeon driver, but no, i think it is a pretty basic driver.

you did not specify what hardware you had; some dells, did have descrete video cards, actually, alot of them did.  But no, i would not get my hopes up about a descrete video.

as a side bar, my notebook DOES have a removeable video component, however, Asus never did make a replacement.

---

