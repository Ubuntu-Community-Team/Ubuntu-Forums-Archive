---
title: "Connecting to Internet On Boot Up With AWLL6075"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by mothdragon on 2010-04-19
I have an AWL6075 Golden N Wireless Mini USB Adapter from Airlink, and I'm running Ubuntu 9.10. (Kernel 2.6.31-20-generic) I've learned that in order to get this to work, I needed to download this firmware update: [http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz) and copy it into /lib/firmware.

I have also needed to download and install the drivers at [http://www.filestube.com/f76673d157e2ab6203ea/go.html](http://www.filestube.com/f76673d157e2ab6203ea/go.html)

I've even Edited my connection to make it available to all users.

This is great, and it gets my internet running. Unfortunately, I seem to have to make the module, and insmod the module 8712u.ko everytime I boot up. I know I had it set in 9.04 to be able to do this on boot up, but in 9.04 I didn't have to re-make it everytime... Can anyone help me to get my adapter to connect automatically at boot-up? Thanks.

---

### Post by chili555 on 2010-04-19
Did you finish the process with sudo make install? If you, you should be able to add the module to /etc/modules and be all set.

---

### Post by mothdragon on 2010-04-19
Ok, I'm not sure why, but when I try the make install I get a much shorter process than just make on it's own... however, it completely incapacitated my connection, and I had to make uninstall, make clean, rmmod and then make all over again, and insmod (and a variation on the order of these commands a few times and a couple of reboots) before I was finally able to connect again... 
I also added the line 8712u (the name of the module) to /etc/modules but have since commented it out by putting the # in front of the 8712u, but I had originally added the 8712u line before trying to get it to start at boot up but didn't think to do a make install... needless to say, the make install didn't work...
The instructions that come with the driver say to:
   make
   ./clean
   insmod 8712u.ko
   ifconfig wlan0 up

I have found that I don't need to do the ifconfig line as just doing the insmod 8712u.ko activates my connection. Of course, in 9.10 these instructions didn't work at all until I installed the firmware update that I mentioned earlier.

I don't know if it helps, but perhaps someone who has more knowledge than I will understand the makefile which is:

EXTRA_CFLAGS += -O1 -Wno-unused-variable -Wno-unused-value -Wno-unused-label -Wno-unused-parameter -Wno-uninitialized
EXTRA_CFLAGS += -I$(src)/include  -Wno-unused -Wno-unused-function

CONFIG_BUILT_IN = n

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

ifeq ($(CONFIG_PLATFORM_MIPS_RMI), y)
EXTRA_CFLAGS += -DCONFIG_LITTLE_ENDIAN
ARCH:=mips
CROSS_COMPILE:=mipsisa32r2-uclibc-
KVER:= 
KSRC:= /root/work/kernel_realtek
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


I did note that there is a difference from the make verses the make install, where using the make method I have to insmod 8712u.ko, where the make install performs a depmod itself so that I don't have to manually install the module.

Thanks for the help!

---

### Post by mothdragon on 2010-04-25
Okay so I take it back... It does work... After doing all that stuff in the previous post, and switching back to inserting the module each time, it continued to inform me that the module 8712u was already inserted, even though I thought I had told it not to do that.... 

So after all that I did above, it occurred to me that perhaps somewhere a conflict had arisen, so I tried just adding the line 8712u to the /etc/modules file again, and voila! It worked like a charm. Thank you for your help, and I apologize for my Newbiness :)

Take care, and Be Blessed

---

### Post by WrathofGod on 2010-12-08
Hello,

Sorry, but I'm having more than a fair share of troubles getting this to work. Is there a way you could do a step by step instructions or a video capture and upload that on youtube for me? Both me and a friend have this card and we can't figure it out. THANK YOU SO MUCH if you can help us out!

---

### Post by balak on 2011-01-06
> **WrathofGod said:**
> Hello,

Sorry, but I'm having more than a fair share of troubles getting this to work. Is there a way you could do a step by step instructions or a video capture and upload that on youtube for me? Both me and a friend have this card and we can't figure it out. THANK YOU SO MUCH if you can help us out!

Which version of ubuntu are you using? We can try to help based on that. Also, if you can, tell us the output of 'uname -a' when you type it on a terminal (Applications->Accesories->Terminal).

I also recently got this card for my desktop. 
All I did was download the firmware, unzip it, and copy to /lib/firmware/ and it seems to work fine so far. I use ubuntu lucid 10.04.

Detailed steps:
1. Download the firmware posted at
[http://ubuntuforums.org/showpost.php?p=9311531&postcount=15](http://ubuntuforums.org/showpost.php?p=9311531&postcount=15)
The file name is rtl8192swf.bin.gz
2. Open a terminal and cd to the directory where you have downloaded the firmware. For example if the download is in 'Downloads' directory, type 
'cd Downloads' and press enter.
3. type 'gunzip rtl8192swf.bin.gz' - what this will do is to unzip the file. 
4. type 'sudo mkdir /lib/firmware/`uname -r`/RTL8192SU'. Type all this rather than copy/paste. This will create a directory called RTL8192SU corresponding to your current running kernel. This step may ask for your passwd since you will need root permissions to add this directory.
5. type 'sudo cp rtl8192swf.bin /lib/firmware/`uname -r`/RTL8192SU'. This will copy the file into that directory. 

After this, you can just remove and re-insert the adapter. The system should see the new driver and start using it. You should go to 'network manager' (the network icon on the top panel, close to the right side) and choose your wireless network. 

let me know if this helps.

---

### Post by balak on 2011-01-06
Here is the bug no. for reference:
[https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455](https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455)

---

