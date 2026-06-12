---
title: "Video image freezes or quits unexpectedly after window resize (Totem and VLC)"
date: 2008-07-21
forum: Multimedia Software
---

### Post by Ryuho on 2008-07-21
I have 8.04 with XPS 1710 (GPU=7900gtx with driver installed).

For the most of the time I try to make my video window bigger (full screen, 200%, whatever) it works, but sometimes, the image of the video freezes when I try to resize (and it seems like it freezes only when i try to stretch it) with audio being unaffected.

I have noticed the window just closing with out saying anything also.. It feels like these two problems are some how related

Have anyone else seen this symptom? It randomly goes away, and I'm not sure if it really is random, or if it's something I'm doing with out thinking.

Thanks,
Ryuho


----
EDIT:

I thought I should add the vlc output when it closed unexpectedly...

ryuho:~$ vlc
VLC media player 0.8.6e Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  157
  Current serial number in output stream:  158

---

### Post by mediajunkie on 2008-07-21
Hi, 

You might want to read this post. 

[http://ubuntuforums.org/showthread.php?p=5432709#post5432709](http://ubuntuforums.org/showthread.php?p=5432709#post5432709)

worked for me.

---

