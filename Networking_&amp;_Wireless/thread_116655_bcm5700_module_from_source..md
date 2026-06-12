---
title: "bcm5700 module from source."
date: 2006-01-13
forum: Networking &amp; Wireless
---

### Post by jl-ubuntu on 2006-01-13
Hi all,

I have installed Ubuntu Hoary with kernel 2.6.10.

#uname -a
Linux ubuntu 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux

I want to add the broadcom 5700 module to my kernel without recompile the entire kernel.

I have downloaded and installed the next packages:

bcm5700-source
linux-source-2.6.10
linux-tree-2.6.10

Now I have a tar compressed file in /usr/src called bcm5700.tar.gz.
I do:

tar zxvf bcm5700.tar.gz and I have ths directory:

   /usr/src/modules/bcm5700/src

I do cd to that directory and execute 

   #make

and then displays the error:

    Makefile:36: *** Linux kernel source tree not found.  Stop.

I think I have installed the kernel source tree but 'make' can't find it.

Anybody knows what I have to do to compile the module????

Many thanks.

---

