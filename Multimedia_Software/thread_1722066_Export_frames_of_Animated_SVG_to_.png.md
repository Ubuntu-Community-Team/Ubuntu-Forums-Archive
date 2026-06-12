---
title: "Export frames of Animated SVG to .png?"
date: 2011-04-05
forum: Multimedia Software
---

### Post by dalovering on 2011-04-05
I made an animated .svg (which uses the animateTransform key) and I can't seem to find any way of getting rendered frames out of it. Does anybody know a good way of getting these frames?

---

### Post by SeijiSensei on 2011-04-05
If you can play the file with mplayer (I don't know anything about SVG), you can create a sequence of png's like this:

```
mplayer -vo png -ao null /path/to/the/file
```

That will convert the frames and store the png files in the current directory.

You can use the "-ss hh:mm:ss" and "-endpos N" options to start at a particular timestamp and end "N" seconds later.

---

### Post by dalovering on 2011-04-05
no dice, MPlayer doesn't support SVG :(

---

### Post by SeijiSensei on 2011-04-05
A little googling shows that [ImageMagick]("http://www.imagemagick.org/") can convert from svg to png, but I don't know whether it handles an animated svg.  I presume the images are layers like in animated gifs?  Maybe the documentation at the ImageMagick site can give you some alternatives.  If you don't have IM installed already, it's in the repositories.

---

### Post by dalovering on 2011-04-06
That's the problem though, there aren't any "frames" IN the svg. what you do is you tell it to rotate an object at a certain speed, etc. You can also control the speed based off of a curve, which is nice. But anyways, Imagemagick won't handle it, thought that was my first thought.

---

