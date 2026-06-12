---
title: "Compiling XviD Codec..."
date: 2009-12-26
forum: Multimedia Software
---

### Post by mobrien118 on 2009-12-26
Hi all,

I wanted to compile the newer version of XviD for my Karmic system (to enable multi-threaded encodiong, which is compiled by default into the newer versions of XviD)... So I did.

I:
1. ran the compile instructions from the XviD website on the newest stable branch, then
2. copied the .so file into /var/lib/ alongside the original Ubuntu one, then
3. rebooted, which updated the libxvid symbolic link to point to the new 1.2 version file (like magic!) and mencoder started using the new one!!!

So, after all that, I though all was going to be great!... But... When I tried to encode a video, it *looked* like it was working, but the video index would be messed up, and for a couple of encodes, when I would start playing the movie, it would only go about 2-5 seconds into the video, then start using 100% CPU and just hang there.

I removed the 1.2 codec (.so file) and re-set the symlink to the 1.1.2 library file, re-encoded the videos again and had no problem.

So, what am I doing wrong??? Am I missing some compiler flags I need? Does anyone know what command Ubuntu uses to build and compile XviD?

BTW, Yes, I have nasm installed.

Thanks in advance and sorry for the long post.

--mobrien118

---

