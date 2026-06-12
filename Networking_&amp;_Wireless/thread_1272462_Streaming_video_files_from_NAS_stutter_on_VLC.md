---
title: "Streaming video files from NAS stutter on VLC"
date: 2009-09-22
forum: Networking &amp; Wireless
---

### Post by tushar_t on 2009-09-22
I have a network hard drive which has some video files stored on it and I view those files streaming on VLC from my desktop. The desktop has Windows 7 and Ubuntu 9.04 dual-boot setup. 

If I view the videos on VLC from Windows, there are no issues whatsoever. However, if I view the same files on VLC in Ubuntu, it plays the file smoothly for about 40-60 seconds, then stutters (pauses video, but sound goes on) for another 5-10 seconds and then continues smoothly again. This happens repeatedly.

Are there any settings in Ubuntu or within VLC where I can increase the cache size or something? Or is it some other issue altogether?

Thanks.

---

### Post by tushar_t on 2009-09-23
bump. anyone?

---

### Post by lisanels47 on 2009-12-07
I had the same problem.  
If you open tools/codec infor and choose the statistics tab you might see that when the sound chops, you get lost buffers.

I fixed it by going into tool/preferences
Checked ALL At the bottom

Input/Codec
  Access Modules
    File
      Set Caching Value to 2400...

Now it works great...
Lisa

---

