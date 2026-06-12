---
title: "Compiling rt2870 driver from source"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by Dry Lips on 2011-04-19
I'm trying to install the rt2870 driver on my “server” running Ubuntu Server 8.04.
 I've installed build-essential, checkinstall, cvs, subversion, git-core, mercurial...
 After uncompressing the tarball, doing a "sudo make" gives me this output:
```
make[1]: Entering directory `/usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools' 
 gcc -g bin2h.c -o bin2h 
 make[1]: Leaving directory `/usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools' 
 /usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools/bin2h 
 cp -f os/linux/Makefile.6 /usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/Makefile 
 make -C /lib/modules/2.6.24-28-server/build SUBDIRS=/usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux modules 
 make: *** /lib/modules/2.6.24-28-server/build: No such file or directory.  Stop. 
 make: *** [LINUX] Error 2 

``` I guess I'm stuck... Anyone?

---

### Post by uncaspi on 2011-04-19
It can't find the build folder. Sure you have the headers installed?
If not try sudo apt-get install linux-headers-$(uname-r)
I'm not sure about the right syntax. Perhaps google it.

---

### Post by Dry Lips on 2011-04-19
First of all, thanks for replying!

> **uncaspi said:**
> It can't find the build folder. Sure you have the headers installed?
If not try sudo apt-get install linux-headers-$(uname-r)
I'm not sure about the right syntax. Perhaps google it.

Oh, sorry my bad.
 I've already done ```
sudo apt-get install linux-headers-generic
```Was that the one you referred to?
 
After reading your answer I manually made a folder called build under 
/lib/modules/2.6.24-28-server/
 But shouldn't "make" take care of stuff like that automatically? 
However, running &#8220;make&#8221; again gave me a new error message this time:
  

```
make -C tools 
 make[1]: Entering directory `/usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools' 
 gcc -g bin2h.c -o bin2h 
 make[1]: Leaving directory `/usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools' 
 /usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools/bin2h 
 cp -f os/linux/Makefile.6 /usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/Makefile 
 make -C /lib/modules/2.6.24-28-server/build SUBDIRS=/usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux modules 
 **make[1]: Entering directory `/lib/modules/2.6.24-28-server/build' **
 **make[1]: *** No rule to make target `modules'.  Stop. **
 **make[1]: Leaving directory `/lib/modules/2.6.24-28-server/build' **
 **make: *** [LINUX] Error 2 **
 
```

---
Edit: And for the record, I've never compiled drivers before, so if there is some
common error that n00bs do when attempting this for the first time, please don't
hesitate to point it out!

---

### Post by uncaspi on 2011-04-19
It's not enough to create a build folder.
Try sudo apt-get install linux-headers-$(uname-r)

---

### Post by Dry Lips on 2011-04-19
```
sudo apt-get install linux-headers-$(uname-r)
-bash: uname-r: command not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
```

---

### Post by Dry Lips on 2011-04-19
> **uncaspi said:**
> It's not enough to create a build folder.
Try sudo apt-get install linux-headers-$(uname-r)

are you sure the syntax is correct?

Tried:
sudo apt-get install linux-headers-$
```
Couldn't find package linux-headers-$
```

---

### Post by uncaspi on 2011-04-19
So you need to type uname -r in a terminal and put in the generic digits i.e on mine Linux.
sudo apt-get install linux-headers-2.6.32-28-generic

---

### Post by chili555 on 2011-04-19
Please try:```
sudo apt-get install linux-headers-`uname -r`
```Those tick marks are on the left side of my US keyboard on the same key with ~.

---

### Post by Dry Lips on 2011-04-19
I did:
```
sudo apt-get install linux-headers-2.6.24-28-server
```after doing uname -r and pasting the contents. The installation went just 
fine, but I still get the same error message as above:

```
make -C tools
make[1]: Entering directory `/usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
/usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools/bin2h
cp -f os/linux/Makefile.6 /usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/Makefile
make -C /lib/modules/2.6.24-28-server/build SUBDIRS=/usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux modules
make[1]: Entering directory `/lib/modules/2.6.24-28-server/build'
[B]make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.24-28-server/build'
make: *** [LINUX] Error 2[/B]

```Would it make any difference that I'm running the server edition?

---
edit:
And why couldn't they just include the driver in the repos???

---

