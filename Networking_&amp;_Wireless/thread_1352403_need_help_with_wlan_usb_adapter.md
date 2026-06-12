---
title: "need help with wlan usb adapter"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by alfo982 on 2009-12-11
I just installed UBUNTU 9.10, and now I have the problem to install and configure my wlan usb adapter.
Could anyone of you support me in this work?

First of all how can I verfy if my pen is already recognized by the OS, or I need drivers?
At the moment I have 2 available pens, therefore... I will try with both, I hope that at least 1 of them will work.

So, could you give me instructions in order to make me able to surf in internet?

Thank you so much!!!

PS: I don't have any router... at the moment I'm using an open acess point available in my zone.

please give me an hand...

---

### Post by alfo982 on 2009-12-11
Could anybody help me?

---

### Post by bkratz on 2009-12-11
> **alfo982 said:**
> Could anybody help me?




Go to the terminal   Applications--Accessories--Terminal

And type in 

lspci | grep Wireless

(That is LSPCI in lowercase) and either read the contents and post here or just post what you get here.

If you don't see anything just type in 

lspci

and post here


REREAD and it is USB so substitute lsusb!

---

### Post by alfo982 on 2009-12-11
thank you in advice.

so, with lspci | grep Wireless

no answer

with lspci

> 

all@Linux-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 11)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 11)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)
02:03.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


with lsusb

> 

all@Linux-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 7392:7711  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
all@Linux-desktop:~$ 





---

### Post by bkratz on 2009-12-11
It appears to be some type of Edimax unit from  the ID of

7392:7711
in line 3 of lsusb. But I have not figured just which one it is yet, still looking.

---

### Post by alfo982 on 2009-12-11
I can tell you: it is a Wireless nLite mini-size USB Adapter of the Edimax (EW-7711UMn).
Inside the packet there is also the CD with Linux drivers, but I don't know if I need them in Ubuntu 9.10,if they are compatible with the Kernel and if yes... I don't know how to install them...

---

### Post by bkratz on 2009-12-11
Found a recent thread with the same ID number the 7392:7711 where he had the drivers and built them.  Skip to post number 12 and see if that helps.

