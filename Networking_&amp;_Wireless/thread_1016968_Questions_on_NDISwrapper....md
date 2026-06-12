---
title: "Questions on NDISwrapper..."
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by icanfly0307 on 2008-12-20
Hi, I compiled my own cutsom kernel and it's running great (boottime reduced from 1 min 20 secs to 20 sec.):) However, I need to get NDISwrapper working and I was wondering if reinstalling from the repos would be enough? Or do I have to compile NDISwrapper from source? Any help would be appreciated. Thanks.

---

### Post by Ayuthia on 2008-12-20
You are going to need to compile ndiswrapper from source.  This is because it is a kernel module.  The ndiswrapper that comes packaged in the repos does not supply the ndiswrapper.ko file.  The way it works in Ubuntu is that the ndiswrapper application comes in the repos, but the ndiswrapper.ko module comes with the Ubuntu kernels.  So if you install ndiswrapper from the repos, you get the application, but you will not be able to do the modprobe for ndiswrapper because it is not there.

---

### Post by icanfly0307 on 2008-12-20
Thanks for the info. I have another issue. Whenever I try to compile ndiswrapper 1.53, I keep failing with a "make all error 2" error. It throws a long list of "too few arguments" sort of error. Do you know how to get around this? Thanks.

---

### Post by Ayuthia on 2008-12-20
Here is a link that has a link to the patch:
[http://www.linuxquestions.org/questions/slackware-14/ndiswrapper-and-2.6.27-675886/](http://www.linuxquestions.org/questions/slackware-14/ndiswrapper-and-2.6.27-675886/)

---

### Post by icanfly0307 on 2008-12-20
Thanks. I'll try it out.

---

### Post by icanfly0307 on 2008-12-20
Ah, man. The patch didn't work. When I executed "patch -p0 xxxx.patch", it just froze there and I had to hit "Ctrl + C" to get it out. Any other thoughts? Oh and by the way, if I copy the *ndiswrapper.ko* file from */lib/modules/2.6.24-21-generic/ubuntu/misc/ndiswrapper* to my new kernel, will it work? Thanks.

---

### Post by Ayuthia on 2008-12-20
> **icanfly0307 said:**
> Ah, man. The patch didn't work. When I executed "patch -p0 xxxx.patch", it just froze there and I had to hit "Ctrl + C" to get it out. Any other thoughts? Oh and by the way, if I copy the *ndiswrapper.ko* file from */lib/modules/2.6.24-21-generic/ubuntu/misc/ndiswrapper* to my new kernel, will it work? Thanks.

I think that the patch is applied by doing patch -p1 < xxxx.patch

As for copying the .ko file over, it might not work because it was compiled with a different kernel source.

EDIT:
The patch has to be applied in the driver directory and not the ndiswrapper-1.53 directory.

---

### Post by icanfly0307 on 2008-12-21
Thanks for your help so far, Ayuthia. I've just noticed that HAL and udev are broken because I forgot to enable inotify in my kernel. So I'm going to recompile it and follow [this]("http://d-kriptik.com/blog/2005/09/14/custom-kernel-build-on-debian/") guide to compile ndiswrapper as a module along with the other modules. Thanks!

---

### Post by icanfly0307 on 2008-12-22
Thanks again. I recompiled my kernel but the ndiswrapper module didn't get compiled in. However, I tried out your patch command method and WALA!!! it worked! Now the only thing is that I can't get my terminal to work. It keeps giving out a "no child process created..." error. Oh well. That's for another post. Thanks again for your help, Ayuthia. I really appreciate it. :)

---

