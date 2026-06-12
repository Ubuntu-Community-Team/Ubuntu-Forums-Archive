---
title: "Usb-dvb Pinnacle PCTV 200e and kernel 3.13.0-24"
date: 2014-06-16
forum: Multimedia Software
---

### Post by danjde on 2014-06-16
Hi friends, 

I've a Pinnacle PCTV 200e on Ubuntu LTS 14.04, kernel Linux  3.13.0-24-generic 
#47-Ubuntu SMP Fri May 2 23:31:42 UTC 2014 i686 i686 i686 GNU/Linux: 

```

lsusb: 
#Bus 001 Device 004: ID 2304:020e Pinnacle Systems, Inc. PCTV 200e 

dmesg: 
[ 5287.516227] usb 1-8: new high-speed USB device number 4 using ehci-pci 
[ 5287.649014] usb 1-8: New USB device found, idVendor=2304, idProduct=020e 
[ 5287.649026] usb 1-8: New USB device strings: Mfr=1, Product=2,  SerialNumber=3 
[ 5287.649034] usb 1-8: Product: DVB-T 
[ 5287.649041] usb 1-8: Manufacturer: Pinnacle Systems, Inc. 
[ 5287.649048] usb 1-8: SerialNumber: 0C22175D0319C8EA 
```

I've seen the page: 
[http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_200e#Development_ToDo_List](http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_200e#Development_ToDo_List)   

I've installed headers and source kernel for kernel 3.13.0-24 
and followed this post: [http://ubuntuforums.org/showthread.php?t=1301793](http://ubuntuforums.org/showthread.php?t=1301793)
but compiling obtain this errors:



```

sudo dkms build -m pctv200e -v 20080520

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.13.0-24-generic -C /lib/modules/3.13.0-24-generic/build M=/var/lib/dkms/pctv200e/20080520/build....(bad exit status: 2)
ERROR (dkms apport): binary package for pctv200e: 20080520 not found
Error! Bad return status for module build on kernel: 3.13.0-24-generic (i686)
Consult /var/lib/dkms/pctv200e/20080520/build/make.log for more information.

#cat  /var/lib/dkms/pctv200e/20080520/build/make.log

DKMS make.log for pctv200e-20080520 for kernel 3.13.0-24-generic (i686)
lun 16 giu 2014, 16.18.36, CEST
make: ingresso nella directory "/usr/src/linux-headers-3.13.0-24-generic"
   LD      /var/lib/dkms/pctv200e/20080520/build/built-in.o
   CC [M]  /var/lib/dkms/pctv200e/20080520/build/pctv200e.o
gcc: fatal error: no input files
compilation terminated.
make[1]: *** [/var/lib/dkms/pctv200e/20080520/build/pctv200e.o] Errore 4
make: *** [_module_/var/lib/dkms/pctv200e/20080520/build] Errore 2
make: uscita dalla directory "/usr/src/linux-headers-3.13.0-24-generic"
/var/lib/dkms/pctv200e/20080520/build/make.log (END)

```

Do you know if is it possible to compile the 200e module for a 3.x kernel?

many many thanks 

Davide 
Italy

---

### Post by arulbero on 2015-01-04
My Pinnacle PCTV 200e works on Ubuntu 14.10, kernel Linux  3.16

See my post:  [http://forum.ubuntu-it.org/viewtopic.php?f=9&t=581659#p4701888](http://forum.ubuntu-it.org/viewtopic.php?f=9&t=581659#p4701888)

---

