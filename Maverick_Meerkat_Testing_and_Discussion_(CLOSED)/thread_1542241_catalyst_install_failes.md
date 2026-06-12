---
title: "catalyst install failes"
date: 2010-07-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by napsy on 2010-07-30
Hello.

I'm unable to install catalyst drivers due to installation failure. The installation log says:

> 
DKMS make.log for fglrx-8.723.1 for kernel 2.6.35-12-generic (x86_64)
pet jul 30 14:53:24 CEST 2010
AMD kernel module generator version 2.1
cat: /lib/modules/2.6.35-12-generic/build/include/linux/utsrelease.h: No such file or directory
Error:
kernel includes at /lib/modules/2.6.35-12-generic/build/include do not match current kernel.
they are versioned as ""
instead of "2.6.35-12-generic".
you might need to adjust your symlinks:
- /usr/include
- /usr/src/linux


I have:
linux-headers-2.6.35-12, version 2.6.35-12.17
linux-headers-generic, version 2.6.35-12.13
linux-image-2.6.35.12-generic, version 2.6.35-12.17
linux-image-generic, version 2.6.35-12.13

Any ideas how I could fix this error?

---

### Post by rajeev1204 on 2010-07-30
> **napsy said:**
> Hello.

I'm unable to install catalyst drivers due to installation failure. The installation log says:



I have:
linux-headers-2.6.35-12, version 2.6.35-12.17
linux-headers-generic, version 2.6.35-12.13
linux-image-2.6.35.12-generic, version 2.6.35-12.17
linux-image-generic, version 2.6.35-12.13

Any ideas how I could fix this error?


YOu have to install the 10.7 catlyst drivers for this kernel .Download it.

---

### Post by andrek on 2010-07-30
Add this repository [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) and upgrade.

---

### Post by napsy on 2010-07-30
Thanks it worked.

---

### Post by rajeev1204 on 2010-07-30
> **andrek said:**
> Add this repository [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates") and upgrade.


This repo is the 10.6 version , but AMD have made the new driver 10.7 install on ubuntu without any hacks, its a direct install and goes through with any xserver or kernel version.

---

### Post by andrek on 2010-07-30
> **rajeev1204 said:**
> This repo is the 10.6 version , but AMD have made the new driver 10.7 install on ubuntu without any hacks, its a direct install and goes through with any xserver or kernel version.

Umm is it?
> 
fglrx-installer - 2:8.753-0ubuntu0sarvatt        (changes file)        sarvatt       2010-07-28      Published      Maverick      Misc       All builds were built successfully.
Publishing details

    Published on 2010-07-28

Changelog

fglrx-installer (2:8.753-0ubuntu0sarvatt) maverick; urgency=low

  * **New upstream release (10.7)**. Changes:
(...)


---

### Post by fvdnabee on 2010-08-07
I too had the exact same problem trying to install ati catalyst 10.7 on ubuntu 10.04 with the maverick 2.6.35 kernel(2.6.35-020635-generic). 
I can confirm that Andrek's solution worked for me.

---

### Post by pulpo69 on 2010-08-08
i installed fglrx from this repo and the driver is working fine.

---

### Post by rajeev1204 on 2010-08-09
> **andrek said:**
> Umm is it?

You were correct, it wasnt updated when they released catalyst 10.7 so i wasnt sure when the ppa would have the new one.


Thanks for this update .

rajeev

---

### Post by pulpo69 on 2010-08-10
with the kernel-update last night the driver don't work.

---

### Post by pulpo69 on 2010-08-10
i've this ppa or repo installed: 
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
i choosed the propietary fglrx driver. all was fine till yesterday
with an kernel update nothing worked. boot gets till a violet
screen saying ubuntu and nothing more. choosing the failsafex
in grub i can only get a command line. anyone expperienced the same? and how to solve it?

---

