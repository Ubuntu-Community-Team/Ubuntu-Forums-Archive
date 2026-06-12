---
title: "Problems with nvidia driver in kernel 2.6.38 and Ubuntu 10.04"
date: 2011-02-20
forum: Multimedia Software
---

### Post by Daniao on 2011-02-20
Dear all,

I have Ubuntu 10.04 and after installing kernel 2.6.38 my nvidia driver stopped working. I have the kernel sources installed.

This is what happens if I do:

~$ sudo apt-get install nvidia-current

Building initial module for 2.6.38-1-generic

Error! Bad return status for module build on kernel: 2.6.38-1-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-173/173.14.22/build/ for more information.
dpkg: error processing nvidia-173 (--configure):
 subprocess installed post-installation script returned error exit status 10
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 nvidia-173
E: Sub-process /usr/bin/dpkg returned an error code (1)

Does anyone know how to install the nvidia driver in kernel 2.6.38? Do I have to compile it from the source ?

Best Regards

Daniao

PS: The content of make.log is:

...

*** Unable to determine the target kernel version. ***

make: *** [select_makefile] Error 1

---

### Post by BicyclerBoy on 2011-02-20
Where did you get your kernel from ? ubuntu kernel ppa ?

The normal 10.04 kernel is 2.6.32-29.
You need kernel headers to compile nvidia driver not source.
I see you are using dkms to build & install from GUI..

The 10.04 nvidia current should be 195.36.24    not 173..

Do you have a dependency blockage or a locked version of driver ? 

It is very possible that 173 will not compile against 2.6.38 or that you do not have the headers package..

You can find nvidia 270 pre-compiled ppa for 10.04 in couple of ppa..
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)  (very careful with other packages)

10.10 only
[https://launchpad.net/~ferramroberto/+archive/nvidia](https://launchpad.net/~ferramroberto/+archive/nvidia)

---

### Post by barnex on 2011-07-28
I have a related problem: after upgrading my ubuntu 11.04 to kernel 2.6.38-10, the nvidia-current driver stopped working. 
I upgraded my system with the normal software updates, no manual installing anything whatsoever. I had to remove the driver (with jockey, over ssh) to get my display back.
This is extremely annoying as I need the nvidia driver to do my CUDA development...

Hopefully someone has a workaround!

Cheers,
Arne.

---

