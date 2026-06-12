---
title: "Compiling a numbered image sequence to a video file"
date: 2009-10-06
forum: Multimedia Software
---

### Post by starbase1 on 2009-10-06
Are there any tools for Ubuntu that will take a numbered sequence of image files, such as pic001.jpg, pic002.jpg, etc, into a video file?

I've tried a couple of video progs, but no luck so far...

Bonus points if it will handle big HD images, and even more bonus points if I can throw in a soundtrack file at the same time!

Thanks,
Nick

---

### Post by MartyBuntu on 2009-10-06
Have you tried **Stopmotion**? It's in the repositories.

---

### Post by starbase1 on 2009-10-06
> **MartyBuntu said:**
> Have you tried **Stopmotion**? It's in the repositories.

Ah, I had not heard of that - the name alone is enough to be encouraging, thanks!

Nick

---

### Post by PeterVR on 2010-06-16
Stopmotion looks very promising!
Thanks

---

### Post by gnarly_buttons on 2010-06-17
Have you gotten it to export to a video file? I've tried and tried, but I can't figure it out.

---

### Post by manosx on 2010-10-20
I am suggesting **luciole**.
It is in synaptics and it is the only one that worked for me out of the box without crashing and very easily..

Get it by:
> sudo apt-get install luciole

tip:
you can change the size of the images with the jpegoptim program

example: jpegoptim --max=50 *

m~

---

