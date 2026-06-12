---
title: "[SOLVED] low resolution (640x480)  nvidia-glx-new with 8600 GT"
date: 2008-05-29
forum: Multimedia Software
---

### Post by procreative on 2008-05-29
Dear Colleagues,

I need a help regarding the new driver nvidia-glx-new using it on Ubuntu 8.04 with GNOME. The activation of the package nvidia-glx-new running successful, but after I restart the PC. The highest screen resolution is 640x480x50Hz :(. And no other resolution is available in the system program "Monitor Resolution Settings".
When I deactivate the package nvidia-glx-new, the I have 1248x800x60Hz, but the monitor could show also an highest resolution. The graphics card NVIDIA 8600GT can use much higher resolutions.
Sorry for the amateur question, but I have no idea what to do. :confused:

Thanks

---

### Post by Ubuginer on 2008-05-29
> **procreative said:**
> Dear Colleagues,

I need a help regarding the new driver nvidia-glx-new using it on Ubuntu 8.04 with GNOME. The activation of the package nvidia-glx-new running successful, but after I restart the PC. The highest screen resolution is 640x480x50Hz :(. And no other resolution is available in the system program "Monitor Resolution Settings".
When I deactivate the package nvidia-glx-new, the I have 1248x800x60Hz, but the monitor could show also an highest resolution. The graphics card NVIDIA 8600GT can use much higher resolutions.
Sorry for the amateur question, but I have no idea what to do. :confused:

Thanks

You may wan to try this to see it'll help

In terminal type: sudo -s displayconfig-gtk

This is how I got my 7300 GT to work.

---

### Post by Istonian on 2008-05-30
That did work for me, but my problem is my fonts look absolutely horrid. If I could fix them that would be great. Any ideas. 

What is weird is my monitor resolution was picked up automatically until one day I booted it up and saw that my resolution was at 640x480. Not even reinstalling fixed this. Weird...

---

### Post by procreative on 2008-05-30
> **Ubuginer said:**
> 
In terminal type: sudo -s displayconfig-gtk


Thank you very much. :-D 
That was the solution.
Best Regards ):P

---