[http://ubuntuforums.org/showthread.php?t=1347123&highlight=7392:7711](http://ubuntuforums.org/showthread.php?t=1347123&highlight=7392:7711)

---

### Post by alfo982 on 2009-12-11
but precisely how can I compile the tar.bz2 packet that I have?I've never done it before  and I've no idea how to install it...

---

### Post by alfo982 on 2009-12-11
the makefile inside the packet is as follow:

> 

RT28xx_MODE = STA
TARGET = LINUX
CHIPSET = 3070
#RT28xx_DIR = home directory of RT28xx source code
RT28xx_DIR = $(shell pwd)
RTMP_SRC_DIR = $(RT28xx_DIR)/RT$(CHIPSET)
PLATFORM = PC
#PLATFORM = 5VT
#PLATFORM = IKANOS_V160
#PLATFORM = IKANOS_V180
#PLATFORM = SIGMA
#PLATFORM = SIGMA_8622
#PLATFORM = INIC
#PLATFORM = STAR
#PLATFORM = IXP
#PLATFORM = INF_TWINPASS
#PLATFORM = INF_DANUBE
#PLATFORM = BRCM_6358
#PLATFORM = INF_AMAZON_SE
#PLATFORM = CAVM_OCTEON
#PLATFORM = CMPC
RELEASE = DPO
ifeq ($(PLATFORM),CMPC)
LINUX_SRC = /opt/fvt_11N_SDK_0807/fvt131x_SDK_11n/linux-2.6.17
CROSS_COMPILE =
endif

ifeq ($(PLATFORM),5VT)
LINUX_SRC = /opt/fvt_11N_SDK_0807/fvt131x_SDK_11n/linux-2.6.17
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

ifeq ($(PLATFORM),INIC)
UCOS_SRC = /opt/uCOS/iNIC_rt2880
CROSS_COMPILE = /usr/bin/mipsel-linux-
endif

ifeq ($(PLATFORM),STAR)
LINUX_SRC = /opt/star/kernel/linux-2.4.27-star
CROSS_COMPILE = /opt/star/tools/arm-linux/bin/arm-linux-
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

ifeq ($(PLATFORM),CAVM_OCTEON)
OCTEON_ROOT = /usr/local/Cavium_Networks/OCTEON-SDK
LINUX_SRC = $(OCTEON_ROOT)/linux/kernel_2.6/linux
CROSS_COMPILE = mips64-octeon-linux-gnu-
endif

export RT28xx_DIR RT28xx_MODE LINUX_SRC CROSS_COMPILE CROSS_COMPILE_INCLUDE PLATFORM RELEASE CHIPSET RTMP_SRC_DIR LINUX_SRC_MODULE

all: build_tools $(TARGET)


build_tools:
    make -C tools
    $(RT28xx_DIR)/tools/bin2h

UCOS:
    make -C os/ucos/ MODE=$(RT28xx_MODE)
    echo $(RT28xx_MODE)


LINUX:
ifneq (,$(findstring 2.4,$(LINUX_SRC)))
    cp -f os/linux/Makefile.4 $(RT28xx_DIR)/os/linux/Makefile
    make -C $(RT28xx_DIR)/os/linux/
    cp -f $(RT28xx_DIR)/os/linux/rt$(CHIPSET)sta.o /tftpboot
else
    cp -f os/linux/Makefile.6 $(RT28xx_DIR)/os/linux/Makefile
    make  -C  $(LINUX_SRC) SUBDIRS=$(RT28xx_DIR)/os/linux modules
    cp -f $(RT28xx_DIR)/os/linux/rt$(CHIPSET)sta.ko /tftpboot
endif

release:
ifeq ($(TARGET), LINUX)
    make -C $(RT28xx_DIR)/os/linux -f Makefile.release release
ifeq ($(RELEASE), DPO)
    make -C $(RT28xx_DIR)/os/linux -f Makefile.DPO release
    rm -rf build
endif
endif

clean:
ifeq ($(TARGET), LINUX)
ifneq (,$(findstring 2.4,$(LINUX_SRC)))
    cp -f os/linux/Makefile.4 os/linux/Makefile
else
    cp -f os/linux/Makefile.6 os/linux/Makefile
endif
    make -C os/linux clean
    rm -rf os/linux/Makefile
endif    
ifeq ($(TARGET), UCOS)
    make -C os/ucos clean MODE=$(RT28xx_MODE)
endif

uninstall:
ifeq ($(TARGET), LINUX)
ifneq (,$(findstring 2.4,$(LINUX_SRC)))
    make -C $(RT28xx_DIR)/os/linux -f Makefile.4 uninstall
else
    make -C $(RT28xx_DIR)/os/linux -f Makefile.6 uninstall
endif
endif

install:
ifeq ($(TARGET), LINUX)
ifneq (,$(findstring 2.4,$(LINUX_SRC)))
    make -C $(RT28xx_DIR)/os/linux -f Makefile.4 install
else
    make -C $(RT28xx_DIR)/os/linux -f Makefile.6 install
endif
endif





should I modify something?

---

### Post by bkratz on 2009-12-11
Isn't there also a readme file in the folder you extracted? The directions should be there.

---

### Post by alfo982 on 2009-12-11
readme file:

> 

* README
*
* Ralink Tech Inc.
* 
* [http://www.ralinktech.com](http://www.ralinktech.com)
*

=======================================================================
ModelName:
===========
RT2870 Wireless Lan Linux Driver


=======================================================================
Driver lName:
===========
rt2870.o/rt2870.ko


=======================================================================
Supporting Kernel:
===================
linux kernel 2.4 and 2.6 series. 
Tested in Redhat 7.3 or later.


=======================================================================
Ralink Hardware:
===================
Ralink 802.11n Wireless LAN Card.


=======================================================================
Description:
=============
This is a linux device driver for Ralink RT2870 USB ABGN WLAN Card.


=======================================================================
Contents:
=============
Makefile            : Makefile
*.c                    : c files
*.h                    : header files


=======================================================================
Features:
==========
   This driver implements basic IEEE802.11. Infrastructure and adhoc mode with 
   open or shared or WPA-PSK or WPA2-PSK authentication method. 
   NONE, WEP, TKIP and AES encryption. 


=======================================================================
Build Instructions:  
====================

1> $tar -xvzf DPB_RT2870_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2870_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
     define the linux kernel source include file path LINUX_SRC
     modify to meet your need.

3> In os/linux/config.mk 
    define the GCC and LD of the target machine
    define the compiler flags CFLAGS
    modify to meet your need.
    ** Build for being controlled by NetworkManager
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
    ** Build for being controlled by WpaSupplicant with Ralink Custom Event
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
       command: #./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make                                    # compile driver source code

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
    
=======================================================================
CONFIGURATION:  
====================
RT2870 driver can be configured via following interfaces, 
i.e. (i)"iwconfig" command, (ii)"iwpriv" command, (iii) configuration file

i)  iwconfig comes with kernel.  
ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.
iii)modify configuration file "RT2870STA.dat" in /etc/Wireless/RT2870STA/RT2870STA.dat.
           
