---
title: "Kernel build with audio changes"
date: 2017-06-27
forum: Multimedia Software
---

### Post by rw1968 on 2017-06-27
I'm trying to get a Focusrite Saffire 6 USB working with Ubuntu Studio 16.04LTS
There is a patch available to add support which I'd like to try out.
I've been trying to get kernel source with the help of this wiki page:
[https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)
but I can't install either the source or the build-dep packages.

This is what I get:

```
rich@Ginetta:~$ apt-get source linux-image-$(uname -r)
Reading package lists... Done
Picking 'linux-hwe' as source package instead of 'linux-image-4.8.0-56-lowlatency'
E: Unable to find a source package for linux-hwe
rich@Ginetta:~$ 
rich@Ginetta:~$ 
rich@Ginetta:~$ sudo apt-get build-dep linux-image-$(uname -r)
Reading package lists... Done
Picking 'linux-hwe' as source package instead of 'linux-image-4.8.0-56-lowlatency'
E: Unable to find a source package for linux-image-4.8.0-56-lowlatency
rich@Ginetta:~$ 
```


What am I doing wrong?

---

