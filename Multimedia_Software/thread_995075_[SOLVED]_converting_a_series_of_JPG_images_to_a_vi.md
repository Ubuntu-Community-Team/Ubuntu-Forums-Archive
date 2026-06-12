---
title: "[SOLVED] converting a series of JPG images to a video"
date: 2008-11-27
forum: Multimedia Software
---

### Post by stooshbunutu on 2008-11-27
Hello All,

As a photography project I have a series of photographs which I want to put into a video, around 5 frames per second.

My computer is low spec so I want to use command line rather than a GUI such as Stopmotion.

I have looked into tutorials online for ffmpeg and mencoder but have had no success.

The files are numerically named (001.JPG, 002.JPG, ..., 150.JPG). I want some kind of way of converting the images to a video (format not important, so long as it works).

Also some of the JPG files are larger than others, so some kind of resize parameter may be useful (around 3:2 width:hight) ratio in all).

All help greatly appreciated.

---

### Post by little_penguin on 2008-11-27
You can use **manslide** for this, it creates a slideshow movie of a collection of images. It's easy to use and you can specify slide transition times and effects. It's also in the repositories if you want to try it out.

---

### Post by stooshbunutu on 2008-11-27
> **little_penguin said:**
> You can use **manslide** for this, it creates a slideshow movie of a collection of images. It's easy to use and you can specify slide transition times and effects. It's also in the repositories if you want to try it out.

Thanks, but as previously stated I need a non GUI way of doing this as my computer is old and slow, I have found GUIs capable of doing this but they seize up and crash when loading images because my computer just can't handle it.

---

### Post by little_penguin on 2008-11-27
Oops, I missed that. **dvd-slideshow** is a command line tool you could use, that's also in the repos.

---

### Post by stooshbunutu on 2008-11-27
> **little_penguin said:**
> Oops, I missed that. **dvd-slideshow** is a command line tool you could use, that's also in the repos.

Cheers for that, any idea where I can find documentation, or do u know a simple command to get me started, cheers

---

### Post by stooshbunutu on 2008-11-27
> **stooshbunutu said:**
> Cheers for that, any idea where I can find documentation, or do u know a simple command to get me started, cheers

not to worry, found some from the file

---

### Post by little_penguin on 2008-11-29
I haven't actually used dvd-slideshow myself, but the following command will get you the manual page, which gives details of usage and some examples:

```
man dvd-slideshow
```

You can also redirect the command output into a file, which you can print and read more conveniently:

```
man dvd-slideshow > filename
```

---

### Post by stooshbunutu on 2008-11-29
Cheers for the help, it seems to work, well, hangs every now and then but I reckon that's just my slow laptop.

---

### Post by little_penguin on 2008-11-30
That's great :-)

---

### Post by stooshbunutu on 2008-12-07
if you interested here's the video I made with the software

[http://uk.youtube.com/watch?v=YJaCXcOL3ys]("http://uk.youtube.com/watch?v=YJaCXcOL3ys")

---