Configuration File : RT2870STA.dat
---------------------------------------
# Copy this file to /etc/Wireless/RT2870STA/RT2870STA.dat
# This file is a binary file and will be read on loading rt.o module.
#
# Use "vi RT2870STA.dat" to modify settings according to your need.
# 
# 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infrastructure
# 2.) set Channel to "0" for auto-select on Infrastructure mode
# 3.) set SSID for connecting to your Accss-point.
# 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE"
# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES"
# for more information refer to the Readme file.
# 
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
SSID=Dennis2860AP
NetworkType=Infra
WirelessMode=9
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
WmmCapable=0
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
FastRoaming=0
RoamThreshold=70
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
EthConvertMode=
EthCloneMac=
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0

-----------------------------------------------
*NOTE:
    WMM parameters
            WmmCapable            Set it as 1 to turn on WMM Qos support                
            AckPolicy1~4        Ack policy which support normal Ack or no Ack
                                (AC_BK, AC_BE, AC_VI, AC_VO)        
    
    All WMM parameters do not support iwpriv command but ¡¥WmmCapable¡¦¡¦, 
    please store all parameter to RT2870STA.dat, and restart driver.     

-----------------------------------------------
syntax is 'Param'='Value' and describes below. 

@> CountryRegion=value                                 
    value
        0: use 1 ~ 11 Channel
        1: use 1 ~ 13 Channel
        2: use 10 ~ 11 Channel
        3: use 10 ~ 13 Channel
        4: use 14 Channel
        5: use 1 ~ 14 Channel
        6: use 3 ~ 9 Channel
        7: use 5 ~ 13 Channel
                                                  
@> CountryRegionForABand=value                                  
    value    
        0: use 36, 40, 44, 48, 52, 56, 60, 64, 149, 153, 157, 161, 165 Channel
        1: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140 Channel
        2: use 36, 40, 44, 48, 52, 56, 60, 64 Channel
        3: use 52, 56, 60, 64, 149, 153, 157, 161 Channel
        4: use 149, 153, 157, 161, 165 Channel
        5: use 149, 153, 157, 161 Channel
        6: use 36, 40, 44, 48 Channel
        7: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140, 149, 153, 157, 161, 165 Channel
        8: use 52, 56, 60, 64 Channel
        9: use 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140 Channel
                                                           
@> SSID=value                    
    value
        0~z, 1~32 ascii characters.
                        
@> WirelessMode=value
    value    
        0: legacy 11b/g mixed 
        1: legacy 11B only 
        2: legacy 11A only         //Not support in RfIcType=1(id=RFIC_5225) and RfIcType=2(id=RFIC_5325)
        3: legacy 11a/b/g mixed     //Not support in RfIcType=1(id=RFIC_5225) and RfIcType=2(id=RFIC_5325)
        4: legacy 11G only
        5: 11ABGN mixed
        6: 11N only
        7: 11GN mixed
        8: 11AN mixed
        9: 11BGN mixed
       10: 11AGN mixed    
                     
