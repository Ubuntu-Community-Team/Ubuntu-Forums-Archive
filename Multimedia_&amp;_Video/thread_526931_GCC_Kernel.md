---
title: "GCC Kernel??"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by gmalac on 2007-08-16
Hi,
I am running Easycam in order to make Ubuntu 7.04 recognise my Logitech Quickcam.
It stops with the following message:
gcc-3.4 version: version gcc 3.4.6 (ubuntu 3.4.6-5ubuntu1)
gcc version: version gcc 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Make version: GNU Make 3.81
Linker version: GNU 1d version 2.17.50 20070103 Ubuntu
Kernel compiler: gcc version 4.1.2 (Ubuntu 4.1.2.0ubuntu4)
Kernel compiler and gcc-3.4 seem to be different versions. Should be same version. Need replace Kgcc with proper compiler (sorry I am translating from french).

The command export CC=kgcc gives nothing

uname -r gives 2.6.20-16-generic

I can see that I have installed:
gcc                      version 4:4.1.2-1ubuntu1
gcc--3-3.base   version 1:3.3.6-15ubuntu1
gcc-3.4               version 3.4.6-5ubuntu1
gcc-3.4-base    version 3.4.6-5ubuntu1
gcc-4.1              version 4.1.2-0ubuntu4
gcc-4.1-base    version 4.1.2-0ubuntu4

Somebody could be so kind and tell me what I should do please?

Thank you very much

---

### Post by gmalac on 2007-08-18
Bump! Anyone?
Meantime I removed version GCC-3.4 but nothing improved
Thanks

---

### Post by tseliot on 2007-08-18
reinstall gcc-3.4:
```
sudo apt-get install gcc-3.4
```

then type:
```
 ls -l /usr/bin/gcc
```

you will see something like this:
```
~$ ls -l /usr/bin/gcc*
lrwxrwxrwx 1 root root      7 2007-02-24 11:41 [COLOR="Red"]/usr/bin/gcc -> gcc-4.1[/COLOR]
-rwxr-xr-x 1 root root 183904 2007-03-03 03:52 /usr/bin/gcc-4.1
lrwxrwxrwx 1 root root     10 2007-02-24 11:41 /usr/bin/gccbug -> gccbug-4.1
-rwxr-xr-x 1 root root  16266 2007-03-03 03:47 /usr/bin/gccbug-4.1
-rwxr-xr-x 1 root root   2018 2006-12-20 15:41 /usr/bin/gccmakedep
```

the line I put in red is the one you will have to pay attention to. In my case it says that gcc is a link to gcc-4.1

Make sure gcc-3.4 is the list of files when you type ls -l /usr/bin/gcc*

then type:
```
sudo ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc
```

Compile what you need and then restore the previous link to gcc-4.1 or to whatever appeared in the line I put in red by typing:
```
sudo ln -sf /usr/bin/gcc-4.1 /usr/bin/gcc
```

P.S. of course you could have exported CC as well.

---

### Post by gmalac on 2007-08-18
Thanks for the reply, I did what you instructed but compiling continue to give me an error now a bit different:

gcc version: version gcc 3.4.6 (ubuntu 3.4.6-5ubuntu1)
gcc version: version gcc 3.4.6 (Ubuntu 3.4.6-5ubuntu1)
Make version: GNU Make 3.81
Linker version: GNU ld version 2.17.50 20070103 Ubuntu
Kernel compiler: gcc version 4.1.2 (Ubuntu 4.1.2.0ubuntu4)
Kernel compiler and gcc seem to be different versions. Should be same version. Need replace Kgcc with proper compiler (sorry I am translating from french).

Its clearer now with everything 3.4 but the kernel compiler 4.1 But where do I go from here? What should I do?

Thanks for your appreciated help

---

### Post by tseliot on 2007-08-18
> **gmalac said:**
> Thanks for the reply, I did what you instructed but compiling continue to give me an error now a bit different:

gcc version: version gcc 3.4.6 (ubuntu 3.4.6-5ubuntu1)
gcc version: version gcc 3.4.6 (Ubuntu 3.4.6-5ubuntu1)
Make version: GNU Make 3.81
Linker version: GNU ld version 2.17.50 20070103 Ubuntu
Kernel compiler: gcc version 4.1.2 (Ubuntu 4.1.2.0ubuntu4)
Kernel compiler and gcc seem to be different versions. Should be same version. Need replace Kgcc with proper compiler (sorry I am translating from french).

Its clearer now with everything 3.4 but the kernel compiler 4.1 But where do I go from here? What should I do?

Thanks for your appreciated help

Ubuntu's kernels are compiled with gcc 4.1.x ...

---

### Post by gmalac on 2007-08-19
OK, but then?

This Logitech Quickcam Messenger is supposed to just work in Feisty, well it doesn't, not in my and probably others cases.

It's quite frustrating because I've been trying for some time now to convince the rest of the family to fully abandon Windows and all switch to Linux Ubuntu (dual boot for now), but they (rightly so) pretend to continue having these basics (for chat, etc.) that just work in Windows.

Anyway, thanks for the help and I'll keep trying...and my faith!

---

