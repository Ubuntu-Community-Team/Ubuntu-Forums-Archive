---
title: "can't open gstreamer-properties"
date: 2010-05-23
forum: Multimedia Software
---

### Post by suckerpunch on 2010-05-23
I was trying to fix a blue tint problem so I opened gstreamer-properties from the terminal. Following some directions from another thread, I changed the output to "custom" and filled in a box with a bunch of code that I didn't know anything about. I pressed "test" and it didn't work. Out of frustration, I deleted the text I had written in the box and closed gstreamer-properties.

Now it won't open back up. When I try to open it from the terminal i get:

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
Segmentation fault

That's it. It won't open and when I try to open it directly from its source folder, nothing happens at all.

How can I open it back up so I can continue to fiddle with it and (hopefully) fix this blue-tint problem.

Thanks a lot!!!

---

### Post by no2498 on 2010-05-23
you may try sudo gstreamer-properties

---

### Post by no2498 on 2010-05-23
btw if the blue is from a video you clicked on line
open totem click edit preference reset the display to defaults
or move the sliders and reset

---

### Post by suckerpunch on 2010-05-25
Sudo worked!! Thanks no2498!

---