@> Channel=value
    value
        depends on CountryRegion or CountryRegionForABand
                        
@> BGProtection=value
    value
        0: Auto 
        1: Always on 
        2: Always off
                        
@> TxPreamble=value
      value
        0:Preamble Long
        1:Preamble Short 
        2:Auto
                        
@> RTSThreshold=value
    value
        1~2347                                                       
                                                               
@> FragThreshold=value
    value           
        256~2346
                        
@> TxBurst=value
    value
        0: Disable
        1: Enable

@> NetworkType=value                
    value 
        Infra: infrastructure mode
           Adhoc: adhoc mode
                                                                                                                                                                                                                      
@> AuthMode=value
    value
        OPEN         For open system    
        SHARED          For shared key system    
        WEPAUTO     Auto switch between OPEN and SHARED
        WPAPSK      For WPA pre-shared key  (Infra)
        WPA2PSK     For WPA2 pre-shared key (Infra)
        WPANONE        For WPA pre-shared key  (Adhoc)
        WPA         Use WPA-Supplicant
        WPA2        Use WPA-Supplicant

@> EncrypType=value
    value
        NONE        For AuthMode=OPEN                    
        WEP            For AuthMode=OPEN or AuthMode=SHARED 
        TKIP        For AuthMode=WPAPSK or WPA2PSK                    
        AES            For AuthMode=WPAPSK or WPA2PSK                     
        
@> DefaultKeyID=value
    value
        1~4

@> Key1=value
    Key2=value
    Key3=value
    Key4=value
    value
        10 or 26 hexadecimal characters eg: 012345678
        5 or 13 ascii characters eg: passd
    (usage : "iwpriv" only)     

@> Key1Type=vaule
    Key2Type=value
    Key3Type=vaule
    Key4Type=vaule
    value
        0   hexadecimal type
        1   assic type
    (usage : reading profile only)

@> Key1Str=value
    Key2Str=value
    Key3Str=vaule
    Key4Str=vaule
    value
        10 or 26 characters (key type=0)
        5 or 13 characters  (key type=1)
    (usage : reading profile only)    

@> WPAPSK=value                  
    value
        8~63 ASCII          or 
        64 HEX characters
                                                                                                                                                            
@> WmmCapable=value
    value
        0: Disable WMM
        1: Enable WMM
        
@> PSMode=value
    value
        CAM                Constantly Awake Mode
        Max_PSP            Max Power Savings
        Fast_PSP        Power Save Mode

@> FastRoaming=value
    value
        0                Disabled
        1                Enabled

@> RoamThreshold=value
    value
        Positive Interger(dBm)

@> HT_RDG=value
    value
        0                Disabled
        1                Enabled

@> HT_EXTCHA=value (Extended Channel Switch Announcement)
    value
        0                Below
        1                 Above

@> HT_OpMode=value
    value
        0                HT mixed format
        1                HT greenfield format

@> HT_MpduDensity=value
    value (based on 802.11n D2.0)
        0: no restriction
        1: 1/4 £gs
        2: 1/2 £gs
        3: 1 £gs
        4: 2 £gs
        5: 4 £gs
        6: 8 £gs
        7: 16 £gs

@> HT_BW=value
    value
        0                20MHz
        1                40MHz

@> HT_AutoBA=value
    value
        0                Disabled
        1                Enabled

@> HT_BADecline
    value
        0                Disabled
        1                Enabled <Reject BA request from AP>

@> HT_AMSDU=value
    value
        0                Disabled
        1                Enabled

@> HT_BAWinSize=value
    value
        1 ~ 64

@> HT_GI=value
    value
        0                long GI
        1                short GI

@> HT_MCS=value
    value
        0 ~ 15
        33: auto

@> HT_MIMOPSMode=value
    value (based on 802.11n D2.0)
        0                Static SM Power Save Mode
        1                Dynamic SM Power Save Mode
        2                Reserved
        3                SM enabled
    (not fully support yet)

@> EthConvertMode=value
    value
        dongle
        clone
        hybrid

