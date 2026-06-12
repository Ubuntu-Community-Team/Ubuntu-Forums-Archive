---
title: "Unsuported webcam"
date: 2010-06-17
forum: Multimedia Software
---

### Post by tashe on 2010-06-17
I just bought a web camer, Hantol HW-6682, but after opening it. I realized that it is only supported for Windows. I only have Ubuntu 10.04.
Is there any way to use it under Ubuntu?

Thank you

---

### Post by tashe on 2010-06-17
> **tashe said:**
> I just bought a web camer, Hantol HW-6682, but after opening it. I realized that it is only supported for Windows. I only have Ubuntu 10.04.
Is there any way to use it under Ubuntu?

Thank you

I'll relocated it to Hardware.

---

### Post by ajgreeny on 2010-06-17
Have you tried it with cheese or wxcam; it may work even if it says only supported by windows.

---

### Post by no2498 on 2010-06-18
cheese webcam booth should be loaded
look in sound & video for it

if it does not come on try this

open a terminal type, LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese 
click enter

if its still not on try this

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's


hope this helps

---

