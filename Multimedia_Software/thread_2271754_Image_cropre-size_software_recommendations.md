---
title: "Image crop/re-size software recommendations?"
date: 2015-04-01
forum: Multimedia Software
---

### Post by remmas-sido on 2015-04-01
Hello guys 
I am looking for a software that re-size, or crop images for example if I want to use a specific wallpaper as a cover for my music files and that kind of stuff. Is there any?

---

### Post by ian-weisser on 2015-04-01
Command line: Imagemagick (you probably have it already). I use imagemagick frequently for resizes and cropping and convering formats.

Graphical: Gimp, available in the Software Center.

---

### Post by FakeOutdoorsman on 2015-04-01
If you're working with JPEG you can perform lossless cropping and rotation with jpegtran (looks like it's a part of the libjpeg-turbo-progs package).

```
jpegtran -crop WxH+X+Y -optimize -perfect input.jpg > output.jpg
```

See "man jpegtran" for more info.

---

### Post by SeijiSensei on 2015-04-02
The graphics viewer **gwenview** that comes with Kubuntu provides cropping and resizing facilities as well.  You don't need to run Kubuntu to use gwenview, just add it with "sudo apt-get install gwenview".  It will bring in a bunch of "dependencies," libraries it needs that come with KDE installations. 

Otherwise you can use **GIMP**, but that might be more complex than you need.  To resize, crop, and rotate images, look in the Image menu.  To select an area, hit Ctrl-B to bring up the Tool**B**ox and choose the rectangular selection tool at the top left of the toolbox.

---

