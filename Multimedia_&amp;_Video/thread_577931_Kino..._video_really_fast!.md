---
title: "Kino... video really fast?!"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by JRevell on 2007-10-16
Hello all.
I'm trying to edit a video, but when ever I import my .avi files, which I got from my Canon PowerShot A510, the speed of the video is ridiculously fast. 2 minutes reduced to a couple seconds. Anyone no whats up? :confused:

---

### Post by Tuxi on 2007-12-22
I had a similar problem earlier today.  I estimate the speedup to be 6 times.

I reboted into the generic kernel (2.6.22-14-generic) and kino plays the files at the proper speed now.

I was running the 386 kernel (default in GRUB) because the NVidia driver wouldn't work with the generic kernel.  I changed to the nv driver and all is OK using the generic kernel.

---

