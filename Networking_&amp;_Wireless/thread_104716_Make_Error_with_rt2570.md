---
title: "Make Error with rt2570"
date: 2005-12-16
forum: Networking &amp; Wireless
---

### Post by coderasm on 2005-12-16
I'm trying to compile the rt2570 driver source.  I receive this error:

root@ubuntu:/home/rt2570-cvs-2005121614/Module# make
make: *** /lib/modules/2.6.12-10-686/build: No such file or directory.  Stop.
rt2570.ko failed to build!
make: *** [module] Error 1

I've been told I'm missing my kernel source.  How do I get the kernel source and install it?  Can I use apt-get?  Thanks for any help.

---

### Post by Sutekh on 2005-12-16
I think to do this (compile drivers) you will need the kernel headers, not the source, for the kernel that you are using.

To download your kernel headers you will need to determine your kernel version; at a command line type
```

uname -r

```
You will get something like 2.6.12-10-386. You would need to then download the headers using
```

sudo apt-get install linux-headers-2.6.12-10-386

```
Of course if your kernel version is different, just adjust that code.
If it turns out you need the source use
```

sudo apt-get install linux-source-2.6.12

```
You don't need the extra -10-386 (or whatever your version is)

You could also do this in Synaptic just search for "linux-headers" and "linux-source" and select to install the correct version

---

### Post by Lambert on 2005-12-16
make sure make and build-essentials is also installed.

---

### Post by diantel on 2005-12-17
You have to edit the Makefile(in the Module directory) . 

Change this line: #KERNDIR=/usr/src/linux-2.6

to KERNDIR=/usr/src/`uname -r`

(you have to install your kernel headers before).

Good luck.

---

