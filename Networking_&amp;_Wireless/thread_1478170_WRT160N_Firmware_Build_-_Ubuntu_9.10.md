---
title: "WRT160N Firmware Build - Ubuntu 9.10"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by 1111000110 on 2010-05-09
Here's a quick write-up of the steps I took to build the GPL firmware for the WRT160N, the errors I received, and the steps to fix.  This was on a fresh install (VM) of Ubuntu 9.10.
 
1) Download source tarball from LinkSys GPL Code Center
 
2) Unpack (tar -xvf)
 
3) Copy the Toolchain to the /opt/ directory (per the Readme)
# sudo -s
# mkdir /opt/brcm
# cp -r ~/wrt160n.../tools/brcm/* /opt/brcm/
# exit <Note: I had to exit sudo to avoid some permission conflicts later on>
 
4) Build:
# cd ~/wrt160n.../release/src/# make

Build Error #1: "/usr/bin/ld: cannot find -lncurses"
# sudo apt-get install libncurses5-dev
 
Build Error #2: "/bin/sh: mipsel-uclibc-gcc: not found"
# PATH=/opt/brcm/hndtools-mipsel-uclibc-0.9.19/bin/:$PATH
 
Build Error #3: "make[2]: mipsel-linux-gcc: Command not found"
# PATH=/opt/brcm/hndtools-mipsel-linux-3.2.3/bin/:$PATH
 
Build Error #4: "g++: Command not found"
# sudo apt-get install g++
 
Build Error #5: mksquashfs-lzma: not found
# apt-get install lzma-dev lzma-source

---

### Post by K.Mandla on 2010-05-13
Moved to Networking and Wireless.

---