@> EthCloneMac=value
    value
        xx:xx:xx:xx:xx:xx

@> IEEE80211H=value
    value
        0                Disabled
        1                Enabled

@> TGnWifiTest=value
    value
        0                Disabled
        1                Enabled

@> WirelessEvent=value
    value
        0                Disabled
        1                Enabled <send custom wireless event>
        
MORE INFORMATION
=================================================================================
If you want for rt2870 driver to auto-load at boot time:
A) choose ra0 for first RT2870 WLAN card, ra1 for second RT2870 WLAN card, etc.
   
B) create(edit) 'ifcfg-ra0' file in /etc/sysconfig/network-scripts/,      
   edit( or add the line) in /etc/modules.conf:
       alias ra0 rt2870sta
   
C) edit(create) the file /etc/sysconfig/network-scripts/ifcfg-ra0  
   DEVICE='ra0'
   ONBOOT='yes'     


NOTE:
   if you use dhcp, add this line too .
    BOOTPROTO='dhcp'

*D) To ease the Default Gateway setting, 
    add the line
    GATEWAY=x.x.x.x   
    in /etc/sysconfig/network
=======================================================================
Dongle/Clone Features:
======================
A) Dongle mode: 
       Provides a 1-to-N MAC address mapping mechanism such that more than one PC behind the STA 
       can transparently connect to the AP.

B) Clone mode:
    Provides a 1-to-1 MAC address mapping mechanism. 
    STA can use own MAC as SA MAC or 
            use user desired MAC as SA MAC or
            use source MAC of first packet coming from wired device as SA MAC.
    NOTE: In this mode, only the PC who own the specified MAC can connect to the AP.

 
C) Hybrid mode(Dongle+Clone):
    Provides a 1-to-N MAC address mapping mechanism such that more than one PC behind the STA 
       can transparently connect to the AP.
    STA can use own MAC as SA MAC or 
            use user desired MAC as SA MAC or
            use source MAC of first packet coming from wired device as SA MAC.

D) Please refer to "Config STA to link as dongle mode..." in iwpriv_usage.txt for releated commands.




wtf... I've linux from 2 days... really: points 1 to 7 are more or less arabian for me...

what do you suggest me to do?

---

### Post by bkratz on 2009-12-11
Sorry, I have only built one driver myself and wouldn't pretend to give advice to someone else regarding that. I would probably try it myself; but I probably would be of little use directing you.  I did find this which is supposed to be directions on building RT2870 driver you need.  Maybe someone else will step in and help. Anyway here is the link, hope it helps.

