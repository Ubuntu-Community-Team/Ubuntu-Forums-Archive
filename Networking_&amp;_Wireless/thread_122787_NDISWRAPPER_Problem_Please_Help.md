---
title: "NDISWRAPPER Problem Please Help"
date: 2006-01-28
forum: Networking &amp; Wireless
---

### Post by TecSoft on 2006-01-28
Hello everyone. Here is my problem. I have installed ndiswrapper 1.9rc1. I did ndiswrapper -i and installed my driver. I did ndiswrapper -l to see if the hard ware was present. It was. But the lights were not lighting up on my Netgear USB device thing. I did iwconfig and there was no wlan0. I had slackware before and WIFI worked on it. I went back to windows (Dual Booting) and it works. Can anyone help me?

---

### Post by moephan on 2006-01-28
I assume you used modprobe on the ndis wrapper?

Here's another thread that seems related to your question:
[http://www.ubuntuforums.org/showthread.php?t=67686](http://www.ubuntuforums.org/showthread.php?t=67686)

---

### Post by TecSoft on 2006-01-28
Yes but it says permission denied even as root

---

### Post by moephan on 2006-01-28
I never tried this by running as root in Ubuntu. In fact, I never run as root in Ubuntu. To load ndiswrapper, I just:

promt$sudo modprobe ndiswrapper

then put in my user password. However, as you can see from the thread above, this did not work as expected for everyone. In anycase, ndiswrapper will never work if the module isn't loaded. Can you tell us exactly what you typed, and what the output was?

Cheers, Rick

---

### Post by mpvano on 2006-01-28
That's because you built ndiswrapper with the wrong compiler.

The Ubuntu (and everyone else's) kernel is NOT built with the compiler installed by build-tools for application development. Because of the complexity of kernel development, C compiler switches are usually done more conservatively and kernel C compilers are usually a few revisions behind.

In order to build ndiswrapper (or anything else involving a kernel module) and create a kernel module that is compatible with a standard Ubuntu kernel, you need to find out exactly which compiler was used to build the kernel, download it and make sure you use it for the compilation.

The last module I tried to build (needlessly, as it turned out) was a few months ago and at that time, I believe that the correct compiler was gcc 3.4. Even if you download it, you still need to know how to switch over to using it for your build.

If you use the wrong compiler, the module will have incompatible function calls and cannot be loaded.

This is why it's usually best not to try to build packages that are already part of Ubuntu. 

The usual way to use ndiswrapper is just to install the ndiswrapper-utilities package from the regular ubuntu repository and to use the ndiswrapper kernel module pre-installed in all the kernels.

Are you sure you really need functionality from the later ndiswrapper? The one already built into Ubuntu generally works well with most cards. Later ndiswrapper versions usually don't improve the wireless functionality at all, and furthermore you have to keep re-building them everytime there's a kernel update. The built in one is automatically updated.

In any event, I suggest you try installing gcc3.4. Once that's done, do the following:

Make sure that your existing gcc compiler is present at /usr/bin/gcc-4.0. You should see something like the following if you do an "ls -l /usr/bin/gcc"

lrwxrwxrwx  1 root root 7 2005-12-18 22:01 /usr/bin/gcc -> gcc-4.0

If you don't see a link, rename what you DO see as gcc-4.0

If you see a link, write down what you see.

Then create the following link which will destroy whatever USED to be /usr/bin/gcc.

sudo ln -fs /usr/bin/gcc-3.4 /usr/bin/gcc

Build and install ndiswrapper

Go back and restore the way /usr/bin/gcc used to be.

There are definitely other ways to do this, but unfortunately, I don't believe that "update-alternatives" usually maintains development compilers.

sorry this is so complicated, but it's not usually something beginners should get into.

Mario

---

### Post by TecSoft on 2006-01-28
Okay everything now works but when I do iwconfig I see no wlan0.
The lights light up on my device but nothing.

---

### Post by mpvano on 2006-01-29
check to see if the driver actually loaded and stayed loaded.

lsmod | grep ndis

should display the ndiswrapper driver name if it's currently loaded.

It's possible you still have a build problem if it won't stay loaded.

---

