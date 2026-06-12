---
title: "Corel PhotoPaint 9 wont install on Karmic?"
date: 2009-11-09
forum: Multimedia Software
---

### Post by sroland81 on 2009-11-09
Hi guys, i downloaded an installer .tar.gz of Corel Photo Paint 9 and extracted it. Then executed "sudo ./install"... and there is one error... The terminal output is this:

santiago@hyperion:~/Downloads/corelinstaller/CorelPHOTOPAINT9Lnx$ sudo ./install 
Log file name:/tmp/corel/Setup.log
Qt: Locales not supported on X server
X Error: BadValue 2
  Major opcode:  18
Aborted

Any ideas?

Thanks,

---

### Post by sroland81 on 2009-11-20
Hey.. does anybody installed Linux version of Corel Photo Paint in Ubuntu?

Thanks,

---

### Post by HappyFeet on 2009-11-20
```
Qt: Locales not supported on X server
```
Locales refers to languages supported on your computer. There is a conflict because you don't have proper support.

I just found out corel photopaint 9 is very old. Have you tried GIMP for what you want to do?

---

### Post by sroland81 on 2009-11-22
i'm looking for a software that handles objects, in which you can insert images like objects and apply transparency to. write text, insert figures, brushes... no layers. GIMP has no support for object handling and layer management is dark and confsue. Corel had an object list sidebar that was the best way to compose images and add effects... similar software is Xara Xtreme but it lacks of lots of things and transparency and other things are very experimental and SVG export doesn't work at all. also tried InkScape but again, it is for drawing and you can't open a picture for retouching and add objects... still experimenting with it anyway...

any ideas?

---

### Post by nekrozzz on 2011-04-25
I've the same problem with Photo-paint installation. Do anyone install it?

---

### Post by mörgæs on 2011-04-26
Have you tried Gimp? 
There are lots of tutorials on Youtube.

---

