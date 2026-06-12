---
title: "[SOLVED] Break one big image file into smaller 32x32 image files?"
date: 2008-12-28
forum: Multimedia Software
---

### Post by crazyfuturamanoob on 2008-12-28
I got a large image file (256x32) I wish to cut down into smaller ones, (32x32).

Of course this could be done in gimp, but it would be annoying and take a lot time.

So maybe there's a program to do this task?

---

### Post by amac777 on 2008-12-28
I only know how to do it in Gimp. But it's not that annoying and shouldn't take a lot of time so I wonder if this still might help you:

1. Image -> Guides -> New Guide
2. Set 7 new Vertical guides at pixels #s: 32, 64, 96, 128, 160, 192, and 224
3. Image -> Transform -> Guillotine

That will create eight new windows of the 32x32 sections you wanted. You can save them directly as they will have the file name of the original with a unique sequence number.

---

### Post by crazyfuturamanoob on 2008-12-28
But I want a program to do this. I got so many files to edit. 
Doing it with gimp will take a lot time and get on my nerves.

---

### Post by amac777 on 2008-12-28
Ok, well, check out image magick:

[http://www.imagemagick.org/script/command-line-processing.php](http://www.imagemagick.org/script/command-line-processing.php)

there is a crop command so with a little work you could probably write a script to do what you need to do for all your files.

---

### Post by crazyfuturamanoob on 2008-12-29
Edit: 
Found help from here: [http://www.vbulletin.com/forum/showthread.php?t=76653](http://www.vbulletin.com/forum/showthread.php?t=76653)
Somebody was trying just to resize an image, but he accidentally did what I want. :D
So the command is as simple as "mogrify -crop 32x32 filename".

---

