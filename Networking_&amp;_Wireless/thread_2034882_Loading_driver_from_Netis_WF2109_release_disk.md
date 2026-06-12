---
title: "Loading driver from Netis WF2109 release disk"
date: 2012-07-29
forum: Networking &amp; Wireless
---

### Post by csmilovitz on 2012-07-29
I'm driving myself nuts trying to install a netis WF-2109 USB-based modem.  The box claims linux support.  But they gave no instructions.   I copied the contents of the modem's installation disk to a memory stick so I could compile it

In the disk that came with the modem comes with various Windows files (*.ini, *.inf, *.exe) and a directory  'Driver'.  Inside the Driver directory is an insane hierarchy of compressed and uncompressed files.  The gritty details (which you can skip should you want and proceed immediately to the next paragraph):  Inside Driver/WF-2109  (where WF-2109 is my product number), I found linux/linux_v2.6.006.20100625.zip.  Unzipped this in Archive Manager and it created a folder rtl8712_8188_8191_8192SU_usb_linux_v2.6.006.20100625.  Below this was a directory 'driver' and under that the file rtl8712_81888191_8192SU_usb_linux_v2.6.0006.20100625.tar.gz.  Used Archive Manager again to get directory rtl8712_81888191_8192SU_usb_linux_v2.6.0006.20100625.  This had a Makefile and other files and directories. 

In the final directory listed above, I ran make.  That resulted in the creation of files 8712u.ko, 8712u.o, 8712u.mod.c, and 8712u.mod.o.

What do I do with these files and how do I get them installed?   As it is dmesg | grep 8192 returns nothing.  iwconfig does not show wlan0 or any other wlan.

BTW: I'm running ubuntu 10.04 because that's what I had a release disk for.

Thanks

---

### Post by chili555 on 2012-07-29
> In the final directory listed above, I ran make. That resulted in the creation of files 8712u.ko, 8712u.o, 8712u.mod.c, and 8712u.mod.o.Now, in the same directory,please run:```
sudo make install
sudo modprobe 8712u
```Is a wireless interface created, ideally wlan0?```
iwconfig
```Now can you click the Network Manager icon, see your network and connect?

---

### Post by csmilovitz on 2012-07-30
Thanks, but this hasn't worked. The make install seems to be dying now.  I seem to have been given a misformed Makefile and have been struggling to get it to work.  I'm a real newbie at makefiles.  Currently it seems to be failing on a statement 

include $(src)/config

The error message says "No rule to make target /config"  Previously I assigned "src=.[There's a dot there, as in pwd and in another trial I left src undefined].  I'm running make from the commandline in a directory deep in my directory tree that has a config file that assigns all the variables CONFIG_.... to y or n.  So perhaps for some reason the src shell variable is not working

The whole messy makefile is included here.  (Since it doesn't have a file extension I couldn't include it as an attachment)

--------------------- Makefile -----------------------------

EXTRA_CFLAGS += -O1 -Wno-unused-variable -Wno-unused-value -Wno-unused-label -Wno-unused-parameter -Wno-uninitialized
EXTRA_CFLAGS += -I$(src)/include  -Wno-unused -Wno-unused-function

#add assignment to src since it seems uninitialized
src = $(PWD)
#CONFIG_BUILT_in = n_
CONFIG_BUILT_IN = y
#src=/media/882B-9F61/netisDriver/Driver/WF-2109/linux/rtl8712_8818_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100615

export TOPDIR := $(PWD)

ifeq ($(CONFIG_BUILT_IN), y)
include $(src)/config
else
include $(TOPDIR)/config
endif

ifeq ($(CONFIG_RTL8711), y)
RTL871X = rtl8711
MODULE_NAME = 8711
endif

ifeq ($(CONFIG_RTL8712), y)

RTL871X = rtl8712

ifeq ($(CONFIG_SDIO_HCI), y)
MODULE_NAME = 8712s
endif
ifeq ($(CONFIG_USB_HCI), y)
MODULE_NAME = 8712u
endif

endif