### Post by uncaspi on 2011-04-19
Will you try to attach the Makefile in your posting.
I don't think it has anything to do with the server distro except there is a lot of drivers missing.

---

### Post by Dry Lips on 2011-04-20
> **uncaspi said:**
> Will you try to attach the Makefile in your posting.
I don't think it has anything to do with the server distro except there is a lot of drivers missing.

Here you go:

```
RT28xx_MODE = STA
TARGET = LINUX
CHIPSET = 2870
OSABL = NO

#RT28xx_DIR = home directory of RT28xx source code
RT28xx_DIR = $(shell pwd)
RTMP_SRC_DIR = $(RT28xx_DIR)/RT$(CHIPSET)

#PLATFORM: Target platform
PLATFORM = PC
#PLATFORM = 5VT
#PLATFORM = IKANOS_V160
#PLATFORM = IKANOS_V180
#PLATFORM = SIGMA
#PLATFORM = SIGMA_8622
#PLATFORM = STAR
#PLATFORM = IXP
#PLATFORM = INF_TWINPASS
#PLATFORM = INF_DANUBE
#PLATFORM = INF_AR9
#PLATFORM = INF_VR9
#PLATFORM = BRCM_6358
#PLATFORM = INF_AMAZON_SE
#PLATFORM = CAVM_OCTEON
#PLATFORM = CMPC
#PLATFORM = RALINK_2880
#PLATFORM = RALINK_3052
#PLATFORM = SMDK
#PLATFORM = RMI
#PLATFORM = RMI_64
#PLATFORM = KODAK_DC
#PLATFORM = DM6446
#PLATFORM = FREESCALE8377
#PLATFORM = BL2348
#PLATFORM = BLUBB
#PLATFORM = BLPMP
#PLATFORM = MT85XX
#PLATFORM = NXP_TV550
#PLATFORM = MVL5


ifeq ($(TARGET),LINUX)
MAKE = make
endif

ifeq ($(PLATFORM),5VT)
LINUX_SRC = /project/stable/5vt/ralink-2860-sdk/linux-2.6.17
CROSS_COMPILE = /opt/crosstool/uClibc_v5te_le_gcc_4_1_1/bin/arm-linux-
endif

ifeq ($(PLATFORM),IKANOS_V160)
LINUX_SRC = /home/sample/projects/LX_2618_RG_5_3_00r4_SRC/linux-2.6.18
CROSS_COMPILE = mips-linux-
endif

ifeq ($(PLATFORM),IKANOS_V180)
LINUX_SRC = /home/sample/projects/LX_BSP_VX180_5_4_0r1_ALPHA_26DEC07/linux-2.6.18
CROSS_COMPILE = mips-linux-
endif

ifeq ($(PLATFORM),SIGMA)
LINUX_SRC = /root/sigma/smp86xx_kernel_source_2.7.172.0/linux-2.6.15
CROSS_COMPILE = /root/sigma/smp86xx_toolchain_2.7.172.0/build_mipsel_nofpu/staging_dir/bin/mipsel-linux-
endif

ifeq ($(PLATFORM),SIGMA_8622)
LINUX_SRC = /home/snowpin/armutils_2.5.120.1/build_arm/linux-2.4.22-em86xx
CROSS_COMPILE = /home/snowpin/armutils_2.5.120.1/toolchain/bin/arm-elf-
CROSS_COMPILE_INCLUDE = /home/snowpin/armutils_2.5.120.1/toolchain/lib/gcc-lib/arm-elf/2.95.3
endif

ifeq ($(PLATFORM),STAR)
LINUX_SRC = /opt/star/kernel/linux-2.4.27-star
CROSS_COMPILE = /opt/star/tools/arm-linux/bin/arm-linux-
endif

ifeq ($(PLATFORM),RMI)
LINUX_SRC = /opt/rmi/1.7.0/linux/src/
CROSS_COMPILE = /opt/rmi/1.7.0/mipscross/nptl/bin/mips64-unknown-linux-gnu-
endif

ifeq ($(PLATFORM),RMI_64)
LINUX_SRC = /opt/rmi/1.7.0/linux_64/src/
CROSS_COMPILE = /opt/rmi/1.7.0/mipscross/nptl/bin/mips64-unknown-linux-gnu-
endif

ifeq ($(PLATFORM), RALINK_2880)
LINUX_SRC = /project/stable/RT288x/RT288x_SDK/source/linux-2.4.x
CROSS_COMPILE = /opt/buildroot-gdb/bin/mipsel-linux-
endif

ifeq ($(PLATFORM),RALINK_3052)
LINUX_SRC = /home/peter/ap_soc/SDK_3_3_0_0/RT288x_SDK/source/linux-2.6.21.x
CROSS_COMPILE = /opt/buildroot-gcc342/bin/mipsel-linux-uclibc-
endif

ifeq ($(PLATFORM),FREESCALE8377)
LINUX_SRC = /opt/ltib-mpc8377_rds-20090309/rpm/BUILD/linux-2.6.25 
CROSS_COMPILE = /opt/freescale/usr/local/gcc-4.2.187-eglibc-2.5.187/powerpc-linux-gnu/bin/powerpc-linux-gnu-
endif

ifeq ($(PLATFORM),BL2348)
LINUX_SRC = /home/sample/Customers/BroadLight/bl234x-linux-2.6.21-small-v29
CROSS_COMPILE = mips-wrs-linux-gnu-
endif

ifeq ($(PLATFORM),BLUBB)
LINUX_SRC = /home/sample/Customers/BroadLight/UBB/gmp20/linux-2.6.21-small
CROSS_COMPILE = mips-wrs-linux-gnu-
endif

ifeq ($(PLATFORM),BLPMP)
LINUX_SRC = /home/sample/Customers/BroadLight/UBB/pmp16/bl234x-linux-2.6.21-small-v30.2
CROSS_COMPILE = mips-wrs-linux-gnu-
endif

ifeq ($(PLATFORM),PC)
# Linux 2.6
LINUX_SRC = /lib/modules/$(shell uname -r)/build
# Linux 2.4 Change to your local setting
#LINUX_SRC = /usr/src/linux-2.4
LINUX_SRC_MODULE = /lib/modules/$(shell uname -r)/kernel/drivers/net/wireless/
CROSS_COMPILE = 
endif

ifeq ($(PLATFORM),IXP)
LINUX_SRC = /project/stable/Gmtek/snapgear-uclibc/linux-2.6.x
CROSS_COMPILE = arm-linux-
endif

ifeq ($(PLATFORM),INF_TWINPASS)
# Linux 2.6
#LINUX_SRC = /lib/modules/$(shell uname -r)/build
# Linux 2.4 Change to your local setting
LINUX_SRC = /project/stable/twinpass/release/2.0.1/source/kernel/opensource/linux-2.4.31/
CROSS_COMPILE = mips-linux-
endif

ifeq ($(PLATFORM),INF_DANUBE)
LINUX_SRC = /opt/danube/sdk/linux-2.6.16.x
CROSS_COMPILE = mips-linux-
ROOTDIR = /opt/danube/sdk
export ROOTDIR
endif

ifeq ($(PLATFORM),INF_AR9)
LINUX_SRC = /root/ar9/xR9_BSP1.2.2.0/source/kernel/opensource/linux-2.6.20/
CROSS_COMPILE = /root/ar9/ifx-lxdb26-1.0.2/gcc-3.4.4/toolchain-mips/bin/
endif

ifeq ($(PLATFORM),INF_VR9)
LINUX_SRC = /home/public/lantiq/VR9/UGW-4.2/build_dir/linux-ifxcpe_platform_vr9/linux-2.6.20.19
CROSS_COMPILE = /home/public/lantiq/VR9/UGW-4.2/staging_dir/toolchain-mips_gcc-3.4.6_uClibc-0.9.29/bin/mips-linux-
endif

ifeq ($(PLATFORM),BRCM_6358)
LINUX_SRC = 
CROSS_COMPILE = 
endif

ifeq ($(PLATFORM),INF_AMAZON_SE)
# Linux 2.6
#LINUX_SRC = /lib/modules/$(shell uname -r)/build
# Linux 2.4 Change to your local setting
LINUX_SRC = /backup/ifx/3.6.2.2/source/kernel/opensource/linux-2.4.31
#CROSS_COMPILE = mips-linux-
#LINUX_SRC = /project/Infineon/3.6.2.2/source/kernel/opensource/linux-2.4.31
CROSS_COMPILE = /opt/uclibc-toolchain/ifx-lxdb-1-2-3-external/gcc-3.3.6/toolchain-mips/R0208V35/mips-linux-uclibc/bin/
endif

ifeq ($(PLATFORM),ST)
LINUX_SRC = /opt/STM/STLinux-2.2/devkit/sources/kernel/linux0039
CROSS_COMPILE = /opt/STM/STLinux-2.2/devkit/sh4/bin/sh4-linux-
ARCH := sh
export ARCH
endif

ifeq ($(PLATFORM),CAVM_OCTEON)
OCTEON_ROOT = /usr/local/Cavium_Networks/OCTEON-SDK
LINUX_SRC = $(OCTEON_ROOT)/linux/kernel_2.6/linux
CROSS_COMPILE = mips64-octeon-linux-gnu-
endif

ifeq ($(PLATFORM),CMPC)
LINUX_SRC = /opt/fvt_11N_SDK_0807/fvt131x_SDK_11n/linux-2.6.17
CROSS_COMPILE =
endif

ifeq ($(PLATFORM),SMDK)
LINUX_SRC = /home/bhushan/itcenter/may28/linux-2.6-samsung
CROSS_COMPILE = /usr/local/arm/4.2.2-eabi/usr/bin/arm-linux-
endif

ifeq ($(PLATFORM),KODAK_DC)
SKD_SRC = C:/SigmaTel/DC1250_SDK_v1-9/sdk
CROSS_COMPILE = $(cc)
endif

ifeq ($(PLATFORM),DM6446)
LINUX_SRC = /home/fonchi/work/soc/ti-davinci
endif

ifeq ($(PLATFORM),MT85XX)
LINUX_SRC = /home/john/MTK/BDP_Linux/linux-2.6.27
CROSS_COMPILE = armv6z-mediatek-linux-gnueabi-
endif

ifeq ($(PLATFORM),NXP_TV550) 
LINUX_SRC = /data/tv550/kernel/linux-2.6.28.9
LINUX_SRC_MODULE = /data/tv550/kernel/linux-2.6.28.9/drivers/net/wireless
CROSS_COMPILE = /opt/embeddedalley/nxp_tv550/bin/mipsel-linux-
endif

ifeq ($(PLATFORM),MVL5)
LINUX_SRC = /home2/charlestu/AP-VT3426/linux-2.6.18
CROSS_COMPILE = /opt/montavista/pro/devkit/arm/v5t_le_mvl5/bin/arm_v5t_le-
endif

export OSABL RT28xx_DIR RT28xx_MODE LINUX_SRC CROSS_COMPILE CROSS_COMPILE_INCLUDE PLATFORM RELEASE CHIPSET RTMP_SRC_DIR LINUX_SRC_MODULE TARGET

# The targets that may be used.
PHONY += all build_tools test UCOS THREADX LINUX release prerelease clean uninstall install libwapi osabl

all: build_tools $(TARGET)


build_tools:
    $(MAKE) -C tools
    $(RT28xx_DIR)/tools/bin2h

test:
    $(MAKE) -C tools test

LINUX:
ifneq (,$(findstring 2.4,$(LINUX_SRC)))

    cp -f os/linux/Makefile.4 $(RT28xx_DIR)/os/linux/Makefile
    $(MAKE) -C $(RT28xx_DIR)/os/linux/

    cp -f $(RT28xx_DIR)/os/linux/rt$(CHIPSET)sta.o /tftpboot
else
    cp -f os/linux/Makefile.6 $(RT28xx_DIR)/os/linux/Makefile
ifeq ($(PLATFORM),DM6446)
    $(MAKE)  ARCH=arm CROSS_COMPILE=arm_v5t_le- -C  $(LINUX_SRC) SUBDIRS=$(RT28xx_DIR)/os/linux modules
else
ifeq ($(PLATFORM),FREESCALE8377)
    $(MAKE) ARCH=powerpc CROSS_COMPILE=$(CROSS_COMPILE) -C  $(LINUX_SRC) SUBDIRS=$(RT28xx_DIR)/os/linux modules
else
    $(MAKE) -C $(LINUX_SRC) SUBDIRS=$(RT28xx_DIR)/os/linux modules
endif
endif

endif    

clean:
ifeq ($(TARGET), LINUX)
ifneq (,$(findstring 2.4,$(LINUX_SRC)))
    cp -f os/linux/Makefile.4 os/linux/Makefile
else
    cp -f os/linux/Makefile.6 os/linux/Makefile
endif
    $(MAKE) -C os/linux clean
    rm -rf os/linux/Makefile
endif    

uninstall:
ifeq ($(TARGET), LINUX)
ifneq (,$(findstring 2.4,$(LINUX_SRC)))
    $(MAKE) -C $(RT28xx_DIR)/os/linux -f Makefile.4 uninstall
else
    $(MAKE) -C $(RT28xx_DIR)/os/linux -f Makefile.6 uninstall
endif
endif

install:
ifeq ($(TARGET), LINUX)
ifneq (,$(findstring 2.4,$(LINUX_SRC)))
    $(MAKE) -C $(RT28xx_DIR)/os/linux -f Makefile.4 install
else
    $(MAKE) -C $(RT28xx_DIR)/os/linux -f Makefile.6 install
endif
endif
```

