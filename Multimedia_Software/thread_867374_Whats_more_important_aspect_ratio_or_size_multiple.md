---
title: "Whats more important aspect ratio or size multiple of 16?"
date: 2008-07-22
forum: Multimedia Software
---

### Post by mikeym on 2008-07-22
Hi,

I'm working on a script for converting DVD's / video files to x246 and I want to know what's more important keeping my aspect ratio or my widths and heights as multiples of 16?

I can either use mencoder to calculate my aspect with

-vf scale=640:-2 

or calculate it as a multiple of 16 and put that in

SCALE=704/416=1.69
WIDTH=640
HEIGHT=640/SCALE=378.1
ADJUSTED_HEIGHT=round( HEIGHT / 16 )*16=384

and then 

-vf scale=640:384

Which is better?

---

### Post by scragar on 2008-07-22
I'd keep aspect ratio, that way problems with widescreen and non-widescreen don't cause huge problems with distorted pictures. Unless I'm missunderstanding you here.

---

### Post by mikeym on 2008-07-22
Slightly,

as I'm talking about calculating the height to the correct aspect ratio and then adjusting it to ensure that it's a multiple of 16.

So in my example the adjustment to the height to make it a multiple of 16 is 5.9 pixels.

---

### Post by scragar on 2008-07-22
no-one is going to notice 5 or 6 pixels when the height is over 300, it's too small for people to notice unless you point it out to them.

---

### Post by mikeym on 2008-07-22
That's right but would players notice the change in aspect ratio? How important is it important to keep the ratio of 16 for sizes?

---

