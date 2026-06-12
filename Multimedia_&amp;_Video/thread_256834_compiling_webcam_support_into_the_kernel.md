---
title: "compiling webcam support into the kernel"
date: 2006-09-13
forum: Multimedia &amp; Video
---

### Post by martijn hoekstra on 2006-09-13
As there were no official drivers for my WB-1400T webcam I found a driver that was sayd to work with the chipset in the webcam. The Install file says

> Module compile outside the kernel tree but need the source of your running
kernel installed and configured.
be sure your kernel include usb and v4l stuff
Kernel 2.4.x 
	configure your kernel
	make dep
	go to the spca5xx directories
	make clean (to be sure)
	make
	if all goes right as root :
	make install
Kernel 2.6.x
	make clean
	make
	if all goes right as root :
	make install

I got the following output
> 
$ make clean
rm -r -f drivers/usb/*.o drivers/usb/.spcadecoder.o.cmd \
        drivers/usb/.spca5xx.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i

$ sudo make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=xxxxxxx/webcam/spca5xx-20060501 CC=cc modules
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
make: *** [default] Error 2

What am I doing wrong?

I added the makefile for extra info. 
```
VERSION    = 00.60.00
CVSVERSION = "$Experimental work Michel Xhaard && Reza Jelveh 03/02/2004"
DEFINES    =

###
# The following flags enable experimental features.
# By default, these are enabled for development versions of the driver, and
# disabled for release versions.

# Optional: Enable driver debugging
DEFINES   += -DSPCA50X_ENABLE_DEBUG

# Optional: Enable direct register read/write for PAC207 development
#DEFINES   += -DSPCA5XX_ENABLE_REGISTERPLAY

###
# The following flags enable features that aren't yet implemented, and
# therefore are disabled by default.

# Optional: Enable compression
DEFINES   += -DSPCA50X_ENABLE_COMPRESSION

###
# Rest of Makefile follows here. You probably won't need to touch this.

# Setup defines
DEFINES   += -DCONFIG_USB_SPCA5XX_MODULE=1 -DMODULE -D__KERNEL__
DEFINES   += -DVID_HARDWARE_SPCA5XX=0xFF -DSPCA5XX_VERSION=\"$(VERSION)\"

ifneq ($(shell uname -r | cut -d. -f1,2), 2.4)

ifneq ($(KERNELRELEASE),)   # We were called by kbuild
CFLAGS += $(DEFINES) 
obj-m += spca5xx.o
spca5xx-objs := drivers/usb/spca5xx.o drivers/usb/spcadecoder.o 

else   # We were called from command line

KERNEL_VERSION = `uname -r`
KERNELDIR := /lib/modules/$(KERNEL_VERSION)/build
PWD  := $(shell pwd)
MODULE_INSTALLDIR = /lib/modules/$(KERNEL_VERSION)/kernel/drivers/usb/media/

# Targets, don't change!
default:
	@echo '   Building SPCA5XX driver for 2.5/2.6 kernel.'
	@echo '   Remember: you must have read/write access to your kernel source tree.'
	$(MAKE) -C $(KERNELDIR) SUBDIRS=$(PWD) CC=$(CC) modules

install:
	mkdir -p $(MODULE_INSTALLDIR)
	rm -f $(MODULE_INSTALLDIR)spca50x.ko
	rm -f $(MODULE_INSTALLDIR)et61x.ko
	install -c -m 0644 spca5xx.ko $(MODULE_INSTALLDIR)
	/sbin/depmod -ae

uninstall:
	rm -f $(MODULE_INSTALLDIR)/spca5xx.ko
	/sbin/depmod -aq

endif

else   # kernel version test

# For Linux 2.4 users (omitted)
                          

endif  # End kernel version test


############################################################################## 
# OTHER TARGETS 
##############################################################################
clean:
	rm -r -f drivers/usb/*.o drivers/usb/.spcadecoder.o.cmd \
	drivers/usb/.spca5xx.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i
	
############################################################################## 

```

---

### Post by Ice1532 on 2006-09-19
i am actually getting the same error and cant figure it out... its really pissing me off...

---

### Post by martijn hoekstra on 2006-09-19
I found out that the driver is actualy readily available in the Ubuntu Universe. search for DSPCA5XX in Synaptic.

I still haven't got my cam working tho.

---

