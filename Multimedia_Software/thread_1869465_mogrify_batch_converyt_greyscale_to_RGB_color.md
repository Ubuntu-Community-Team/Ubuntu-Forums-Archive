---
title: "mogrify: batch converyt greyscale to RGB color"
date: 2011-10-25
forum: Multimedia Software
---

### Post by LancerNZ on 2011-10-25
Anyone know the options for mogrify to batch convert a whole lot of greyscale PNGs to become RGB?

I'm wanting to set up a load of "colour by paint fill" exercises (for young kids) where the original images are black and while line art. The conversion from GIF to PNG auto greyscale-mode them all, and I'd like to quick-convert them to RGB so that they aren't all wondering why their bright green paint is showing up as dark grey when they hit the canvas.

I could open them all one at a time and manually set mode from Greyscale to RGB, but one at a time isn't as efficient as mogrify <options> *.png

*...but what are the correct setings?*

I've tried several options. As a simple example, what I have here are two files; "right.png" which is correctly saves as RGB and "wrong.png" which is greyscale. Here you can see the differenced in both filesize (25K rgb vs 18K grescale) and the "file" properties themselves.

```
lancer@lancer-laptop:~/pnglab$ ls -lah
total 56K
drwxr-xr-x 2 lancer lancer 4.0K 2011-10-25 23:07 .
drwxr-xr-x 3 lancer lancer 4.0K 2011-10-25 23:07 ..
-rw-r--r-- 1 lancer lancer  25K 2011-10-25 23:05 right.png
-rw-r--r-- 1 lancer lancer  18K 2011-10-25 23:06 wrong.png
lancer@lancer-laptop:~/pnglab$ file *
right.png: PNG image, 718 x 957, 8-bit/color RGB, non-interlaced
wrong.png: PNG image, 718 x 957, 8-bit grayscale, non-interlaced
```

That said... a couple of attempts among many, here attempting to use both mogrify and then convert to see if it makes any difference:

```
lancer@lancer-laptop:~/pnglab$ mogrify -colorspace rgb wrong.png 
lancer@lancer-laptop:~/pnglab$ file wrong.png 
wrong.png: PNG image, 718 x 957, 8-bit grayscale, non-interlaced

lancer@lancer-laptop:~/pnglab$ convert wrong.png -colorspace rgb fixed.png 
lancer@lancer-laptop:~/pnglab$ file fixed.png 
fixed.png: PNG image, 718 x 957, 8-bit grayscale, non-interlaced
```

...image never gets converted to "colorRGB". Mogrify is normally really good for batch operations to lots of images. I just can't see the options to convert to RGB once a png is already greyscale.


.....can't seem to figure out the right options though. Anyone know?

---

### Post by LancerNZ on 2011-10-26
Hmmmm - so I guess mogrify can't convert greyscale format to rbg.

---

### Post by papibe on 2011-10-26
Yes it can. Try this:
```
mogrify  -colorspace Gray yourpic.jpg
```
Hope it helps,
Regards.

---

### Post by LancerNZ on 2011-10-27
> **papibe said:**
> Yes it can. Try this:
```
mogrify  -colorspace Gray yourpic.jpg
```
Hope it helps,
Regards.

As shown in my previous example, that does not work.

I don't want to convert rgb to greyscale. I want the other way around and for PNG.

Mogrify reports no errors (appears to work) but it does not do it.

---

### Post by papibe on 2011-10-27
I apologize for the the confusion.

I just tested the following command adding the -type options, and it is working for me:
```
$ file file.png 
file.png: PNG image, 1944 x 2592, 8-bit grayscale, non-interlaced

$ mogrify **-type TrueColor **-colorspace RGB file.png 

$ file file.png 
file.png: PNG image, 1944 x 2592, **[COLOR="Red"]8-bit/color RGB[/COLOR]**, non-interlaced
```
Hope it helps now,
Regards.

---

### Post by LancerNZ on 2011-10-27
Fantastic! :D

I'm not at home at the moment and need to find a Linux box (or try later on) but your output there certainly looks like it does the job. Thanks so much. I was trying RGB everytihng, did not think to use TrueColor (must be an obvious reference I've missed).

I'll hop back on later and confirm if it does the trick my end.

---

### Post by LancerNZ on 2011-10-28
Okay - home now and have tested and it works :D

Thank you.

It turns out that -type TrueColor is the essential part, so all that is needed for batch conversion is...

```
mogrify -type TrueColor *.png
```

---

### Post by papibe on 2011-10-28
:D Great! Please mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you have the chance.
Regards.

---

### Post by LancerNZ on 2011-10-28
I did try, but I think the Tread Tool button to do so is broke. I don't get the option to mark as "solved" instead, Thread Tools just jumps to the bottom of the page.

And now it has a white triangle and the drop list is there. I wonder if it was because I had to make the last post? Dunno.

---

