---
title: "Problem with sk_buff errors"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by jbhtexas on 2009-01-12
Hello!

I'm trying to compile the Basilisk II 1.0 JIT Macintosh emulator on Ubuntu 8.04. uname -r reports 2.6.24-23-generic.

I have the basic program working, but for networking in the emulator, I need to get a driver called sheep_net compiled.  When trying to do that I get the following errors:

[FONT="Courier New"]make -C /lib/modules/2.6.24-23-generic/build M=$PWD modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
sheep_net.c:22:26: error: linux/config.h: No such file or directory
sheep_net.c:29:31: error: linux/modversions.h: No such file or directory
sheep_net.c:283: error: ‘struct sk_buff’ has no member named ‘mac’
sheep_net.c:400: error: ‘struct sk_buff’ has no member named ‘nh’
sheep_net.c:400: error: ‘struct sk_buff’ has no member named ‘h’
sheep_net.c:487: warning: passing argument 1 
sheep_net.c:487: error: too few arguments to function ‘dev_get_by_name’[/FONT]

After searching the web, there are literally hundreds of pages that get these same errors with sk_buff and dev_get_by_name when trying to compile network-related programs. However, I haven't really found a good explanation of what the problem is.  Some of the posts suggest that something has changed in the kernel header files along the way, or there may be some out of date headers. Many times the solution is to get an update package or patch from the software vendor, or get some different headers. In this case, I haven't found any patches.

I don't have experience writing networking code, so I'm looking for a little direction on how to proceed with this problem.  Some of the web articles I searched have reported that this driver has been successfully compiled on some other Linux flavors (like Red Hat).

Do I need some updated or different header files to use when compiling this driver against?

Does the code need to be rewritten?

Is there an Ubuntu patch or update that I need?  Update Manager says that I'm up to date.

Do I need to try a different flavor of Linux that might work better?

I can post the source file if that would be of help.

Thanks for any help!

---

