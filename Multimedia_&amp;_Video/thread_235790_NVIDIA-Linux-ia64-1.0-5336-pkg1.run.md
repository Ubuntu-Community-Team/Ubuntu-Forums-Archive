---
title: "NVIDIA-Linux-ia64-1.0-5336-pkg1.run"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by IgD on 2006-08-13
I installed Ubuntu 6.06.1!  Now I want to get my nVidia 6800 GT card working.  I'm running on an AMD 64 processor.  I went to the nVidia site and downloaded the drivers:  NVIDIA-Linux-ia64-1.0-5336-pkg1.run.

It says to "sh" that file.  I tried doing that and I got errors that it needed to be run as root, needed the binutils packaged installed and then that it needed libc/ld installed.  I gave up after this.

I'm really confused.  If I go through the Ubuntu package manager GUI it looks like you can install nVidia drivers from the CD.  I tried this but I don't see any kind of nVidia control panel or other notification the drivers are installed.

I also looked through some of the posts here and am more confused.  What do I need to do to get my video card working?

Thanks!

---

### Post by tseliot on 2006-08-13
Please read my guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

You can use Method 1.


BTW you downloaded a quite old version (current is 8762, yours 5336) and the installer is not for your architecture. You'll see that on my guide.

---

### Post by IgD on 2006-08-15
Method 1 worked for me.  However I ended up installing the Intel 386 flavor of Ubuntu.  I couldn't get Cedega to work correctly and got error messages with other packages using AMD 64.

---

