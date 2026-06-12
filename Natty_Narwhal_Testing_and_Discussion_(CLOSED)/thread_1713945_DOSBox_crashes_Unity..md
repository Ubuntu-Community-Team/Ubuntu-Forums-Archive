---
title: "DOSBox crashes Unity."
date: 2011-03-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by JRV on 2011-03-24
When running DOSBOX in Unity, if you use <CTRL>-<ALT>-<Enter> to make it fullscreen the window quits working.  Then when you try to close it the screen goes black with an enlarged mouse pointer.  At this point the only way out is <CTRL>-<ALT>-<Backspace>. (If you have it enabled.)  This applies to 3d Unity only, it works as exoecter in Unity2d.

---

### Post by kostkon on 2011-03-24
First of all, what graphics output do you use in dosbox (it happens to be a sdl-based app)?

To find out, open your dosbox configuration file (you will find it in the .dosbox hidden folder that resides in your home folder, i.e. *~/.dosbox/dosbox-0.xx.conf*) and check for the line that says e.g.

```
#           output: What video system to use for output.
#                   Possible values: surface, overlay, opengl, openglnb.
.
.
.
output=surface
```
Try changing it to one of the other available values.

For example,  Unity is compiz based, thus try changing the output to *opengl*.

Also, do you use the original game res when going to full screen or a fixed one. Try setting a fixed one (for example, the default res of your desktop/monitor), i.e.
```
#   fullresolution: What resolution to use for fullscreen: original or fixed size (e.g. 1024x768).
.
.
.
fullresolution=original
```

---

### Post by JRV on 2011-03-28
Thank you, that did it.
I'm sorry it took so long to get back to you, I got too busy to play old games.

Thread marked solved.

---

