---
title: "An unsuccessful FGLRX attempt in Feisty"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by je1117 on 2007-05-17
I run a Radeon 9200 (rv280), and I decided that after failed attempts at getting FGLRX to work in the past, I would try again.

I read somewhere online that there wasn't a way to get even the old 8.28 drivers to work on Feisty, but I tried anyway.

I had to run the install like this: X_VERSION=x710_64a bash ./ati*.run to even get it to work because of the new xorg I guess.

So I installed the driver and the kernel and it didn't work. If anyone knows how to get FGLRX running on an older card in Feisty, I look forward to a response.

But that isn't really my question, it is, when I removed the fglrx driver and kernel (completely?) and now when I type glxinfo, glxgears it outputs:

glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

A search for the file reveals nothing. Help?

---