ifeq ($(CONFIG_SDIO_HCI), y)

 
_OS_INTFS_FILES := os_intf/osdep_service.o \
                    os_intf/linux/os_intfs.o \
                    os_intf/osdep_sdio_intf.o \
                    os_intf/linux/sdio_intf.o \

_HAL_INTFS_FILES := hal/$(RTL871X)/hal_init.o \
            hal/$(RTL871X)/sdio_halinit.o \
            hal/$(RTL871X)/sdio_ops.o \
            hal/$(RTL871X)/sdio_ops_linux.o        

endif


ifeq ($(CONFIG_USB_HCI), y)
 
ifeq ($(CONFIG_BUILT_IN), y)
$(shell cp $(src)/autoconf_$(RTL871X)_usb_linux.h $(src)/include/autoconf.h)
else
$(shell cp $(PWD)/autoconf_$(RTL871X)_usb_linux.h $(PWD)/include/autoconf.h)
endif
 
_OS_INTFS_FILES := os_intf/osdep_service.o \
                   os_intf/linux/os_intfs.o \
                   os_intf/linux/usb_intf.o \


_HAL_INTFS_FILES := hal/$(RTL871X)/hal_init.o \
                    hal/$(RTL871X)/usb_ops.o \
                    hal/$(RTL871X)/usb_ops_linux.o \
                    hal/$(RTL871X)/usb_halinit.o \
        
endif


PWD := $(shell pwd)


ifeq ($(CONFIG_PLATFORM_I386_PC), y)
EXTRA_CFLAGS += -DCONFIG_LITTLE_ENDIAN
SUBARCH := $(shell uname -m | sed -e s/i.86/i386/)
ARCH ?= $(SUBARCH)
CROSS_COMPILE ?=
KVER  := $(shell uname -r)
KSRC := /lib/modules/$(KVER)/build
MODDESTDIR := /lib/modules/$(KVER)/kernel/drivers/net/wireless/
INSTALL_PREFIX :=
endif

ifeq ($(CONFIG_PLATFORM_ARM_S3C), y)
EXTRA_CFLAGS += -DCONFIG_LITTLE_ENDIAN
ARCH := arm
CROSS_COMPILE := arm-linux-
KVER  := 2.6.24.7_$(ARCH)
KSRC := /usr/src/kernels/linux-$(KVER)
endif

ifeq ($(CONFIG_PLATFORM_RTD2880B), y)
EXTRA_CFLAGS += -DCONFIG_BIG_ENDIAN -DCONFIG_PLATFORM_RTD2880B
ARCH:=
CROSS_COMPILE:=
KVER:=
KSRC:=
endif

ifeq ($(CONFIG_PLATFORM_MT53XX), y)
EXTRA_CFLAGS += -DCONFIG_LITTLE_ENDIAN -DCONFIG_PLATFORM_MT53XX
ARCH:= arm
CROSS_COMPILE:= arm11_mtk_le-
KVER:= 2.6.27
KSRC:= /proj/mtk00802/BD_Compare/BDP/Dev/BDP_V301/BDP_Linux/linux-2.6.27
endif

ifeq ($(CONFIG_PLATFORM_MIPS_RMI), y)
EXTRA_CFLAGS += -DCONFIG_LITTLE_ENDIAN
ARCH:=mips
CROSS_COMPILE:=mipsisa32r2-uclibc-
KVER:= 
KSRC:= /root/work/kernel_realtek
endif

ifeq ($(CONFIG_PLATFORM_RTK_DMP), y)
EXTRA_CFLAGS += -DCONFIG_LITTLE_ENDIAN -DRTK_DMP_PLATFORM
ARCH:=mips
CROSS_COMPILE:=mipsel-linux-
KVER:= 
KSRC ?= /root/Desktop/SVN/linux-2.6.12
endif

ifeq ($(CONFIG_PLATFORM_MIPS_PLM), y)
EXTRA_CFLAGS += -DCONFIG_BIG_ENDIAN
ARCH:=mips
CROSS_COMPILE:=mipsisa32r2-uclibc-
KVER:= 
KSRC:= /root/work/kernel_realtek
endif

