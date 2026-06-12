---
title: "No Video with Cloned Display"
date: 2008-06-10
forum: Multimedia Software
---

### Post by Dr Zolygon on 2008-06-10
I'm using Ubuntu 8.04 on my laptop and have an external display set to clone. In all media players that I've tested (VLC, Totem, MPlayer), I get video in my laptop display but not the external display. Video works fine in flash-based players like on youtube.

  I've tried changing the plugin used in gstreamer-properties as mentioned in other posts to no avail.

 Any help is appreciated.

---

### Post by anindya_m on 2008-06-10
This means hardware accelerated video (xv) is not working on the clone. As a quick workaround use the x11 video output in mplayer, for example.

---

### Post by Pjotr123 on 2008-06-10
1. make sure you're running the right driver for your video card:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 2 )

2. use these tools:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 as well)

---

### Post by Dr Zolygon on 2008-06-10
> **anindya_m said:**
> This means hardware accelerated video (xv) is not working on the clone. As a quick workaround use the x11 video output in mplayer, for example.

Thanks. This works perfectly.

---

### Post by anindya_m on 2008-06-10
Good. However, please note that this is kind of a workaround. At some point you should check the driver installation as suggested in an earlier post.

---

### Post by markbuntu on 2008-06-10
If you are using the current restricted ATI driver from the repos this is a known problem that is fixed in the newest 8.5 driver that is unfortunately not yet available from the repos.

---

