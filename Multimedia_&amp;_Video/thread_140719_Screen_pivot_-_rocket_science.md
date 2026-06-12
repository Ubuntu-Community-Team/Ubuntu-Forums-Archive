---
title: "Screen pivot - rocket science?"
date: 2006-03-06
forum: Multimedia &amp; Video
---

### Post by Bartender on 2006-03-06
My PC set up with an Nvidia 9400-X, identified in xorg as GeForce MX4000 AGP 8X for some reason.
Have a Dell 1905FP monitor w/ the pivot thingie so you can stand the screen up in portrait.  Searched "pivot" but found just one or two fairly cryptic responses.  Assuming it's even possible, is it pretty tough for a newb to make pivot work?

---

### Post by rabidsnail on 2006-03-06
To rotate the screen, you could try:
```
xrandr -o right -s <width of new display>x<height of new display>
```
To find the avalable resolutionsm you could try 
```
xrandr -q
```.

I don't know how to tell if the actual display has been physically rotated, but you could put a custom launcher in the panel at the top of the screen with that command, to chance the rotation by clicking on it.

---

