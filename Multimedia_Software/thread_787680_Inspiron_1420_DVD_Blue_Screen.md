---
title: "Inspiron 1420 DVD Blue Screen"
date: 2008-05-09
forum: Multimedia Software
---

### Post by thyquest on 2008-05-09
Hi, 

Got Ubuntu 8.04 installed on a brand new Dell Inspiron 1420. The video card is an "Intel Graphics Media Accelerator X3100"
I have already replaced Totem-Gstreamer with Totem-Xine, libdvdcss2 is installed, etc...
When viewing multimedia from within Firefox, such as movies preview from the Apple website, I can open Totem-Xine fine and watch videos full screen. But when I try with a DVD, All I get with full screen is a blue screen. only audio is working.
I have also tried with vlc, as well as xine with xine-ui, and I am getting the same thing.
I also tried to change the default video output in gstreamer-properties to x Window System (no Xv): same problem.
Any help would be appreciated.
Thanks

Update: Removed totem-xine, installed gxine, changed video driver from "auto" to "xshm". No more  blue screen.

---