---

### Post by Dry Lips on 2011-04-24
Bump!
 
 Now, have I overlooked anything? (Remember, I've never done this before.)
 Here are the instructions that came with the driver. (Which can be found here:[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2))
 
```
Build Instructions:    ==================== 
  
 1> $tar -xvzf RT2870_Linux_STA_x.x.x.x.tgz 
     go to "./RT2870_Linux_STA_x.x.x.x" directory. 
      
 2> In Makefile 
      set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX" 
      define the linux kernel source include file path LINUX_SRC 
      modify to meet your need. 
  
 3> In os/linux/config.mk  
     define the GCC and LD of the target machine 
     define the compiler flags CFLAGS 
     modify to meet your need. 
     ** Build for being controlled by NetworkManager or wpa_supplicant wext functions 
        Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. 
        => #>cd wpa_supplicant-x.x 
        => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d 
     ** Build for being controlled by WpaSupplicant with Ralink Driver 
        Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'. 
        => #>cd wpa_supplicant-0.5.7 
        => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d 
  
 4> $make 
     # compile driver source code 
     # To fix "error: too few arguments to function ¡¥iwe_stream_add_event" 
       => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c 
  
 5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat 
      
 6> load driver, go to "os/linux/" directory. 
     #[kernel 2.4] 
     #    $/sbin/insmod rt2870sta.o 
     #    $/sbin/ifconfig ra0 inet YOUR_IP up 
          
     #[kernel 2.6] 
     #    $/sbin/insmod rt2870sta.ko 
     #    $/sbin/ifconfig ra0 inet YOUR_IP up 
  
 7> unload driver     
     $/sbin/ifconfig ra0 down 
     $/sbin/rmmod rt2870sta 
 
``` Possible errors:
 
**1.** I didn't change anything in the makefile, since I read a post that 
said you didn't need to if you had linuxheaders installed.
 
 **2.** In the config.mk I didn't do anything, except  
```
# Support Wpa_Supplicant 
 HAS_WPA_SUPPLICANT=**y **
  # Support Native WpaSupplicant for Network Maganger 
 HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**n** .

``` I'm not sure if this is right. My wireless router has WPA/WPA2 encryption...
 And I'm not sure what this means:
> &#8220;define the GCC and LD of the target machine 
     define the compiler flags CFLAGS 
     modify to meet your need. &#8221;
 [B]
3.[/B] I didn't have the usb-dongle connected while trying to compile this. 
Do I have to?

---

### Post by chili555 on 2011-04-24
> 1. I didn't change anything in the makefile, since I read a post that
said you didn't need to if you had linuxheaders installed.
Correct.> 2. In the config.mk I didn't do anything, except
Code:

# Support Wpa_Supplicant 
 HAS_WPA_SUPPLICANT=y 
  # Support Native WpaSupplicant for Network Maganger 
 HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n .

I'm not sure if this is right.Nope; please change HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n to HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[COLOR="Red"]y[/COLOR].> And I'm not sure what this means:
Quote:
“define the GCC and LD of the target machine
define the compiler flags CFLAGS
modify to meet your need. ” You may safely ignore this.> 3. I didn't have the usb-dongle connected while trying to compile this.
Do I have to? No.

Since you've made more changes to config.mk, please do:```
cd /location/where/you/downloaded
sudo su
make clean
make
make install
exit
```Note any errors and post them here.

---

### Post by uncaspi on 2011-04-24
I seems to be a strait forward Makefile. Nothing to be done.

---

### Post by chili555 on 2011-04-25
> **uncaspi said:**
> I seems to be a strait forward Makefile. Nothing to be done.I'm not sure I understand. If you were in the correct directory, that is, the same directory as the Makefile, the commands I suggested should have produced several dozen lines of output. Is that what happened?

---

### Post by uncaspi on 2011-04-25
I'm agree. It should have been compiled with those commands

---

### Post by chili555 on 2011-04-25
> **uncaspi said:**
> I'm agree. It should have been compiled with those commandsWould you please try again and give me a screenshot so I can see what's not going correctly?

---

### Post by Dry Lips on 2011-04-25
Wait a minute Chili555. It's me=**Dry Lips** who posted this thread, not **uncaspl**.
I just saw your post. I'll fire up my server right away... I'll try what you suggested
right away. :)

---

### Post by Dry Lips on 2011-04-25
**make clean **
```
cp -f os/linux/Makefile.6 os/linux/Makefile 
 make -C os/linux clean 
 make[1]: Entering directory `/usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux' 
 rm -f ../../common/*.o 
 rm -f ../../common/.*.{cmd,flags,d} 
 rm -f ../../os/linux/*.{o,ko,mod.{o,c}} 
 rm -f ../../os/linux/.*.{cmd,flags,d} 
 rm -fr ../../os/linux/.tmp_versions 
 rm -fr ../../os/linux/Module.markers 
 rm -fr ../../os/linux/Module.symvers 
 rm -fr ../../os/linux/modules.order 
 rm -f ../../chips/*.o 
 rm -f ../../chips/.*.{cmd,flags,d} 
 rm -f ../../sta/*.o 
 rm -f ../../sta/.*.{cmd,flags,d} 
 make[1]: Leaving directory `/usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux' 
 rm -rf os/linux/Makefile 
  
```**make**
```

make -C tools 
 make[1]: Entering directory `/usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools' 
 gcc -g bin2h.c -o bin2h 
 make[1]: Leaving directory `/usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools' 
 /usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools/bin2h 
 cp -f os/linux/Makefile.6 /usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/Makefile 
 make -C /lib/modules/2.6.24-29-server/build SUBDIRS=/usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux modules 
 make: *** /lib/modules/2.6.24-29-server/build: No such file or directory.  Stop. 
 make: *** [LINUX] Error 2 

```
**make install.**
```
make -C /usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux -f Makefile.6 install 
 mkdir: cannot create directory `/etc/Wireless': File exists 
 make[1]: Entering directory `/usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux' 
 rm -rf /etc/Wireless/RT2870STA 
 mkdir /etc/Wireless/RT2870STA 
 cp /usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/RT2870STA.dat /etc/Wireless/RT2870STA/. 
 install -d /lib/modules/2.6.24-29-server/kernel/drivers/net/wireless/ 
 install -m 644 -c rt2870sta.ko /lib/modules/2.6.24-29-server/kernel/drivers/net/wireless/ 
 install: cannot stat `rt2870sta.ko': No such file or directory 
 make[1]: *** [install] Error 1 
 make[1]: Leaving directory `/usr/local/src/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux' 
 make: *** [install] Error 2 

```Last time I did try to create a /lib/modules/2.6.24-29-server/build directory manually.
(It is apparently missing.) When I tried to create one now, I got the same error message as posted previously. (not quoted here.)

Btw, I did enable my root account again, but should using root strictly speaking
be necessary? Why not sudo?

---

### Post by chili555 on 2011-04-25
You should not be using your root account ever. That defeats one of the great strengths of Linux. Running as a user, no passing malware, spyware or virus can install itself. Always use sudo or, if you are doing several commands in a row, sudo su and close out with exit.

Please open System > Administration > Synaptic and confirm that you have linux-headers-2.6.24-29-server and build-essential installed. If not, please do.

---

### Post by Dry Lips on 2011-04-25
> **chili555 said:**
> 
Please open System > Administration > Synaptic and confirm that you have linux-headers-2.6.24-29-server and build-essential installed. If not, please do.
I use Ubuntu server 8.04, so there is no GUI, remember? ;) I removed linux-headers-generic, and the linux-headers I had installed, and reinstalled linux-headers-2.6.24-29-server (but not generic.) And yes, I have build-essential installed. Still no luck! :(
 
> You should not be using your root account ever. That defeats one of the  great strengths of Linux. Running as a user, no passing malware, spyware  or virus can install itself. Always use sudo or, if you are doing  several commands in a row, sudo su and close out with exit.Sorry, my bad. I thought **sudo su** was the same as **su**... I'd normally use **sudo -i**. 
(No worries, I've disabled root.)

---

### Post by Dry Lips on 2011-04-25
However, there's a funny message when I run sudo su. I just ignored it, as it gives
me a #, but perhaps this is a problem after all?

**sudo su**
```
Your account has expired; please contact your system administrator
su: User account has expired
(Ignored)
user@computer:/#
```

---

### Post by chili555 on 2011-04-25
> Last time I did try to create a /lib/modules/2.6.24-29-server/build directory manually.If it is still there, remove it. We are going to try something different. Please do:```
sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

Now try the compile process again and post any errors.

---

### Post by Dry Lips on 2011-04-25
```
make -C tools
make[1]: Entering directory `/usr/local/src/2010_0413_RT3070_Linux_STA_v2.1.3.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/usr/local/src/2010_0413_RT3070_Linux_STA_v2.1.3.0/tools'
/usr/local/src/2010_0413_RT3070_Linux_STA_v2.1.3.0/tools/bin2h
cp -f os/linux/Makefile.6 /usr/local/src/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux/Makefile
make  -C  /lib/modules/2.6.24-29-server/build SUBDIRS=/usr/local/src/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux modules
make[1]: Entering directory `/lib/modules/2.6.24-29-server/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.24-29-server/build'
make: *** [LINUX] Error 2

```

I'm afraid it's the same error as when I created the build folder
manually and then afterwards tried make... (And this time I also
tried to use another driver,  the RT3070, which also supports
my USB-dongle, the D-Link DWA-140 B1.)

---

### Post by Dry Lips on 2011-04-25
I tried **make -rd**

```
GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for i486-pc-linux-gnu
Reading makefiles...
Reading makefile `Makefile'...
Updating makefiles....
 Considering target file `Makefile'.
  Looking for an implicit rule for `Makefile'.
  No implicit rule found for `Makefile'.
  Finished prerequisites of target file `Makefile'.
 No need to remake target `Makefile'.
Updating goal targets....
Considering target file `all'.
 File `all' does not exist.
 Looking for an implicit rule for `all'.
 No implicit rule found for `all'.
  Considering target file `build_tools'.
   File `build_tools' does not exist.
   Finished prerequisites of target file `build_tools'.
  Must remake target `build_tools'.
make -C tools
GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
Putting child 0x0807be88 (build_tools) PID 8725 on the chain.
Live child 0x0807be88 (build_tools) PID 8725 
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for i486-pc-linux-gnu
Reading makefiles...
Reading makefile `Makefile'...
Updating makefiles....
 Considering target file `Makefile'.
  Looking for an implicit rule for `Makefile'.
  No implicit rule found for `Makefile'.
  Finished prerequisites of target file `Makefile'.
 No need to remake target `Makefile'.
Updating goal targets....
Considering target file `all'.
 File `all' does not exist.
 Finished prerequisites of target file `all'.
Must remake target `all'.
make[1]: Entering directory `/usr/local/src/2010_0413_RT3070_Linux_STA_v2.1.3.0/tools'
gcc -g bin2h.c -o bin2h
Putting child 0x0807b5d0 (all) PID 8726 on the chain.
Live child 0x0807b5d0 (all) PID 8726 
Reaping winning child 0x0807b5d0 PID 8726 
Removing child 0x0807b5d0 PID 8726 from chain.
Successfully remade target file `all'.
make[1]: Leaving directory `/usr/local/src/2010_0413_RT3070_Linux_STA_v2.1.3.0/tools'
Reaping winning child 0x0807be88 PID 8725 
/usr/local/src/2010_0413_RT3070_Linux_STA_v2.1.3.0/tools/bin2h
Live child 0x0807be88 (build_tools) PID 8731 
Reaping winning child 0x0807be88 PID 8731 
Removing child 0x0807be88 PID 8731 from chain.
  Successfully remade target file `build_tools'.
  Considering target file `LINUX'.
   File `LINUX' does not exist.
   Finished prerequisites of target file `LINUX'.
  Must remake target `LINUX'.
cp -f os/linux/Makefile.6 /usr/local/src/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux/Makefile
Putting child 0x0807be88 (LINUX) PID 8740 on the chain.
Live child 0x0807be88 (LINUX) PID 8740 
Reaping winning child 0x0807be88 PID 8740 
make  -C  /lib/modules/2.6.24-29-server/build SUBDIRS=/usr/local/src/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux modules
GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
Live child 0x0807be88 (LINUX) PID 8741 
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for i486-pc-linux-gnu
Reading makefiles...
Updating makefiles....
 Considering target file `GNUmakefile'.
  File `GNUmakefile' does not exist.
  Looking for an implicit rule for `GNUmakefile'.
  No implicit rule found for `GNUmakefile'.
  Finished prerequisites of target file `GNUmakefile'.
 Must remake target `GNUmakefile'.
 Failed to remake target file `GNUmakefile'.
 Considering target file `makefile'.
  File `makefile' does not exist.
  Looking for an implicit rule for `makefile'.
  No implicit rule found for `makefile'.
  Finished prerequisites of target file `makefile'.
 Must remake target `makefile'.
 Failed to remake target file `makefile'.
 Considering target file `Makefile'.
  File `Makefile' does not exist.
  Looking for an implicit rule for `Makefile'.
  No implicit rule found for `Makefile'.
  Finished prerequisites of target file `Makefile'.
 Must remake target `Makefile'.
 Failed to remake target file `Makefile'.
Updating goal targets....
Considering target file `modules'.
 File `modules' does not exist.
 Looking for an implicit rule for `modules'.
 No implicit rule found for `modules'.
 Finished prerequisites of target file `modules'.
Must remake target `modules'.
make[1]: Entering directory `/lib/modules/2.6.24-29-server/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.24-29-server/build'
Reaping losing child 0x0807be88 PID 8741 
make: *** [LINUX] Error 2
Removing child 0x0807be88 PID 8741 from chain.
```

Perhaps you'll need to do some changes in the makefile after all..?
[http://www.linuxquestions.org/questions/linux-hardware-18/make%5B1%5D-***-no-rule-to-make-target-%60modules-stop-571661/](http://www.linuxquestions.org/questions/linux-hardware-18/make%5B1%5D-***-no-rule-to-make-target-%60modules-stop-571661/)
And what if it turns out to be a bug? 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/233950](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/233950)

---

### Post by chili555 on 2011-04-26
Frankly, I'm stumped. I wonder if part of the problem is that you have an older kernel and, consequently, gcc version:> 2.6.24-29-serverI believe the fixes you linked should only be necessary if you had a different kernel version from your linux-headers version. Why anyone would do so is beyond me.

Is there a particular reason you are using an old version of Ubuntu? rt2870sta is included in newer versions.

---

### Post by Dry Lips on 2011-04-27
> **chili555 said:**
> 
Is there a particular reason you are using an old version of Ubuntu? rt2870sta is included in newer versions.

Well, yes. I use 8.04 on my LAMP server, which I mainly use for development. 
(The server is an old computer, Celeron 500mhz, 6GB hdd, 64mb ram.) Basically
 I need to use a distro that doesn't eat up the limited resources of my &#8220;beast&#8221;.  
 
 Normally I use my wireless antenna on my desktop, and share my internet connection to my server over my wired network. I occasionally test out other distros alongside Ubuntu on my desktop, but getting the wireless to work without access to the internet is a pain in other distros! So I want to be able to move the antenna to my server,
 and share my internet connection the other way around.
 
 Is the rt2870sta included in newer server editions of Ubuntu? A possible solution could be to ditch Ubuntu 8.04 from my server and install Debian instead. (Or some other lightweight server distro). Do you know if the rt2870 is included in the Debian kernel?  
 
 Thanks a lot for trying to help me out with this. Even if we're stuck for now, you were actually the one who helped me out with my very first thread on this forum:
 [http://ubuntuforums.org/showthread.php?t=1684640](http://ubuntuforums.org/showthread.php?t=1684640)
 
To be frank with you, I probably wouldn't have used Ubuntu now if you hadn't helped me out back then. People quickly loose interest in Ubuntu (and Linux in general) if they don't manage to establish a working internet connection.  
 
So I guess I and probably many more with me, owes you a big THANK YOU!** :D**

---

### Post by chili555 on 2011-04-27
Thank you for your very kind comments. You made my day!

---

