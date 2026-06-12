---
title: "Forcing mod 16 resolution when encoding with mencoder"
date: 2008-08-24
forum: Multimedia Software
---

### Post by sumpm1 on 2008-08-24
Hi. I am using Mencoder from the command line to convert some videos. Eventually I want to be able to batch encode in this manner. Using the options -vf scale -zoom -xy 512, it will resize the video to have a resolution width of 512 and then automatically calculate the vertical resolution for me.

This is very useful for backing up old stuff to lower res, cause you don't have to know the original resolution and it will just resize all of your videos to a fixed width, and allowing you to save some diskspace.

The problem that I am having is that videos should be encoded with resolution width and heights that are both multiples of 16 (mod 16). Is there any command to force Mencoder to use a mod 16 resolution?

Thanks

---

### Post by sumpm1 on 2008-08-25
bump

---

### Post by BRAXS69 on 2008-12-18
i only just recently need to know this as well and i found the solution.
[http://www.videohelp.com/forum/archive/force-mencoder-to-use-mod-16-resolution-t355700.html]("http://www.videohelp.com/forum/archive/force-mencoder-to-use-mod-16-resolution-t355700.html")
 
hope it helps.

---