ifeq ($(CONFIG_PLATFORM_MSTAR389), y)
EXTRA_CFLAGS += -DCONFIG_LITTLE_ENDIAN -DCONFIG_PLATFORM_MSTAR389
ARCH:=mips
CROSS_COMPILE:= mips-linux-gnu-
KVER:= 2.6.28.10
KSRC:= /home/mstar/mstar_linux/2.6.28.9/
endif

ifneq ($(KERNELRELEASE),)

ifeq ($(CONFIG_BUILT_IN), y)
obj-y := $(MODULE_NAME).o
else
obj-m := $(MODULE_NAME).o
endif

$(MODULE_NAME)-y += cmd/rtl871x_cmd.o cmd/$(RTL871X)_cmd.o

$(MODULE_NAME)-y += crypto/rtl871x_security.o 
$(MODULE_NAME)-y += debug/rtl871x_debug.o 

$(MODULE_NAME)-y += eeprom/rtl871x_eeprom.o efuse/rtl8712_efuse.o

$(MODULE_NAME)-y += $(_HAL_INTFS_FILES)

$(MODULE_NAME)-y += io/rtl871x_io.o \
            io/$(RTL871X)_io.o

$(MODULE_NAME)-y += ioctl/rtl871x_ioctl_query.o \
                      ioctl/rtl871x_ioctl_set.o \
                       ioctl/rtl871x_ioctl_linux.o \
                    ioctl/rtl871x_ioctl_rtl.o

$(MODULE_NAME)-y += led/rtl8712_led.o

$(MODULE_NAME)-y += mlme/ieee80211.o mlme/rtl871x_mlme.o                
$(MODULE_NAME)-$(CONFIG_MLME_EXT) += mlme/rtl871x_mlme_ext.o mlme/rtl871x_wlan_mlme.o mlme/rtl871x_wlan_sme.o

$(MODULE_NAME)-$(CONFIG_MP_INCLUDED) += mp/rtl871x_mp.o \
                    mp/rtl871x_mp_ioctl.o

$(MODULE_NAME)-y += os_dep/linux/io_linux.o \
                    os_dep/linux/xmit_linux.o \
                    os_dep/linux/cmd_linux.o \
                    os_dep/linux/mlme_linux.o \
                    os_dep/linux/recv_linux.o

$(MODULE_NAME)-y += $(_OS_INTFS_FILES)

$(MODULE_NAME)-y += pwrctrl/rtl871x_pwrctrl.o

$(MODULE_NAME)-y += recv/rtl871x_recv.o recv/$(RTL871X)_recv.o

$(MODULE_NAME)-y += rf/rtl871x_rf.o rf/$(RTL871X)_rf.o
$(MODULE_NAME)-y += sta_mgt/rtl871x_sta_mgt.o

$(MODULE_NAME)-y += xmit/rtl871x_xmit.o xmit/$(RTL871X)_xmit.o

else

all: modules

modules:
    $(MAKE) ARCH=$(ARCH) CROSS_COMPILE=$(CROSS_COMPILE) -C $(KSRC) M=$(PWD)  modules

install:
    install -p -m 644 $(MODULE_NAME).ko  $(MODDESTDIR)
    /sbin/depmod -a ${KVER}

uninstall:
    rm -f $(MODDESTDIR)/$(MODULE_NAME).ko
    /sbin/depmod -a ${KVER}
    
    
config_r:
    @echo "make config"
    /bin/bash script/Configure script/config.in
    
.PHONY: modules clean

clean:
    rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
    rm .tmp_versions -fr ; rm Module.symvers -fr
    cd cmd ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
    cd crypto ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
    cd debug ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
    cd eeprom ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
    cd hal/$(RTL871X) ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
    cd io ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
    cd ioctl ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
    cd led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
    cd mlme ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
    cd mp ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
    cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
    cd os_intf ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
    cd os_intf/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
    cd pwrctrl ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
    cd recv ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
    cd rf ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
    cd sta_mgt ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
    cd xmit; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
    cd efuse; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 

