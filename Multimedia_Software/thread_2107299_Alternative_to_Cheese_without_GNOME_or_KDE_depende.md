---
title: "Alternative to Cheese without GNOME or KDE dependencies?"
date: 2013-01-21
forum: Multimedia Software
---

### Post by mishagale on 2013-01-21
Hullo all,

I'm trying to find a simple "photobooth" type application (something that will let you capture a still image from a webcam) which I can install on my Lubuntu powered netbook, without needing to install a huge amount of Gnome or KDE dependencies.

The only ones I can find are Camorama, Kamerka and Cheese, all of which require either GNOME or KDE, and I'm trying to minimise disk space usage.

Is there a package available which works with OpenBox? Alternatively, is it possible to recompile one of the above packages without installing all the Gnome/KDE libraries?

EDIT: I found a sort-of solution, by using ffmpeg at the command line, but it means you don't see the image before you capture it. If such doesn't already exist, perhaps I will write some kind of GUI wrapper around ffmpeg for this purpose.

```
ffmpeg -f video4linux2 -r 25 -s 640x480 -i /dev/video0 snap.png
```

EDIT2: Or, somewhat better:
```
avconv -f video4linux2 -i /dev/video0 -vframes 1 snap2.png
```

---

### Post by tilii on 2013-01-21
guvcview might be worth a try? :)

---

### Post by mishagale on 2013-01-21
That seems to work quite well, thanks. A minor problem is that you can't fit the display and the controls into a netbook display, and there is no keyboard shortcut to capture a picture, but otherwise works pretty well.

Another alternative I found was to use GNOME MPlayer and "Open Analogue TV" (which seems to correspond to /dev/video0) and use Ctrl-T to take a screenshot.

---

