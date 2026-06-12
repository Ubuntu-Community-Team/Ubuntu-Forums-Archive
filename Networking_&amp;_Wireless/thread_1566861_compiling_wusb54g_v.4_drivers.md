---
title: "compiling wusb54g v.4 drivers"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by ixifx on 2010-09-02
Hi all.  I'm trying to compile and install drivers for my usb wifi adapter using instructions at [http://www.aircrack-ng.org/doku.php?id=rt2570](http://www.aircrack-ng.org/doku.php?id=rt2570)

if I can get these drivers working I may add network security audits to my ever-growing list of "things I can do with a computer"

I get to the part where it says 

make && make install

but I get this error

make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
rt2570.ko failed to build!
make: *** [module] Error 1

I checked in synaptic and I have the linux-headers-2.6.32-24-generic package installed and there are lots of files and folders in the directory the error message references.  I'm not sure what exactly is going wrong here...

any ideas on how I can get a more detailed error message?

---