endif

---

### Post by chili555 on 2012-07-30
> #[COLOR="Red"]src=/media/882B-9F61/netisDriver[/COLOR]/Driver/WF-2109/linux/rtl8712_8818_8191_8192SU_usb_linux_v2.6.0006.20100 625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100 615
Does this mean you are trying to build this off the CD? The read-only CD?? Does it change if you drag and drop the folder to your desktop?```
cd Desktop/rtl8712_8818_8191_8192SU_usb_linux_v2.6.0006.20100[COLOR="Red"]\[/COLOR] 625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100[COLOR="Red"]\[/COLOR] 615
sudo su
make
```Any errors or warnings to report? No?```
make install
modprobe 8712u
exit
```

EDIT: The space in the name is troublesome in Linux; Netis ought to know better. Escape the space in the terminal with a backslash:> linux/rtl8712_8818_8191_8192SU_usb_linux_v2.6.0006.20100[COLOR="Red"]\[/COLOR] 625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100[COLOR="Red"]\[/COLOR] 615


---

### Post by csmilovitz on 2012-07-30
Good guess, but no.  /media/882B-9F61 is a memory stick, not the CD-ROM.  It alternatively calls itself "4.0 GB filesystem".  I copied the CD image there and the drive is writable.  I have done a make clean and make there.  The make generates lots of CC calls, putting the output .o files in the directory it is run from.  So that confirms that 882B-9F61 is not the cdrom.

Then I get stuck on make install.

---

### Post by chili555 on 2012-07-30
> Then I get stuck on make install.What is the exact wording of the error? Can you please copy and paste from the terminal and post it here?

I strongly suspect you will have the best luck with an unmodified Makefile. If you don't have it or can't recreate it, trash what you extracted and extract the tarball again for a fresh, unmodified starting point. 

Don't ask me how I know this...

>  (Since it doesn't have a file extension I couldn't include it as an attachment)
You could do:```
cp Makefile Makefile.txt
```And the attach the .txt. However, I have a later version (!!!) of that same file on my computer. 

I need a real life.

---

### Post by csmilovitz on 2012-07-30
Actually cutting and pasting is not that easy.  What I'm trying to do is connect a new machine to the net.  It is not currently connected to my current machine, where I'm doing this communication.  I have to transfer by memory stick, which is also where my development environment is.  So I have to break a lot of open file connections before unmounting.

The message is:
$ sudo make install
[sudo] password for craig:
Makefile:13: /config: No such file or directory
make: *** No rule to make target `/config'. Stop.

If I do 

"craig@crs:/media/882B-9F61/netisDriver/Driver/WF-2109/linux/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625$ ls -l config" 

I get: 

-rw-r--r-- 1 craig craig 457 Jun 25  2010 config

"cat config"  from the same directory shows:

#
# Automatically generated make config: don't edit
#

CONFIG_RTL8711            =    n
CONFIG_RTL8712            =    y


CONFIG_USB_HCI            =    y
CONFIG_SDIO_HCI            =     n


CONFIG_MP_INCLUDED        =    y

CONFIG_PLATFORM_I386_PC        =    y
CONFIG_PLATFORM_ARM_S3C        =     n
CONFIG_PLATFORM_ARM_PXA        =     n
CONFIG_PLATFORM_MIPS_RMI    =     n
CONFIG_PLATFORM_RTK_DMP        =     n
CONFIG_PLATFORM_MIPS_PLM    =     n
CONFIG_PLATFORM_RTD2880B    =    n
CONFIG_PLATFORM_MSTAR389    =    n

CONFIG_MLME_EXT            =     n
CONFIG_DRVEXT_MODULE    = n

---

### Post by chili555 on 2012-07-30
> Actually cutting and pasting is not that easy. Can you copy and paste to a text document, save it, drag it to the USB key and post it that way?> EXTRA_CFLAGS += -O1 -Wno-unused-variable -Wno-unused-value -Wno-unused-label -Wno-unused-parameter -Wno-uninitialized
EXTRA_CFLAGS += -I$(src)/include -Wno-unused -Wno-unused-function

#add assignment to src since it seems uninitialized
src = $(PWD)
#CONFIG_BUILT_in = n_
CONFIG_BUILT_IN = y
#src=/media/882B-9F61/netisDriver/Driver/WF-2109/linux/rtl8712_8818_8191_8192SU_usb_linux_v2.6.0006.20100 625/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100 615

export TOPDIR := $(PWD)

ifeq ($(CONFIG_BUILT_IN), y)
[COLOR="Red"]include $(src)/config[/COLOR]
else
include $(TOPDIR)/config
endifAnd then see:> Makefile:[COLOR="Red"]13[/COLOR]: /config: No such file or directory
make: *** No rule to make target `/config'. Stop.
Is the highlighted line number 13 or elsewhere? Can you confirm you have linux-headers-generic installed?