[http://ubuntuforums.org/showthread.php?t=1342593&highlight=rt2870](http://ubuntuforums.org/showthread.php?t=1342593&highlight=rt2870)

---

### Post by alfo982 on 2009-12-12
But just a question: without any driver, I can see the wireless network in the network manager (little icon of an antenna, near the mail icon and time icon, on the bar upper right side of the desktop). There I can see a voice (that is absent when the pen is unplugged) of "wireless networks". But it is, as well as the other 2 voices of LAN cards, gray and unclickable.

So the question is... do I really need the installation of these drivers, or maybe I need simply the configuration of the internet settings?

How can I verify that?

Let me know, if you can...

thx

---

### Post by bkratz on 2009-12-12
Probably the easiest  would be to go to the terminal and type

lshw -C network

(that is LSHW in lowercase)!

And copy and paste the output here.

---

### Post by alfo982 on 2009-12-12
et voilà...


> WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 10
       serial: 00:0e:e8:8e:f5:5e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:22 ioport:b400(size=256) memory:ed000000-ed0000ff memory:efe00000-efe0ffff(prefetchable)
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:02:0b.0
       logical name: eth1
       version: 10
       serial: 00:06:7b:08:b4:13
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:23 ioport:b000(size=256) memory:ec800000-ec8000ff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan5
       serial: 00:1f:1f:74:21:d0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn
all@Linux-desktop:~$ 



thx

---

### Post by bkratz on 2009-12-12
Here's mine (in part)

 *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1b:11:f3:3b:fb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netmw245 driverversion=1.55+Marvell,11/27/2006,1.0.4.9 multicast=yes wireless=IEEE 802.11g


See the diference? Mine shows a driver that being Ndiswrapper + netmw245
driverversion =1.55

Yours doesn't show an assigned driver, I believe that is why your wireless network is not highlighted in your picture.

To be sure you could go to the terminal and type

iwlist scan  (IWLIST in lowercase)  If the card 'sees' any networks it will show you with this command.

---

### Post by alfo982 on 2009-12-12
ok.... I tried the same procedure with the second pen that I have (do you remember, at the beginning of this topic I said that I have 2 available pens... ).

Well, the results with this one are:

> all@Linux-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 10
       serial: 00:0e:e8:8e:f5:5e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:22 ioport:b400(size=256) memory:ed000000-ed0000ff memory:efe00000-efe0ffff(prefetchable)
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:02:0b.0
       logical name: eth1
       version: 10
       serial: 00:06:7b:08:b4:13
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:23 ioport:b000(size=256) memory:ec800000-ec8000ff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:67:f0:62:fd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netw35g driverversion=1.55+Winbond Electronics Corp.,0 multicast=yes wireless=IEEE 802.11g
all@Linux-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     No scan results




As you can see... this pen has the drivers that I've installed via ndiswrapper!

And also in this case... no way...

What the hell has my Computer??? I'm going crazy...

---

### Post by alfo982 on 2009-12-12
ah, just another clarification: with this second pen I installed the win drivers via ndisgtk.
But in "Wireless network Drivers" insterface, when I click on the "Configure Network" button, nothing happens... why in your opinion?

---

### Post by bkratz on 2009-12-12
> **alfo982 said:**
> ah, just another clarification: with this second pen I installed the win drivers via ndisgtk.
But in "Wireless network Drivers" insterface, when I click on the "Configure Network" button, nothing happens... why in your opinion?



Sorry, I didn't see your post until just now, I will subscribe so I don't miss it again.

Doesn't it say something like "could not find network configuration tool" ?  I have received that message since my first install with Ndisgtk and have simply ignored it. 

If you go to the network icon ( upper right corner ) and right click on it do you get a pop up that says something like enable network and edit connections?  Here is where you set your AP name and connection information by selecting the wireless tab and "add connection". It does require password to change the info. I would just be sure to select the button for "make available to all users".  Try without encryption first just to see if things are working.v  Remember to disconnect the wired connection. If you left click on it you should see the available networks.

---

### Post by alfo982 on 2009-12-13
Ok... now I try! But is it not like windows, where you receive the whole list of available AP, and then  you can choose one of them?
If I have right understood, here in Linux you have to insert the data of a precise AP, and then connect to it. Is it right?

however, now I try to configure the AP that I normally use with Windows on the other computer...

---

### Post by alfo982 on 2009-12-13
OK... I tell you what I've done:

I'm gone in network connections and I canceled the wired network.
then I'm gone in Wireless tab and I added a new connection; now is the problem: for SSID I put the name recongized by win on the other computer, but what about BSSID and MAC addr.? where can I find these values?

At the end where should I find this new network? how can I connect to it?

---

### Post by alfo982 on 2009-12-13
oh, just another thing: let have a look here...

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax)

one of the 2 pens of mine  is the EW-7711UMn, and it is written that it works out of the box in Jaunty... do you suggest me to downgrade to 9.04 (in other words... reinstall an old version of ubuntu...)?

this should make the usb adapter able to work directly without any manual setting or driver installation (is this the meaning of "work out of the box"... isn't it?)

---

### Post by alfo982 on 2009-12-13
GOOD NEEEWWWSSSS mate!
I reinstalled jaunty version... and now everything works automatically!!!
thank you so much for your support!!!

---

### Post by bkratz on 2009-12-13
Certainly glad to hear you got it working.  Some people have had issues with 9.10 and wireless (me being 1!) and have considered going back myself, but I really like everything else in 9.10 so much better that I temporarily use a network cable. 

Congratulations!!

---

