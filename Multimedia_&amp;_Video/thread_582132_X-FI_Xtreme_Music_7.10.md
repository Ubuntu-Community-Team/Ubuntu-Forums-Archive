---
title: "X-FI Xtreme Music 7.10"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by xsabrewulf on 2007-10-19
I went to the creative webpage and the ONLY linux driver they have is the 64-bit version.


is there a working one for the 32bit vesion?

---

### Post by ÜbuntuMensch on 2007-10-19
Nope. And the 64 bit is a beta that seems like more trouble than its worth. Lots of discussion on this at Creative's forums, but the overall picture is not encouraging.

---

### Post by billmilosz on 2007-10-20
Ubuntu 7.10 64 bit  uses a 3.x kernel and this Creative X-Fi 64-bit driver was written to work on a 2.6 gentoo kernel, so making your X-Fi work on Ubuntu 7.10/64  is pretty tricky....

it seems to me that the X-Fi drivers use a memory management module SLAB  and Ubuntu 7.10 uses a different memory management module SLAM  so you have to recompile the kernel to use SLAB instead of SLAM....  and then follow this HOWTO [http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)

But I've heard that even after you go through all that sound will work  but work POORLY with looping and skipping etc.  XMMS is supposed to be the only audio app to work at all....

This is not worth it -  it's better to just accept that there is NO X-Fi support in Ubuntu 7.10 at this point.

---

### Post by malaeum on 2007-10-21
> **billmilosz said:**
> Ubuntu 7.10 64 bit  uses a 3.x kernel and this Creative X-Fi 64-bit driver was written to work on a 2.6 gentoo kernel, so making your X-Fi work on Ubuntu 7.10/64  is pretty tricky....



7.10 does not use a 3.x kernel, there is no such thing at this point. I am running Ubuntu 7.10 64-bit and am using a 2.6 kernel. To see this for yourself simply run uname -a. 

```
mmschnei@benzene:~$ uname -a
Linux benzene 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

```

I am going to look into what you posted otherwise about SLAB vs. SLAM and I really would like to try and get this running.

---