---

### Post by csmilovitz on 2012-07-30
Ok,

I got Makefile off of the release disk that came with wireless modem I'm installing.  I put it in the directory I mentioned before that I'm building in.  Now I get:

sudo make install
[sudo] password for craig:
Makefile:11 /config: No such file or directory
make: *** No rule to make target `config'. Stop.

The eleventh line of the makefile is include $(TOPDIR)/config

BTW linux-headers-generic is installed (green box in synaptic listing ofmodules)

previously there was: export TOPDIR := $(PWD).

There is a good-looking 'config' file in this directory as mentioned before.

---

### Post by csmilovitz on 2012-07-30
The preceding seems to all have been a wild goose chase.  I finally got make install to work by  not depending on the export $(TOPDIR) = $(PWD) but rather using $(PWD) where $(TOPDIR) was used.

Then I investigate modprobe.  By issuing:

sudo modprobe --first-time -n -v 8712u
FATAL: Module 8712u already in kernel.

So I've been barking up the wrong tree.  There still isn't a lwan0 in ifconfig.

Thanks for all the help so far.

---

### Post by chili555 on 2012-07-30
> FATAL: Module 8712u already in kernel.Let's see:```
lsmod | grep 8712
dmesg | grep 8712
```

---

### Post by csmilovitz on 2012-07-30
As before, dmesg has nothing for 8712 but lsmod returns "8712u   301711  0"

---

### Post by chili555 on 2012-07-31
Let's take a look at your whole dmesg. In order to not flood the forum with a huge, long post, let's zip it:```
dmesg > csm.txt
zip csm.zip csm.txt
```Look in your user directory and find the file csm.zip. Attach it to your reply using the paperclip tool at the top of the reply box.

---

### Post by csmilovitz on 2012-07-31
Here is the csm.txt file generated from dmesg.    It actually looks very bad, now that I looked at it.

Craig

---

### Post by chili555 on 2012-07-31
Your whole file is nothing but repeats of:> [169178.984341] ACPI Exception: AE_LIMIT, while evaluating GPE method [_L09] (20090903/evgpe-568)
[169179.116383] ACPI Error: Illegal I/O port address/length above 64K: 0x00400020/4 (20090903/hwvalid-154)I suggest you Google or go to General Help and get this  sorted. We will have difficulty getting the wireless to work with ACPI in constant error.

[http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

I suggest, if you can't Google a solution, that your thread be titled 'ACPI Error: Illegal I/O port address/length above 64K'

Sorry I can't help with this error. They only let me play with the easier stuff here!

---

### Post by praseodym on 2012-07-31
> Sorry I can't help with this error. They only let me play with the easier stuff here! 

Well, not true ;)

[http://ubuntuforums.org/showpost.php?p=11276560&postcount=44](http://ubuntuforums.org/showpost.php?p=11276560&postcount=44)

Additional GRUB parameters are found here:

[http://forum.ubuntuusers.de/topic/wlan-problem-mit-ar9287-pc-friert-ein/#post-3584572](http://forum.ubuntuusers.de/topic/wlan-problem-mit-ar9287-pc-friert-ein/#post-3584572)

You may want to translate the comments first!

Maybe a BIOS update could also help?!

---

