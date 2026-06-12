---
title: "Ancient Logitech Express (046d:0850) Webcam with low FPS, how to fix?"
date: 2010-07-19
forum: Multimedia Software
---

### Post by jared650 on 2010-07-19
I have an ancient Logitech Express webcam (046d:0850) that worked immediately when I installed 10.04 Lucid Lynx, except for a frame rate issue. GUVCVideo has the frame rate at between 1-3 fps. I'd like to see it at between 25-30. The video options within guvcvideo DO NOT allow me to adjust the frame rate, resolution, or auto-exposure.

Cheese works, skype works, and camorama doesn't. All functioning programs have the fps issue.

Any ideas? In searching around, all I've found is some wild goose chases promising pots of gold that some leprechaun must have stuffed up his keister because they don't work for me.

Thanks in advance!

---

### Post by jared650 on 2010-07-20
Hm... tried some other stuff, to no avail. Ideas anyone?

---

### Post by gordintoronto on 2010-07-20
I doubt very much that you will convince this webcam to perform in a way it was not designed to perform.

---

### Post by jared650 on 2010-07-20
> **gordintoronto said:**
> I doubt very much that you will convince this webcam to perform in a way it was not designed to perform.

Well, it performs fine in Windows. It only has this low FPS issue in Ubuntu. If there were some way to manually up the FPS I would be set, but I haven't found that fix.

---

### Post by no2498 on 2010-07-21
you may try changing the plugin in gstreamer-properties

the how to is in cheese's help faq's

it may or may not help

i just found out that gspca does not load in/on 910 karmic

my cam does 5fps

good luck

---

