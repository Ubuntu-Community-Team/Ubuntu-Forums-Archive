---
title: "usr9000 compiling a driver..."
date: 2005-12-15
forum: Networking &amp; Wireless
---

### Post by jaleo on 2005-12-15
I'm a new user of Breezy and I want to compile the usr9000 driver on it. The driver installation is described at [http://www.usr.com/support/9000/9000-ug/index.html](http://www.usr.com/support/9000/9000-ug/index.html). What packages are neccesary (gcc, make. kernel headers...) to compile programs on obuntu?

The installation script: **inst_mod**

```
#! /bin/bash
echo off
KRNVRSN=$1

if [ "$KRNVRSN" == "" ];then
clear
echo  "*** You need to give the kernel version ***"
echo  "*** ex : inst_mod **linux-2.4.7-10 **       ***"
exit 1
fi

if [ ! -r "/usr/src/linux" ]
then
rm -f /usr/src/linux* >/rm_temp 2>&1
rm -f /rm_temp
ln -s /usr/src/$KRNVRSN /usr/src/linux
fi

cd ADI_LINUX
make clean
make install
echo
echo 

```

By the way, **/usr/src** is empty in my system, it's normal?

Many thanks.

---

### Post by amohanty on 2005-12-16
I think you will need build-essential kernel-package.
/usr/src is empty because the source is not installed by default. To install the source, search in synaptic for linux-tree
 or in a terminal:

```
sudo apt-get install build-essential kernel-package linux-kernel-headers linux-tree
```

Please keep in mind that this is a ton of stuff to download.

HTH

---

