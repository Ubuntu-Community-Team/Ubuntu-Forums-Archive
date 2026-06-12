---
title: "No-hassle out-out-of-the-box wireless adapter"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by Mister J on 2009-01-31
Hello. I have read a few answers to this, but none were very satisfying. I want to know what exactly I need to buy to get wireless internet easily on my computer. I used Wubi to install Ubuntu 64bit on my normally Vista 64bit desktop. Can someone please reccomend a wireless adapter model that will install without hassle? I want to learn linux, but not having internet on it is crippling me. 

I already have a Linksys WUSB100 adapter, but so far trying to learn how to get it working in Ubuntu is confusing me to no end.

---

### Post by pytheas22 on 2009-01-31
If you post the output of this command with the WUSB100 plugged in:
```

lsusb
```

I'll try to give you instructions for making it work on Ubuntu.

As for purchasing a new card: there are many that work out-of-the-box, but the problem with finding them is that most hardware manufacturers have a habit of changing the insides of devices without changing the names they're sold under.  This means that you could buy two wireless cards with the same exact name and sold in the same box, but because they have different chipsets inside, Linux might work painlessly with one, but not so well with another.  The only way to identify a card for sure is to plug it into a computer and see its 'lsusb' and 'lspci' descriptions.

There's a [page]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") of cards that are purported to work, but because you can't be sure that there aren't multiple versions of them floating around under the same name, the list is not very reliable.  Your best bet is to purchase a card from a store with a flexible return policy, and bring it back if it turns out not to be plug-and-play with Linux.

That said, I bet we can make your existing card work, so don't give up yet.

---

### Post by sirebral on 2009-01-31
This link should help.  It provides two options -NDISWrapper, or the native Linux driver and firmware

[http://www.linuxforums.org/forum/wireless-internet/118831-wusb100-help-please.html](http://www.linuxforums.org/forum/wireless-internet/118831-wusb100-help-please.html)

Others might suggest NDISWrapper, but I had a terrible experience with it so I suggest the native Linux driver and firmware.

---

### Post by Mister J on 2009-01-31
@pytheas22
Thank you so much for giving me a bit of hope. I thought I might never get this solved. If I can just get the internet running on it, I can get downloads and etc. to help me.

Here is lsusb.(Small possibility of errors. I hand copied it)
Bus 007 Device 001: ID 1d6b:0001 linux foundation 1.1 root hub
Bus 006 Device 006: ID 0a48:3302 I/O Interconnect
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 004: ID 1737:0070 Linksys
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0461:4b16 Primax Electronics, LTD
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

@Sirebral
Thank you, but I don't know how to get NDISwrapper, and I didn't understand the other method. Pretend you're explaining it to Michael Scott from the office. lol

---

### Post by pytheas22 on 2009-02-01
There's a driver for your Linksys card (which apparently has an rt2870 chipset, in case you care) available [here]("http://www.ralinktech.com/ralink/Home/Support/Linux.html").  At some point in the future, it will probably be built into Ubuntu (meaning that your card will become one of the ones that 'just work'), but for the time being you have to install it manually.  Please follow these instructions to do that:

1. on a computer with Internet access, download [this file]("http://www.ralinktech.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2").  Transfer it to your Ubuntu computer and save it on the desktop there.

2. put your Ubuntu installation CD in your disk drive (if you don't have an Ubuntu CD, please [download one]("http://www.ubuntu.com/getubuntu/download"); if this is a real hassle, let me know and we can work around it), then go to System>Administration>Software Sources.  Under the 'Ubuntu Software' tab, you should see a box to enable the use of your CD as a repository (if you're unsure what I'm talking about, I can post a screenshot).  Make sure this box is checked, then close the window.  If you're asked about reloading the sources list, say yes.

3. open a terminal from the Applications>Accessories menu and run these commands:
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf 2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2
cd 2008_0925_RT2870_Linux_STA_v1.4.0.0/
sudo make
sudo modprobe os/linux/rt2870sta.ko
```

At this point, if all has gone well, your wireless card should start working and you should be able to connect using Network Manager.  If it's not working, please post the output of all of the above, as well as the following commands:
```

lshw -C Network
sudo iwlist scan
dmesg | grep -e rt2 -e wlan
iwconfig
```

If it does work at this point, that's good, but if you reboot your computer it will stop working.  However we can fix that by making the installation permanent once we confirm that this works (for now, the changes you make will essentially be erased by a reboot).

***FYI: to make it easier to post output from the terminal on this website even though you have no Internet connection in Ubuntu, you could first paste the output into a text file (you can open a blank text file by going to Applications>Accessories>Text Editor), then save it onto a USB stick or CD and transfer it to a computer with Internet access, where you can copy and paste into the forum.  (Alternatively, if you installed Ubuntu via wubi, you should be able to access your Windows drive from Ubuntu by going to Places>Home Folder, then putting the location '/host' in the address bar.  This corresponds to your C:\ drive in Windows, and you can save files there for accessing in Windows).  It's a lot better than typing it out by hand!

---

### Post by Mister J on 2009-02-01
I'm sorry, it didn't work.

Step 1 went as planned.
Step 2: I have the CD, and attempted to do what you said. I didnt see any specific box to check for "Use CD as repository" but there was a white box that had the CD's name in it, and I checked that box. Reloading source list did not work, every single one said it failed. (Maybe a screen shot would help)
I also ran those commands you told me to run if it didnt work, those are seperated by -----) Also, when prompted to put a disk in the drive and hit enter, it never recognized the disk. I tried several times. Thank you so much for helping me out. I'm sure we can get it eventually.

Here is what happened while using the terminal.:
laughingmrj@ubuntu:~$ sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/main Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/restricted Translation-en_US
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
laughingmrj@ubuntu:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.3 libstdc++6-4.3-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg
  libstdc++6-4.3-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.3 libstdc++6-4.3-dev patch
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6932kB of archives.
After this operation, 23.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)'
in the drive '/cdrom/' and press enter
cd ~/desktop
Err cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/main libstdc++6-4.3-dev 4.3.2-1ubuntu11
  Disk not found.
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/pool/main/g/gcc-4.3/libstdc++6-4.3-dev_4.3.2-1ubuntu11_amd64.deb  Disk not found.
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
laughingmrj@ubuntu:~$ tar -xjvf 2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2
tar: 2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
laughingmrj@ubuntu:~$ cd 2008_0925_RT2870_Linux_STA_v1.4.0.0/
bash: cd: 2008_0925_RT2870_Linux_STA_v1.4.0.0/: No such file or directory
laughingmrj@ubuntu:~$ sudo make
make: *** No targets specified and no makefile found.  Stop.
laughingmrj@ubuntu:~$ sudo modprobe os/Linux/rt2870sta.ko
FATAL: Module os/Linux/rt2870sta.ko not found.
laughingmrj@ubuntu:~$ 

-----------


laughingmrj@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:22:68:3a:a3:4f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 96:99:a9:35:4f:e0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
laughingmrj@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

laughingmrj@ubuntu:~$ dmesg | grep -e rt2 -e wlan
laughingmrj@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

laughingmrj@ubuntu:~$

---

### Post by pytheas22 on 2009-02-01
Sorry it didn't work.  The problem was that the system wasn't able to use your CD as a repository for some reason.  I don't know why it failed.  But let's try a second approach that doesn't involve the CD (sorry for making your burn it if it turns out not to be necessary).

First, download these four files and save them to your desktop on Ubuntu: [file1]("http://ubuntu.secs.oakland.edu/pool/main/d/dpkg/dpkg-dev_1.14.20ubuntu6_all.deb") [file2]("http://ubuntu.secs.oakland.edu/pool/main/g/gcc-defaults/g++_4.3.1-1ubuntu2_amd64.deb") [file3]("http://ubuntu.secs.oakland.edu/pool/main/g/glibc/libc6-dev_2.8~20080505-0ubuntu7_amd64.deb") [file4]("http://ubuntu.secs.oakland.edu/pool/main/m/make-dfsg/make_3.81-5_amd64.deb").  Then run this command:
```

cd ~/Desktop
sudo dpkg -i *deb
```

Then proceed with the following commands:

```
cd ~/Desktop
tar -xjvf 2008*
cd 2008*
gedit os/linux/config.mk
```

At this point a file will pop open.  Please erase everything in the file, and replace it with the following:

```
# Support ATE function
HAS_ATE=n

# Support 28xx QA ATE function
HAS_28xx_QA=n

# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

#Support Net interface block while Tx-Sw queue full
HAS_BLOCK_NET_IF=n

#Support DFS function
HAS_DFS_SUPPORT=n

#Support Carrier-Sense function
HAS_CS_SUPPORT=n

#ifdef MULTI_CARD
# Support for Multiple Cards
HAS_MC_SUPPORT=n
#endif // MULTI_CARD //

#Support for IEEE802.11e DLS
HAS_QOS_DLS_SUPPORT=n

#Support for EXT_CHANNEL
HAS_EXT_BUILD_CHANNEL_LIST=n

#Support for Net-SNMP
HAS_SNMP_SUPPORT=n

#Support features of Single SKU. 
HAS_SINGLE_SKU_SUPPORT=n

#Support features of 802.11n
HAS_DOT11_N_SUPPORT=y


#################################################

CC := $(CROSS_COMPILE)gcc
LD := $(CROSS_COMPILE)ld

WFLAGS := -DAGGREGATION_SUPPORT -DPIGGYBACK_SUPPORT -DWMM_SUPPORT  -DLINUX -Wall -Wstrict-prototypes -Wno-trigraphs 


#################################################

#ifdef CONFIG_STA_SUPPORT
# config for STA mode

ifeq ($(RT28xx_MODE),STA)
WFLAGS += -DCONFIG_STA_SUPPORT -DDBG 

ifeq ($(HAS_WPA_SUPPLICANT),y)
WFLAGS += -DWPA_SUPPLICANT_SUPPORT
endif

ifeq ($(HAS_NATIVE_WPA_SUPPLICANT_SUPPORT),y)
WFLAGS += -DNATIVE_WPA_SUPPLICANT_SUPPORT
endif

ifeq ($(HAS_ATE),y)
WFLAGS += -DRALINK_ATE
ifeq ($(HAS_28xx_QA),y)
WFLAGS += -DRALINK_28xx_QA
endif
endif

ifeq ($(HAS_SNMP_SUPPORT),y)
WFLAGS += -DSNMP_SUPPORT
endif

ifeq ($(HAS_QOS_DLS_SUPPORT),y)
WFLAGS += -DQOS_DLS_SUPPORT
endif

ifeq ($(HAS_DOT11_N_SUPPORT),y)
WFLAGS += -DDOT11_N_SUPPORT
endif

ifeq ($(HAS_CS_SUPPORT),y)
WFLAGS += -DCARRIER_DETECTION_SUPPORT
endif

ifeq ($(HAS_SINGLE_SKU_SUPPORT),y)
WFLAGS += -DSINGLE_SKU
endif

endif
# endif of ifeq ($(RT28xx_MODE),STA)
#endif // CONFIG_STA_SUPPORT //

#################################################

#################################################

#
# Common compiler flag
#


ifeq ($(HAS_EXT_BUILD_CHANNEL_LIST),y)
WFLAGS += -DEXT_BUILD_CHANNEL_LIST
endif

ifeq ($(CHIPSET),2860)
WFLAGS +=-DRT2860
endif

ifeq ($(CHIPSET),2870)
WFLAGS +=-DRT2870
endif

ifeq ($(PLATFORM),5VT)
#WFLAGS += -DCONFIG_5VT_ENHANCE
endif

ifeq ($(HAS_BLOCK_NET_IF),y)
WFLAGS += -DBLOCK_NET_IF
endif

ifeq ($(HAS_DFS_SUPPORT),y)
WFLAGS += -DDFS_SUPPORT
endif

#ifdef MULTI_CARD
ifeq ($(HAS_MC_SUPPORT),y)
WFLAGS += -DMULTIPLE_CARD_SUPPORT
endif
#endif // MULTI_CARD //

ifeq ($(HAS_LLTD),y)
WFLAGS += -DLLTD_SUPPORT
endif

ifeq ($(PLATFORM),IXP)
WFLAGS += -DRT_BIG_ENDIAN
endif

ifeq ($(PLATFORM),IKANOS_V160)
WFLAGS += -DRT_BIG_ENDIAN -DIKANOS_VX_1X0
endif

ifeq ($(PLATFORM),IKANOS_V180)
WFLAGS += -DRT_BIG_ENDIAN -DIKANOS_VX_1X0
endif

ifeq ($(PLATFORM),INF_TWINPASS)
WFLAGS += -DRT_BIG_ENDIAN -DINF_TWINPASS
endif

ifeq ($(PLATFORM),INF_DANUBE)
WFLAGS += -DINF_DANUBE -DRT_BIG_ENDIAN
endif

ifeq ($(PLATFORM),CAVM_OCTEON)
WFLAGS += -DRT_BIG_ENDIAN
endif

ifeq ($(PLATFORM),BRCM_6358)
WFLAGS += -DRT_BIG_ENDIAN
endif

ifeq ($(PLATFORM),INF_AMAZON_SE)
#WFLAGS += -DRT_BIG_ENDIAN -DINF_AMAZON_SE -DBG_FT_SUPPORT
WFLAGS += -DRT_BIG_ENDIAN -DINF_AMAZON_SE
endif

#kernel build options for 2.4
# move to Makefile outside LINUX_SRC := /opt/star/kernel/linux-2.4.27-star

ifeq ($(PLATFORM),STAR)
CFLAGS := -D__KERNEL__ -I$(LINUX_SRC)/include -I$(RT28xx_DIR)/include -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -Uarm -fno-common -pipe -mapcs-32 -D__LINUX_ARM_ARCH__=4 -march=armv4  -mshort-load-bytes -msoft-float -Uarm -DMODULE -DMODVERSIONS -include $(LINUX_SRC)/include/linux/modversions.h $(WFLAGS)

export CFLAGS
endif

ifeq ($(PLATFORM),SIGMA)
CFLAGS := -D__KERNEL__ -I$(RT28xx_DIR)/include -I$(LINUX_SRC)/include -I$(LINUX_SRC)/include/asm/gcc -I$(LINUX_SRC)/include/asm-mips/mach-tango2 -I$(LINUX_SRC)/include/asm-mips/mach-tango2 -DEM86XX_CHIP=EM86XX_CHIPID_TANGO2 -DEM86XX_REVISION=6 -I$(LINUX_SRC)/include/asm-mips/mach-generic -I$(RT2860_DIR)/include -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -O2     -fomit-frame-pointer -G 0 -mno-abicalls -fno-pic -pipe  -mabi=32 -march=mips32r2 -Wa,-32 -Wa,-march=mips32r2 -Wa,-mips32r2 -Wa,--trap -DMODULE $(WFLAGS) 

export CFLAGS
endif

ifeq ($(PLATFORM),SIGMA_8622)
CFLAGS := -D__KERNEL__ -I$(CROSS_COMPILE_INCLUDE)/include -I$(LINUX_SRC)/include -I$(RT28xx_DIR)/include -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -fno-common -pipe -fno-builtin -D__linux__ -DNO_MM -mapcs-32 -march=armv4 -mtune=arm7tdmi -msoft-float -DMODULE -mshort-load-bytes -nostdinc -iwithprefix -DMODULE $(WFLAGS)
export CFLAGS
endif

ifeq ($(PLATFORM),5VT)
CFLAGS := -D__KERNEL__ -I$(LINUX_SRC)/include -I$(RT28xx_DIR)/include -mlittle-endian -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O3 -fno-omit-frame-pointer -fno-optimize-sibling-calls -fno-omit-frame-pointer -mapcs -mno-sched-prolog -mabi=apcs-gnu -mno-thumb-interwork -D__LINUX_ARM_ARCH__=5 -march=armv5te -mtune=arm926ej-s --param max-inline-insns-single=40000  -Uarm -Wdeclaration-after-statement -Wno-pointer-sign -DMODULE $(WFLAGS) 

export CFLAGS
endif

ifeq ($(PLATFORM),IKANOS_V160)
CFLAGS := -D__KERNEL__ -I$(LINUX_SRC)/include -I$(LINUX_SRC)/include/asm/gcc -I$(LINUX_SRC)/include/asm-mips/mach-tango2 -I$(LINUX_SRC)/include/asm-mips/mach-tango2 -I$(LINUX_SRC)/include/asm-mips/mach-generic -I$(RT28xx_DIR)/include -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -O2 -fomit-frame-pointer -G 0 -mno-abicalls -fno-pic -pipe -march=lx4189 -Wa, -DMODULE $(WFLAGS)
export CFLAGS
endif

ifeq ($(PLATFORM),IKANOS_V180)
CFLAGS := -D__KERNEL__ -I$(LINUX_SRC)/include -I$(LINUX_SRC)/include/asm/gcc -I$(LINUX_SRC)/include/asm-mips/mach-tango2 -I$(LINUX_SRC)/include/asm-mips/mach-tango2 -I$(LINUX_SRC)/include/asm-mips/mach-generic -I$(RT28xx_DIR)/include -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -O2 -fomit-frame-pointer -G 0 -mno-abicalls -fno-pic -pipe -mips32r2 -Wa, -DMODULE $(WFLAGS)
export CFLAGS
endif

ifeq ($(PLATFORM),INF_TWINPASS)
CFLAGS := -D__KERNEL__ -DMODULE -I$(LINUX_SRC)/include -I$(RT28xx_DIR)/include -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -G 0 -mno-abicalls -fno-pic -march=4kc -mips32 -Wa,--trap -pipe -mlong-calls $(WFLAGS)
export CFLAGS
endif

ifeq ($(PLATFORM),INF_DANUBE)
CFLAGS := -I$(RT28xx_DIR)/include $(WFLAGS) -Wundef -fno-strict-aliasing -fno-common -ffreestanding -Os -fomit-frame-pointer -G 0 -mno-abicalls -fno-pic -pipe -msoft-float  -mabi=32 -march=mips32 -Wa,-32 -Wa,-march=mips32 -Wa,-mips32 -Wa,--trap -I$(LINUX_SRC)/include/asm-mips/mach-generic
export CFLAGS
endif

ifeq ($(PLATFORM),BRCM_6358)
CFLAGS := $(WFLAGS) -I$(RT28xx_DIR)/include -nostdinc -iwithprefix include -D__KERNEL__ -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -I $(LINUX_SRC)/include/asm/gcc -G 0 -mno-abicalls -fno-pic -pipe  -finline-limit=100000 -mabi=32 -march=mips32 -Wa,-32 -Wa,-march=mips32 -Wa,-mips32 -Wa,--trap -I$(LINUX_SRC)/include/asm-mips/mach-bcm963xx -I$(LINUX_SRC)/include/asm-mips/mach-generic  -Os -fomit-frame-pointer -Wdeclaration-after-statement  -DMODULE -mlong-calls
export CFLAGS
endif

ifeq ($(PLATFORM),PC)
    ifneq (,$(findstring 2.4,$(LINUX_SRC)))
	# Linux 2.4
	CFLAGS := -D__KERNEL__ -I$(LINUX_SRC)/include -I$(RT28xx_DIR)/include -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -pipe -mpreferred-stack-boundary=2 -march=i686 -DMODULE -DMODVERSIONS -include $(LINUX_SRC)/include/linux/modversions.h $(WFLAGS)
	export CFLAGS
    else
	# Linux 2.6
	EXTRA_CFLAGS := $(WFLAGS) -I$(RT28xx_DIR)/include
    endif
endif

ifeq ($(PLATFORM),IXP)
        EXTRA_CFLAGS := -v $(WFLAGS) -I$(RT28xx_DIR)/include -mbig-endian
endif

ifeq ($(PLATFORM),CAVM_OCTEON)
	EXTRA_CFLAGS := $(WFLAGS) -I$(RT28xx_DIR)/include \
				    -mabi=64 $(WFLAGS)
export CFLAGS
endif
```

Then save and close the file, and continue by running these commands:

```

sudo make
sudo make install
sudo modprobe rt2870sta
```

At this point, if things go as planned, your card will be up and running within a minute.

If you get any errors, please post them.  Also, please remember to pay attention to case--in the output you posted, it looks like you typed 'cd ~/desktop' instead of 'cd ~/Desktop'.  In Linux, capitalization matters.

Sorry this is so complicated--it's tricky to install this driver without any pre-existing Internet connection (there's no way you can connect via the wire, is there?).

---

### Post by ugm6hr on 2009-02-01
@pytheas:
In case there is a problem with Network Manager - this may help:
[http://ubunturt2870.pbwiki.com/FrontPage](http://ubunturt2870.pbwiki.com/FrontPage)

---

### Post by pytheas22 on 2009-02-01
ugm6hr: thanks a lot for the link.  I didn't realize that those modifications were necessary in order for wpa_supplicant to work.  I modified my post above (#7) to address this.

---

### Post by Mister J on 2009-02-02
I'm sorry, no luck. I don't even know what I'm typing, so I can't even venture a guess as to the myriad ways I could be messing this up.

Code:
laughingmrj@ubuntu:~$ cd ~/Desktop
laughingmrj@ubuntu:~/Desktop$ sudo dpkg -i *deb
[sudo] password for laughingmrj: 
Selecting previously deselected package dpkg-dev.
(Reading database ... 99179 files and directories currently installed.)
Unpacking dpkg-dev (from dpkg-dev_1.14.20ubuntu6_all.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from g++_4.3.1-1ubuntu2_amd64.deb) ...
Preparing to replace libc6-dev 2.8~20080505-0ubuntu7 (using libc6-dev_2.8~20080505-0ubuntu7_amd64.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace make 3.81-5 (using make_3.81-5_amd64.deb) ...
Unpacking replacement make ...
dpkg: dependency problems prevent configuration of dpkg-dev:
 dpkg-dev depends on patch (>= 2.2-1); however:
  Package patch is not installed.
dpkg: error processing dpkg-dev (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of g++:
 g++ depends on g++-4.3 (>= 4.3.1-1); however:
  Package g++-4.3 is not installed.
dpkg: error processing g++ (--install):
 dependency problems - leaving unconfigured
Setting up libc6-dev (2.8~20080505-0ubuntu7) ...
Setting up make (3.81-5) ...
Processing triggers for man-db ...
Errors were encountered while processing:
 dpkg-dev
 g++
laughingmrj@ubuntu:~/Desktop$ cd ~/Desktop
laughingmrj@ubuntu:~/Desktop$ tar -xjvf 2008*
tar: 2008_0925_RT2870_Linux_STA_v1.4.0.0: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Invalid argument
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: Error exit delayed from previous errors
laughingmrj@ubuntu:~/Desktop$ cd 2008*
laughingmrj@ubuntu:~/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0$ gedit os/linux/config.mk
laughingmrj@ubuntu:~/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0$ sudo make
make -C tools
make[1]: Entering directory `/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/md5.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/mlme.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_wep.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/action.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data.o
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data.c: In function ‘RTMP_FillTxBlkInfo’:
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data.c:713: warning: label ‘FillTxBlkErr’ defined but not used
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_tkip.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_sync.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/eeprom.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_info.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/dfs.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/spectrum.o
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/spectrum.c:1598: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/assoc.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/aironet.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/auth.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sanity.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/connect.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/wpa.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.o
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.c:563: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.c:565: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.c:649: warning: assignment makes integer from pointer without a cast
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘update_os_packet_info’:
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.c:671: warning: assignment makes integer from pointer without a cast
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.c:691: warning: assignment makes integer from pointer without a cast
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.c:898: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/ba_action.o
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/ba_action.c: In function ‘convert_reordering_packet_to_preAMSDU_or_802_3_packet’:
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/ba_action.c:1511: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/2870_main_dev.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/2870_rtmp_init.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtusb_io.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtusb_bulk.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtusb_data.o
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data_2870.o
  LD [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/rt2870sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: Found 1 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/rt2870sta.mod.o
  LD [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/rt2870sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
cp -f /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/rt2870sta.ko /tftpboot
laughingmrj@ubuntu:~/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0$ sudo make install
make -C /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.27-7-generic
make[1]: Leaving directory `/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux'
laughingmrj@ubuntu:~/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0$ sudo modprobe rt2870sta
laughingmrj@ubuntu:~/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0$ 


-----------

Also, I got a red Circle with a white dash through it in the upper right, it says this when I mouse over it: An error occured, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was:'Error:BrokenCount > 0'This usually means that your installed packages have unmet dependencies.

When I search the synaptic for the broken files, these 2 popped up. "linux-wlan-ng" and "libcapi20-dev'

Thank you so much for your time. Thanks also for the tip, ugm6hr.

---

### Post by kevdog on 2009-02-02
Did you install the linux-headers and build-essential package?

sudo aptitude install linux-headers-`uname -r` build-essential

Try that and see if your errors go away or new ones are produced!

---

### Post by pytheas22 on 2009-02-02
Mister J: it actually looks like you're a lot closer.  Despite all those error messages, it appears that the driver was compiled successfully, and you were able to modprobe it without error.  This is all good.

Unfortunately, of course, your card doesn't come up as expected.  Please reboot your computer, then post the output of these commands so that we can figure out why:
```

sudo modprobe rt2870
sudo ifconfig ra0 up
dmesg | grep -e wlan -e rt -e ra0
sudo iwlist scan
modinfo rt2870
```

Don't worry about the red circle for now.  This issue is easy to fix once you have an Internet connection.

Please stick with us; I think we're very close!

Also, kevdog: Mister J doesn't have any Internet connection available at this point and his CD is not functioning as a repository for some reason, so those packages won't install.  I had him install a compiler manually instead (see post #7).  Moreover, I don't think he needs the kernel headers or build-essential anymore because it appears that the module was built successfully.  The compiler dumped a lot of warnings--I received them myself when I built the package too--but no errors.

---

### Post by Mister J on 2009-02-02
Brace yourself. From what I understand, this isn't good. 

```
laughingmrj@ubuntu:~$ sudo modprobe rt2870
[sudo] password for laughingmrj: 
FATAL: Module rt2870 not found.
laughingmrj@ubuntu:~$ sudo ifconfig ra0 up
ra0: ERROR while getting interface flags: No such device
laughingmrj@ubuntu:~$ dmesg | grep -e wlan -e rt -e ra0
[    0.000000] KERNEL supported cpus:
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Movable zone start PFN for each node
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at d4000000 (gap: d0000000:2ff00000)
[    0.004000] Checking aperture...
[    0.004000] Node 0: aperture @ 20000000 size 32 MB
[    0.004000] Aperture pointing to e820 RAM. Ignoring.
[    0.004000] Your BIOS doesn't leave a aperture memory hole
[    0.004000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.704297] Booting paravirtualized kernel on bare hardware
[    0.704392] node 0 link 0: io port [1000, ffffff]
[    0.704392] bus: 00 index 0 io port: [0, ffff]
[    0.723080] ACPI: (supports S0 S1 S3 S4 S5)
[    0.760188] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.760188] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.760238] PCI: 0000:00:11.0 reg 10 io port: [b000, b007]
[    0.760245] PCI: 0000:00:11.0 reg 14 io port: [a000, a003]
[    0.760252] PCI: 0000:00:11.0 reg 18 io port: [9000, 9007]
[    0.760259] PCI: 0000:00:11.0 reg 1c io port: [8000, 8003]
[    0.760266] PCI: 0000:00:11.0 reg 20 io port: [7000, 700f]
[    0.760507] pci 0000:00:12.2: supports D1
[    0.760508] pci 0000:00:12.2: supports D2
[    0.760510] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.760721] pci 0000:00:13.2: supports D1
[    0.760722] pci 0000:00:13.2: supports D2
[    0.760724] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.760835] PCI: 0000:00:14.1 reg 10 io port: [0, 7]
[    0.760842] PCI: 0000:00:14.1 reg 14 io port: [0, 3]
[    0.760849] PCI: 0000:00:14.1 reg 18 io port: [0, 7]
[    0.760856] PCI: 0000:00:14.1 reg 1c io port: [0, 3]
[    0.760863] PCI: 0000:00:14.1 reg 20 io port: [ff00, ff0f]
[    0.760966] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.761228] PCI: 0000:01:05.0 reg 14 io port: [c000, c0ff]
[    0.761251] pci 0000:01:05.0: supports D1
[    0.761253] pci 0000:01:05.0: supports D2
[    0.761291] pci 0000:01:05.1: supports D1
[    0.761293] pci 0000:01:05.1: supports D2
[    0.761334] PCI: bridge 0000:00:01.0 io port: [c000, cfff]
[    0.761396] PCI: 0000:02:00.0 reg 18 io port: [d800, d8ff]
[    0.761433] pci 0000:02:00.0: supports D1
[    0.761435] pci 0000:02:00.0: supports D2
[    0.761437] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.761486] PCI: bridge 0000:00:05.0 io port: [d000, dfff]
[    0.761712] PCI: 0000:04:06.0 reg 10 io port: [e800, e8ff]
[    0.761773] pci 0000:04:06.0: PME# supported from D3hot D3cold
[    0.761825] PCI: bridge 0000:00:14.4 io port: [e000, efff]
[    0.769586] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.800680] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.800680] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.824062] system 00:0b: ioport range 0x200-0x20f has been reserved
[    0.824065] system 00:0b: ioport range 0x220-0x233 has been reserved
[    0.824067] system 00:0b: ioport range 0x240-0x253 has been reserved
[    0.824069] system 00:0b: ioport range 0x260-0x273 has been reserved
[    0.824072] system 00:0b: ioport range 0x280-0x293 has been reserved
[    0.824074] system 00:0b: ioport range 0x388-0x389 has been reserved
[    0.824077] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[    0.824079] system 00:0b: ioport range 0x40b-0x40b has been reserved
[    0.824081] system 00:0b: ioport range 0x4d6-0x4d6 has been reserved
[    0.824084] system 00:0b: ioport range 0xb00-0xb0f has been reserved
[    0.824086] system 00:0b: ioport range 0xb30-0xb3f has been reserved
[    0.824089] system 00:0b: ioport range 0xc00-0xc01 has been reserved
[    0.824091] system 00:0b: ioport range 0xc14-0xc14 has been reserved
[    0.824093] system 00:0b: ioport range 0xc50-0xc51 has been reserved
[    0.824096] system 00:0b: ioport range 0xc52-0xc52 has been reserved
[    0.824098] system 00:0b: ioport range 0xc6c-0xc6c has been reserved
[    0.824100] system 00:0b: ioport range 0xc6f-0xc6f has been reserved
[    0.824103] system 00:0b: ioport range 0xcd0-0xcd1 has been reserved
[    0.824105] system 00:0b: ioport range 0xcd2-0xcd3 has been reserved
[    0.824108] system 00:0b: ioport range 0xcd4-0xcd5 has been reserved
[    0.824110] system 00:0b: ioport range 0xcd6-0xcd7 has been reserved
[    0.824113] system 00:0b: ioport range 0xcd8-0xcdf has been reserved
[    0.824116] system 00:0b: ioport range 0x800-0x89f has been reserved
[    0.824118] system 00:0b: ioport range 0xb20-0xb3f could not be reserved
[    0.824121] system 00:0b: ioport range 0x900-0x90f has been reserved
[    0.824124] system 00:0b: ioport range 0x910-0x91f has been reserved
[    0.824127] system 00:0b: ioport range 0xfe00-0xfefe has been reserved
[    0.824143] system 00:0d: ioport range 0xe00-0xe0f has been reserved
[    0.824147] system 00:0d: ioport range 0xe80-0xe8f has been reserved
[    0.824150] system 00:0d: ioport range 0xf40-0xf4f has been reserved
[    0.824152] system 00:0d: ioport range 0xa30-0xa3f has been reserved
[    0.829578] bus: 00 index 0 io port: [0, ffff]
[    0.829582] bus: 01 index 0 io port: [c000, cfff]
[    0.829590] bus: 02 index 0 io port: [d000, dfff]
[    0.829603] bus: 04 index 0 io port: [e000, efff]
[    0.829608] bus: 04 index 3 io port: [0, ffff]
[    1.868222] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    1.868248] pcieport-driver 0000:00:05.0: found MSI capability
[    1.868278] pci_express 0000:00:05.0:pcie00: allocate port service
[    1.868367] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.868392] pcieport-driver 0000:00:06.0: found MSI capability
[    1.868417] pci_express 0000:00:06.0:pcie00: allocate port service
[    1.909286] Linux agpgart interface v0.103
[    1.909291] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.912558] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.913142] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.913150] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.933885] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.933914] rtc0: alarms up to one month, y3k, hpet irqs
[    1.935004] rtc_cmos 00:05: setting system clock to 2009-02-01 22:40:19 UTC (1233528019)
[    2.122738] ACPI: Processor [P001] (supports 8 throttling states)
[    2.546934] ehci_hcd 0000:00:12.2: debug port 1
[    2.561071] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.561324] hub 1-0:1.0: 6 ports detected
[    2.833290] hub 2-0:1.0: 3 ports detected
[    2.997232] hub 3-0:1.0: 3 ports detected
[    3.200303] ehci_hcd 0000:00:13.2: debug port 1
[    3.224027] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.224170] hub 4-0:1.0: 6 ports detected
[    3.492134] hub 5-0:1.0: 3 ports detected
[    3.596311] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    3.596315] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck led clo pmp pio slum part 
[    3.597016] ata1: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ff900 irq 22
[    3.597020] ata2: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ff980 irq 22
[    3.597024] ata3: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ffa00 irq 22
[    3.597029] ata4: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ffa80 irq 22
[    5.457527] hub 4-0:1.0: unable to enumerate USB device on port 2
[    5.596164] hub 6-0:1.0: 3 ports detected
[    6.102225] hub 7-0:1.0: 2 ports detected
[    6.295902] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.296033] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.908031] hub 5-0:1.0: unable to enumerate USB device on port 2
[   18.064106] usbhid: timeout initializing reports
[   18.067539] USB Mass Storage support registered.
[   18.888382] kjournald starting.  Commit interval 5 seconds
[   23.088535] udevd version 124 started
[   23.577271] parport_pc 00:08: reported by Plug and Play ACPI
[   23.577971] parport_pc 00:08: disabled
[   38.064673] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   38.217624] ppdev: user-space parallel port driver
laughingmrj@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

laughingmrj@ubuntu:~$ modinfo rt2870
modinfo: could not find module rt2870
laughingmrj@ubuntu:~$ 
```

Thanks again for sticking with me. I'm sure you'll figure it out.

---

### Post by ugm6hr on 2009-02-02
I think it's:
```
sudo modprobe rt2870sta
```

---

### Post by pytheas22 on 2009-02-02
> I think it's:
Code:

sudo modprobe rt2870sta



Yes, that's right--stupid mistake on my part.  Mister J, please post the output of these commands:
```

sudo modprobe rt2870sta
sudo ifconfig ra0 up
sudo iwlist scan
dmesg | grep -e ra -e wlan -e rt2
modinfo rt2870sta
```

Sorry about that mistake...

---

### Post by Mister J on 2009-02-02
No worries, man. No harm done. I'm grateful just for the fact that you're taking the time to help me.

```
[sudo] password for laughingmrj: 
laughingmrj@ubuntu:~$ sudo modprobe 2870sta
FATAL: Module 2870sta not found.
laughingmrj@ubuntu:~$ sudo ifconfig ra0 up
ra0: ERROR while getting interface flags: No such device
laughingmrj@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

laughingmrj@ubuntu:~$ dmesg | grep -e ra -e wlan -e rt2
[    0.000000] No NUMA configuration found
[    0.000000] Zone PFN ranges:
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 3600.17 BogoMIPS (lpj=7200348)
[    0.004036] Security Framework initialized
[    0.011638] ACPI: Checking initramfs for custom DSDT
[    0.428028] APIC timer calibration result 12500636
[    0.004000] Calibrating delay using timer specific routine.. 3600.44 BogoMIPS (lpj=7200884)
[    0.004000] Calibrating delay using timer specific routine.. 3600.31 BogoMIPS (lpj=7200638)
[    0.004000] Calibrating delay using timer specific routine.. 3600.26 BogoMIPS (lpj=7200532)
[    0.704304] Booting paravirtualized kernel on bare hardware
[    0.704391] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.704391] PCI: Using configuration type 1 for base access
[    0.704391] PCI: Using configuration type 1 for extended access
[    0.722809] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.761812] pci 0000:00:14.4: transparent bridge
[    0.800061] NetLabel:  unlabeled traffic allowed by default
[    0.806941] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.824061] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.824065] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.824073] system 00:0b: ioport range 0x200-0x20f has been reserved
[    0.824076] system 00:0b: ioport range 0x220-0x233 has been reserved
[    0.824078] system 00:0b: ioport range 0x240-0x253 has been reserved
[    0.824080] system 00:0b: ioport range 0x260-0x273 has been reserved
[    0.824083] system 00:0b: ioport range 0x280-0x293 has been reserved
[    0.824085] system 00:0b: ioport range 0x388-0x389 has been reserved
[    0.824088] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[    0.824090] system 00:0b: ioport range 0x40b-0x40b has been reserved
[    0.824092] system 00:0b: ioport range 0x4d6-0x4d6 has been reserved
[    0.824095] system 00:0b: ioport range 0xb00-0xb0f has been reserved
[    0.824097] system 00:0b: ioport range 0xb30-0xb3f has been reserved
[    0.824099] system 00:0b: ioport range 0xc00-0xc01 has been reserved
[    0.824102] system 00:0b: ioport range 0xc14-0xc14 has been reserved
[    0.824104] system 00:0b: ioport range 0xc50-0xc51 has been reserved
[    0.824107] system 00:0b: ioport range 0xc52-0xc52 has been reserved
[    0.824109] system 00:0b: ioport range 0xc6c-0xc6c has been reserved
[    0.824112] system 00:0b: ioport range 0xc6f-0xc6f has been reserved
[    0.824114] system 00:0b: ioport range 0xcd0-0xcd1 has been reserved
[    0.824116] system 00:0b: ioport range 0xcd2-0xcd3 has been reserved
[    0.824119] system 00:0b: ioport range 0xcd4-0xcd5 has been reserved
[    0.824121] system 00:0b: ioport range 0xcd6-0xcd7 has been reserved
[    0.824124] system 00:0b: ioport range 0xcd8-0xcdf has been reserved
[    0.824126] system 00:0b: ioport range 0x800-0x89f has been reserved
[    0.824129] system 00:0b: ioport range 0xb20-0xb3f could not be reserved
[    0.824132] system 00:0b: ioport range 0x900-0x90f has been reserved
[    0.824135] system 00:0b: ioport range 0x910-0x91f has been reserved
[    0.824138] system 00:0b: ioport range 0xfe00-0xfefe has been reserved
[    0.824141] system 00:0b: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.824144] system 00:0b: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.824154] system 00:0d: ioport range 0xe00-0xe0f has been reserved
[    0.824159] system 00:0d: ioport range 0xe80-0xe8f has been reserved
[    0.824161] system 00:0d: ioport range 0xf40-0xf4f has been reserved
[    0.824164] system 00:0d: ioport range 0xa30-0xa3f has been reserved
[    0.824172] system 00:10: iomem range 0xe0000000-0xefffffff has been reserved
[    0.824179] system 00:11: iomem range 0x0-0x9ffff could not be reserved
[    0.824181] system 00:11: iomem range 0xc0000-0xcffff has been reserved
[    0.824184] system 00:11: iomem range 0xe0000-0xfffff could not be reserved
[    0.824188] system 00:11: iomem range 0x100000-0xcfffffff could not be reserved
[    0.824190] system 00:11: iomem range 0xfed45000-0xffffffff could not be reserved
[    0.888287] checking if image is initramfs... it is
[    1.958424] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.436353] usb usb1: configuration #1 chosen from 1 choice
[    2.768332] usb usb2: configuration #1 chosen from 1 choice
[    2.924305] usb 1-3: configuration #1 chosen from 1 choice
[    3.225690] usb 1-5: configuration #1 chosen from 1 choice
[    4.972126] usb usb3: configuration #1 chosen from 1 choice
[    5.024030] hub 2-0:1.0: unable to enumerate USB device on port 2
[    5.132116] usb usb4: configuration #1 chosen from 1 choice
[    5.318167] usb 2-3: configuration #1 chosen from 1 choice
[    5.397401] usb usb5: configuration #1 chosen from 1 choice
[    5.668952] usb usb6: configuration #1 chosen from 1 choice
[    5.750049] usb 4-1: configuration #1 chosen from 1 choice
[    6.172730] usb usb7: configuration #1 chosen from 1 choice
[    6.616473] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    7.785529] hub 5-0:1.0: unable to enumerate USB device on port 2
[    7.792824] Initializing USB Mass Storage driver...
[    7.793041] scsi6 : SCSI emulation for USB Mass Storage devices
[    7.793158] usb-storage: device found at 4
[    7.793162] usb-storage: waiting for device to settle before scanning
[   12.788168] usb-storage: device scan complete
[   17.788331] hiddev96hidraw0: USB HID v1.11 Device [Generic USB2.0-CRW] on usb-0000:00:13.2-3
[   17.788468] scsi7 : SCSI emulation for USB Mass Storage devices
[   17.788595] usb-storage: device found at 6
[   17.788599] usb-storage: waiting for device to settle before scanning
[   17.813654] input,hidraw1: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:12.1-1
[   17.814925] usbcore: registered new interface driver usb-storage
[   17.814940] USB Mass Storage support registered.
[   22.817713] usb-storage: device scan complete
[   41.958016] type=1505 audit(1233612409.842:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4934
[   42.134832] type=1505 audit(1233612410.018:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4939
[   42.135151] type=1505 audit(1233612410.018:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4939
[   44.073821] ppdev: user-space parallel port driver
[  144.292623] type=1503 audit(1233612512.177:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6496/net/" pid=6496 profile="/usr/sbin/cupsd"
[  144.387167] type=1503 audit(1233612512.269:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6496 profile="/usr/sbin/cupsd"
[  144.387184] type=1503 audit(1233612512.269:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6496 profile="/usr/sbin/cupsd"
[  144.387197] type=1503 audit(1233612512.269:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6496 profile="/usr/sbin/cupsd"
[  144.387208] type=1503 audit(1233612512.269:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6496 profile="/usr/sbin/cupsd"
[  144.387218] type=1503 audit(1233612512.269:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6496 profile="/usr/sbin/cupsd"
[  144.387230] type=1503 audit(1233612512.269:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6496 profile="/usr/sbin/cupsd"
[  144.387241] type=1503 audit(1233612512.269:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6496 profile="/usr/sbin/cupsd"
[  144.387254] type=1503 audit(1233612512.269:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6496 profile="/usr/sbin/cupsd"
[  144.387392] type=1503 audit(1233612512.269:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/6496/net/dev" pid=6496 profile="/usr/sbin/cupsd"
[  248.004209] usbcore: registered new interface driver rt2870
laughingmrj@ubuntu:~$ modinfo rt2870sta
filename:       /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/rt2870sta.ko
version:        1.4.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     E00168480A46C5501E5B1FD
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        usbcore
vermagic:       2.6.27-7-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)
laughingmrj@ubuntu:~$ 

```

Edit: Crap, I forgot to write "rt2870sta"

---

### Post by ugm6hr on 2009-02-02
Minor spelling error there...
> laughingmrj@ubuntu:~$ sudo modprobe 2870sta

It's **rt2870sta**

---

### Post by Mister J on 2009-02-02
Thanks. I just realized that. Oddly enough, still no change. Is it supposed to do something when I type in the first command?


```
laughingmrj@ubuntu:~$ sudo modprobe rt2870sta
laughingmrj@ubuntu:~$ sudo ifconfig ra0 up
ra0: ERROR while getting interface flags: No such device
laughingmrj@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

laughingmrj@ubuntu:~$ dmesg | grep -e ra -e wlan -e rt2
[    0.000000] No NUMA configuration found
[    0.000000] Zone PFN ranges:
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 3600.13 BogoMIPS (lpj=7200272)
[    0.004035] Security Framework initialized
[    0.011627] ACPI: Checking initramfs for custom DSDT
[    0.428028] APIC timer calibration result 12500490
[    0.004000] Calibrating delay using timer specific routine.. 3600.35 BogoMIPS (lpj=7200703)
[    0.004000] Calibrating delay using timer specific routine.. 3600.23 BogoMIPS (lpj=7200476)
[    0.004000] Calibrating delay using timer specific routine.. 3600.24 BogoMIPS (lpj=7200497)
[    0.704303] Booting paravirtualized kernel on bare hardware
[    0.704392] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.704392] PCI: Using configuration type 1 for base access
[    0.704392] PCI: Using configuration type 1 for extended access
[    0.723168] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.761821] pci 0000:00:14.4: transparent bridge
[    0.800060] NetLabel:  unlabeled traffic allowed by default
[    0.806873] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.824050] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.824053] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.824061] system 00:0b: ioport range 0x200-0x20f has been reserved
[    0.824064] system 00:0b: ioport range 0x220-0x233 has been reserved
[    0.824067] system 00:0b: ioport range 0x240-0x253 has been reserved
[    0.824069] system 00:0b: ioport range 0x260-0x273 has been reserved
[    0.824071] system 00:0b: ioport range 0x280-0x293 has been reserved
[    0.824074] system 00:0b: ioport range 0x388-0x389 has been reserved
[    0.824076] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[    0.824079] system 00:0b: ioport range 0x40b-0x40b has been reserved
[    0.824081] system 00:0b: ioport range 0x4d6-0x4d6 has been reserved
[    0.824084] system 00:0b: ioport range 0xb00-0xb0f has been reserved
[    0.824086] system 00:0b: ioport range 0xb30-0xb3f has been reserved
[    0.824088] system 00:0b: ioport range 0xc00-0xc01 has been reserved
[    0.824091] system 00:0b: ioport range 0xc14-0xc14 has been reserved
[    0.824093] system 00:0b: ioport range 0xc50-0xc51 has been reserved
[    0.824096] system 00:0b: ioport range 0xc52-0xc52 has been reserved
[    0.824098] system 00:0b: ioport range 0xc6c-0xc6c has been reserved
[    0.824101] system 00:0b: ioport range 0xc6f-0xc6f has been reserved
[    0.824103] system 00:0b: ioport range 0xcd0-0xcd1 has been reserved
[    0.824105] system 00:0b: ioport range 0xcd2-0xcd3 has been reserved
[    0.824108] system 00:0b: ioport range 0xcd4-0xcd5 has been reserved
[    0.824110] system 00:0b: ioport range 0xcd6-0xcd7 has been reserved
[    0.824113] system 00:0b: ioport range 0xcd8-0xcdf has been reserved
[    0.824115] system 00:0b: ioport range 0x800-0x89f has been reserved
[    0.824118] system 00:0b: ioport range 0xb20-0xb3f could not be reserved
[    0.824121] system 00:0b: ioport range 0x900-0x90f has been reserved
[    0.824123] system 00:0b: ioport range 0x910-0x91f has been reserved
[    0.824126] system 00:0b: ioport range 0xfe00-0xfefe has been reserved
[    0.824129] system 00:0b: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.824132] system 00:0b: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.824143] system 00:0d: ioport range 0xe00-0xe0f has been reserved
[    0.824148] system 00:0d: ioport range 0xe80-0xe8f has been reserved
[    0.824150] system 00:0d: ioport range 0xf40-0xf4f has been reserved
[    0.824153] system 00:0d: ioport range 0xa30-0xa3f has been reserved
[    0.824162] system 00:10: iomem range 0xe0000000-0xefffffff has been reserved
[    0.824168] system 00:11: iomem range 0x0-0x9ffff could not be reserved
[    0.824171] system 00:11: iomem range 0xc0000-0xcffff has been reserved
[    0.824173] system 00:11: iomem range 0xe0000-0xfffff could not be reserved
[    0.824178] system 00:11: iomem range 0x100000-0xcfffffff could not be reserved
[    0.824181] system 00:11: iomem range 0xfed45000-0xffffffff could not be reserved
[    0.888268] checking if image is initramfs... it is
[    1.958519] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.457842] usb usb1: configuration #1 chosen from 1 choice
[    2.725723] usb usb2: configuration #1 chosen from 1 choice
[    2.992905] usb usb3: configuration #1 chosen from 1 choice
[    3.016621] usb 1-3: configuration #1 chosen from 1 choice
[    3.256107] usb usb4: configuration #1 chosen from 1 choice
[    3.329610] usb 2-1: configuration #1 chosen from 1 choice
[    3.633306] usb 2-2: configuration #1 chosen from 1 choice
[    5.417645] usb usb5: configuration #1 chosen from 1 choice
[    5.637635] usb usb6: configuration #1 chosen from 1 choice
[    5.656028] hub 3-0:1.0: unable to enumerate USB device on port 2
[    5.904981] usb usb7: configuration #1 chosen from 1 choice
[    6.572945] usb 5-3: configuration #1 chosen from 1 choice
[    6.692064] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.877061] usb 5-5: configuration #1 chosen from 1 choice
[    8.676026] hub 6-0:1.0: unable to enumerate USB device on port 2
[    8.968079] usb 6-3: configuration #1 chosen from 1 choice
[    8.978704] Initializing USB Mass Storage driver...
[    9.397455] usb 2-1: configuration #1 chosen from 1 choice
[   11.548022] hub 3-0:1.0: unable to enumerate USB device on port 2
[   11.676190] scsi6 : SCSI emulation for USB Mass Storage devices
[   11.677679] usb-storage: device found at 4
[   11.677682] usb-storage: waiting for device to settle before scanning
[   16.676160] usb-storage: device scan complete
[   21.680202] hiddev96hidraw0: USB HID v1.11 Device [Generic USB2.0-CRW] on usb-0000:00:13.2-3
[   21.680347] scsi7 : SCSI emulation for USB Mass Storage devices
[   21.680475] usb-storage: device found at 6
[   21.680480] usb-storage: waiting for device to settle before scanning
[   21.705648] input,hidraw1: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:12.1-1
[   21.706939] usbcore: registered new interface driver usb-storage
[   21.706952] USB Mass Storage support registered.
[   26.684235] usb-storage: device scan complete
[   46.691893] type=1505 audit(1233613455.053:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4956
[   46.869102] type=1505 audit(1233613455.234:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4961
[   46.869416] type=1505 audit(1233613455.234:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4961
[   48.574548] ppdev: user-space parallel port driver
[  143.977949] type=1503 audit(1233613552.341:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6464/net/" pid=6464 profile="/usr/sbin/cupsd"
[  144.073218] type=1503 audit(1233613552.437:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6464 profile="/usr/sbin/cupsd"
[  144.073236] type=1503 audit(1233613552.437:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6464 profile="/usr/sbin/cupsd"
[  144.073247] type=1503 audit(1233613552.437:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6464 profile="/usr/sbin/cupsd"
[  144.073260] type=1503 audit(1233613552.437:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6464 profile="/usr/sbin/cupsd"
[  144.073270] type=1503 audit(1233613552.437:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6464 profile="/usr/sbin/cupsd"
[  144.073282] type=1503 audit(1233613552.437:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6464 profile="/usr/sbin/cupsd"
[  144.073293] type=1503 audit(1233613552.437:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6464 profile="/usr/sbin/cupsd"
[  144.073305] type=1503 audit(1233613552.437:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6464 profile="/usr/sbin/cupsd"
[  144.073461] type=1503 audit(1233613552.437:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/6464/net/dev" pid=6464 profile="/usr/sbin/cupsd"
[  161.651468] usbcore: registered new interface driver rt2870
laughingmrj@ubuntu:~$ modinfo rt2870sta
filename:       /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/rt2870sta.ko
version:        1.4.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     E00168480A46C5501E5B1FD
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        usbcore
vermagic:       2.6.27-7-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)
laughingmrj@ubuntu:~$ 


```

---

### Post by pytheas22 on 2009-02-02
Strange, it doesn't look like the kernel is seeing the driver at all when you try to load it.  What is the output of:
```

sudo modprobe rt2870sta
lsmod | grep rt
lsusb
iwconfig
dmesg
```

That last command will produce a lot of output, but please post it all...hopefully the answer as to why this isn't working as intended will be in there.

---

### Post by Mister J on 2009-02-02
Okay, the last command gave out so much text the top started cutting off. I ran it again in a new terminal window, to get as much as possible.

```
laughingmrj@ubuntu:~$ sudo modprobe rt2870sta
laughingmrj@ubuntu:~$ lsmod | grep rt
rt2870sta             567400  0 
parport_pc             44200  0 
parport                50096  3 ppdev,lp,parport_pc
usbcore               175376  7 rt2870sta,usb_storage,usbhid,libusual,ehci_hcd,ohci_hcd
laughingmrj@ubuntu:~$ lsusb
Bus 006 Device 006: ID 0a48:3302 I/O Interconnect 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 004: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 005 Device 002: ID 1737:0070 Linksys 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0461:4d16 Primax Electronics, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
laughingmrj@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

laughingmrj@ubuntu:~$ 

```

This is where I typed in the final command, and all that was in the terminal. 

```
[    0.769616] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.769616] pnp: PnP ACPI init
[    0.769616] ACPI: bus type pnp registered
[    0.780324] pnp: PnP ACPI: found 18 devices
[    0.780326] ACPI: ACPI bus type pnp unregistered
[    0.780347] PCI: Using ACPI for IRQ routing
[    0.800043] NET: Registered protocol family 8
[    0.800045] NET: Registered protocol family 20
[    0.800061] NetLabel: Initializing
[    0.800061] NetLabel:  domain hash size = 128
[    0.800061] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.800061] NetLabel:  unlabeled traffic allowed by default
[    0.800164] PCI-DMA: Disabling AGP.
[    0.800690] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.800690] PCI-DMA: using GART IOMMU.
[    0.800690] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.801720] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.801727] hpet0: 4 32-bit timers, 14318180 Hz
[    0.804048] Switched to high resolution mode on CPU 0
[    0.804444] Switched to high resolution mode on CPU 3
[    0.804497] Switched to high resolution mode on CPU 2
[    0.804542] Switched to high resolution mode on CPU 1
[    0.806925] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.806928]    actual entries 65586
[    0.807044] AppArmor: AppArmor Filesystem Enabled
[    0.807071] ACPI: RTC can wake from S4
[    0.824061] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.824065] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.824073] system 00:0b: ioport range 0x200-0x20f has been reserved
[    0.824076] system 00:0b: ioport range 0x220-0x233 has been reserved
[    0.824078] system 00:0b: ioport range 0x240-0x253 has been reserved
[    0.824081] system 00:0b: ioport range 0x260-0x273 has been reserved
[    0.824083] system 00:0b: ioport range 0x280-0x293 has been reserved
[    0.824085] system 00:0b: ioport range 0x388-0x389 has been reserved
[    0.824088] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[    0.824090] system 00:0b: ioport range 0x40b-0x40b has been reserved
[    0.824093] system 00:0b: ioport range 0x4d6-0x4d6 has been reserved
[    0.824095] system 00:0b: ioport range 0xb00-0xb0f has been reserved
[    0.824097] system 00:0b: ioport range 0xb30-0xb3f has been reserved
[    0.824100] system 00:0b: ioport range 0xc00-0xc01 has been reserved
[    0.824102] system 00:0b: ioport range 0xc14-0xc14 has been reserved
[    0.824105] system 00:0b: ioport range 0xc50-0xc51 has been reserved
[    0.824107] system 00:0b: ioport range 0xc52-0xc52 has been reserved
[    0.824109] system 00:0b: ioport range 0xc6c-0xc6c has been reserved
[    0.824112] system 00:0b: ioport range 0xc6f-0xc6f has been reserved
[    0.824114] system 00:0b: ioport range 0xcd0-0xcd1 has been reserved
[    0.824117] system 00:0b: ioport range 0xcd2-0xcd3 has been reserved
[    0.824119] system 00:0b: ioport range 0xcd4-0xcd5 has been reserved
[    0.824122] system 00:0b: ioport range 0xcd6-0xcd7 has been reserved
[    0.824124] system 00:0b: ioport range 0xcd8-0xcdf has been reserved
[    0.824127] system 00:0b: ioport range 0x800-0x89f has been reserved
[    0.824130] system 00:0b: ioport range 0xb20-0xb3f could not be reserved
[    0.824132] system 00:0b: ioport range 0x900-0x90f has been reserved
[    0.824135] system 00:0b: ioport range 0x910-0x91f has been reserved
[    0.824138] system 00:0b: ioport range 0xfe00-0xfefe has been reserved
[    0.824141] system 00:0b: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.824144] system 00:0b: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.824154] system 00:0d: ioport range 0xe00-0xe0f has been reserved
[    0.824159] system 00:0d: ioport range 0xe80-0xe8f has been reserved
[    0.824162] system 00:0d: ioport range 0xf40-0xf4f has been reserved
[    0.824164] system 00:0d: ioport range 0xa30-0xa3f has been reserved
[    0.824174] system 00:10: iomem range 0xe0000000-0xefffffff has been reserved
[    0.824181] system 00:11: iomem range 0x0-0x9ffff could not be reserved
[    0.824183] system 00:11: iomem range 0xc0000-0xcffff has been reserved
[    0.824186] system 00:11: iomem range 0xe0000-0xfffff could not be reserved
[    0.824190] system 00:11: iomem range 0x100000-0xcfffffff could not be reserved
[    0.824192] system 00:11: iomem range 0xfed45000-0xffffffff could not be reserved
[    0.829487] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.829490] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.829494] pci 0000:00:01.0:   MEM window: 0xfe800000-0xfe9fffff
[    0.829498] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.829503] pci 0000:00:05.0: PCI bridge, secondary bus 0000:02
[    0.829505] pci 0000:00:05.0:   IO window: 0xd000-0xdfff
[    0.829509] pci 0000:00:05.0:   MEM window: 0xfea00000-0xfeafffff
[    0.829512] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.829516] pci 0000:00:06.0: PCI bridge, secondary bus 0000:03
[    0.829517] pci 0000:00:06.0:   IO window: disabled
[    0.829521] pci 0000:00:06.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.829523] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.829527] pci 0000:00:14.4: PCI bridge, secondary bus 0000:04
[    0.829530] pci 0000:00:14.4:   IO window: 0xe000-0xefff
[    0.829536] pci 0000:00:14.4:   MEM window: disabled
[    0.829540] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.829565] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.829568] pci 0000:00:05.0: setting latency timer to 64
[    0.829576] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.829579] pci 0000:00:06.0: setting latency timer to 64
[    0.829587] bus: 00 index 0 io port: [0, ffff]
[    0.829590] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.829592] bus: 01 index 0 io port: [c000, cfff]
[    0.829594] bus: 01 index 1 mmio: [fe800000, fe9fffff]
[    0.829596] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.829597] bus: 01 index 3 mmio: [0, 0]
[    0.829599] bus: 02 index 0 io port: [d000, dfff]
[    0.829601] bus: 02 index 1 mmio: [fea00000, feafffff]
[    0.829603] bus: 02 index 2 mmio: [0, 0]
[    0.829604] bus: 02 index 3 mmio: [0, 0]
[    0.829606] bus: 03 index 0 mmio: [0, 0]
[    0.829607] bus: 03 index 1 mmio: [feb00000, febfffff]
[    0.829609] bus: 03 index 2 mmio: [0, 0]
[    0.829611] bus: 03 index 3 mmio: [0, 0]
[    0.829612] bus: 04 index 0 io port: [e000, efff]
[    0.829614] bus: 04 index 1 mmio: [0, 0]
[    0.829616] bus: 04 index 2 mmio: [0, 0]
[    0.829617] bus: 04 index 3 io port: [0, ffff]
[    0.829619] bus: 04 index 4 mmio: [0, ffffffffffffffff]
[    0.829633] NET: Registered protocol family 2
[    0.868213] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.869971] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.873994] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.874495] TCP: Hash tables configured (established 524288 bind 65536)
[    0.874498] TCP reno registered
[    0.884127] NET: Registered protocol family 1
[    0.884274] checking if image is initramfs... it is
[    1.650531] Freeing initrd memory: 8697k freed
[    1.656362] audit: initializing netlink socket (disabled)
[    1.656377] type=2000 audit(1233587221.656:1): initialized
[    1.662434] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.665471] VFS: Disk quotas dquot_6.5.1
[    1.665572] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.665682] msgmni has been set to 7415
[    1.665820] io scheduler noop registered
[    1.665822] io scheduler anticipatory registered
[    1.665824] io scheduler deadline registered
[    1.665957] io scheduler cfq registered (default)
[    1.868048] pci 0000:01:05.0: Boot video device
[    1.868219] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    1.868245] pcieport-driver 0000:00:05.0: found MSI capability
[    1.868275] pci_express 0000:00:05.0:pcie00: allocate port service
[    1.868364] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.868389] pcieport-driver 0000:00:06.0: found MSI capability
[    1.868414] pci_express 0000:00:06.0:pcie00: allocate port service
[    1.909102] hpet_resources: 0xfed00000 is busy
[    1.909236] Linux agpgart interface v0.103
[    1.909242] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.912446] brd: module loaded
[    1.912534] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.912672] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PSMS] at 0x60,0x64 irq 1,12
[    1.913116] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.913124] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.941664] mice: PS/2 mouse device common for all mice
[    1.941833] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.941861] rtc0: alarms up to one month, y3k, hpet irqs
[    1.941914] cpuidle: using governor ladder
[    1.941916] cpuidle: using governor menu
[    1.942365] TCP cubic registered
[    1.942632] registered taskstats version 1
[    1.942823]   Magic number: 13:777:132
[    1.942928] acpi PNP0C02:04: hash matches
[    1.942936] acpi device:07: hash matches
[    1.942973] rtc_cmos 00:05: setting system clock to 2009-02-02 15:07:03 UTC (1233587223)
[    1.942976] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.942978] EDD information not available.
[    1.943024] Freeing unused kernel memory: 536k freed
[    1.943262] Write protecting the kernel read-only data: 4348k
[    1.963903] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.097086] fuse init (API version 7.9)
[    2.124518] processor ACPI0007:00: registered as cooling_device0
[    2.124523] ACPI: Processor [P001] (supports 8 throttling states)
[    2.124599] processor ACPI0007:01: registered as cooling_device1
[    2.124669] processor ACPI0007:02: registered as cooling_device2
[    2.124746] processor ACPI0007:03: registered as cooling_device3
[    2.351304] usbcore: registered new interface driver usbfs
[    2.351370] usbcore: registered new interface driver hub
[    2.351512] No dock devices found.
[    2.354059] usbcore: registered new device driver usb
[    2.354307] sky2 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.354325] sky2 0000:02:00.0: setting latency timer to 64
[    2.354360] sky2 0000:02:00.0: v1.22 addr 0xfeafc000 irq 17 Yukon-2 Extreme rev 2
[    2.355221] sky2 eth0: addr 00:22:68:3a:a3:4f
[    2.356834] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.356897] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.356917] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    2.356991] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
[    2.357049] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe7fe000
[    2.371631] SCSI subsystem initialized
[    2.386957] libata version 3.00 loaded.
[    2.416336] usb usb1: configuration #1 chosen from 1 choice
[    2.416367] hub 1-0:1.0: USB hub found
[    2.416390] hub 1-0:1.0: 3 ports detected
[    2.624540] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.624563] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    2.624595] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 2
[    2.624618] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe7fd000
[    2.684429] usb usb2: configuration #1 chosen from 1 choice
[    2.684463] hub 2-0:1.0: USB hub found
[    2.684477] hub 2-0:1.0: 3 ports detected
[    2.760159] usb 1-3: new full speed USB device using ohci_hcd and address 2
[    2.892636] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.892658] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.892695] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 3
[    2.892732] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe7fc000
[    2.952191] usb usb3: configuration #1 chosen from 1 choice
[    2.952222] hub 3-0:1.0: USB hub found
[    2.952234] hub 3-0:1.0: 3 ports detected
[    2.960189] usb 1-3: configuration #1 chosen from 1 choice
[    3.108024] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    3.157391] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.157410] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.157445] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 4
[    3.157466] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe7fb000
[    3.216111] usb usb4: configuration #1 chosen from 1 choice
[    3.216139] hub 4-0:1.0: USB hub found
[    3.216149] hub 4-0:1.0: 3 ports detected
[    3.273244] usb 2-1: configuration #1 chosen from 1 choice
[    3.320175] ahci 0000:00:11.0: version 3.0
[    3.320195] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.320306] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    3.320310] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck led clo pmp pio slum part 
[    3.320600] scsi0 : ahci
[    3.320724] scsi1 : ahci
[    3.320792] scsi2 : ahci
[    3.320862] scsi3 : ahci
[    3.320968] ata1: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ff900 irq 22
[    3.320972] ata2: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ff980 irq 22
[    3.320975] ata3: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ffa00 irq 22
[    3.320979] ata4: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ffa80 irq 22
[    3.408024] usb 2-2: new full speed USB device using ohci_hcd and address 3
[    3.577220] usb 2-2: configuration #1 chosen from 1 choice
[    3.712023] usb 3-2: new full speed USB device using ohci_hcd and address 2
[    3.804030] ata1: softreset failed (device not ready)
[    3.804036] ata1: failed due to HW bug, retry pmp=0
[    3.852015] usb 3-2: device descriptor read/64, error 18
[    3.968036] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.968856] ata1.00: ATA-8: WDC WD6400AAKS-22A7B2, 01.03B01, max UDMA/133
[    3.968859] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.969765] ata1.00: configured for UDMA/133
[    4.096022] usb 3-2: device descriptor read/64, error 18
[    4.336011] usb 3-2: new full speed USB device using ohci_hcd and address 3
[    4.452011] ata2: softreset failed (device not ready)
[    4.452015] ata2: failed due to HW bug, retry pmp=0
[    4.476011] usb 3-2: device descriptor read/64, error 18
[    4.616072] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.618630] ata2.00: ATAPI: HL-DT-ST DVDRAM GH15F, EG00, max UDMA/100
[    4.622415] ata2.00: configured for UDMA/100
[    4.720027] usb 3-2: device descriptor read/64, error 18
[    4.940040] ata3: SATA link down (SStatus 0 SControl 300)
[    4.960020] usb 3-2: new full speed USB device using ohci_hcd and address 4
[    4.984997] usb 3-2: device descriptor read/8, error -71
[    5.108992] usb 3-2: device descriptor read/8, error -71
[    5.264036] ata4: SATA link down (SStatus 0 SControl 300)
[    5.264162] scsi 0:0:0:0: Direct-Access     ATA      WDC WD6400AAKS-2 01.0 PQ: 0 ANSI: 5
[    5.267194] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH15F     EG00 PQ: 0 ANSI: 5
[    5.267365] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.267380] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    5.267412] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 5
[    5.267453] ehci_hcd 0000:00:12.2: debug port 1
[    5.267473] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe7ff000
[    5.349524] usb 3-2: new full speed USB device using ohci_hcd and address 5
[    5.360065] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.360173] usb usb5: configuration #1 chosen from 1 choice
[    5.360202] hub 5-0:1.0: USB hub found
[    5.360209] hub 5-0:1.0: 6 ports detected
[    5.372983] usb 3-2: device descriptor read/8, error -71
[    5.496981] usb 3-2: device descriptor read/8, error -71
[    5.569808] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    5.569821] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    5.569866] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 6
[    5.569901] ehci_hcd 0000:00:13.2: debug port 1
[    5.569918] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe7fa800
[    5.580025] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.580126] usb usb6: configuration #1 chosen from 1 choice
[    5.580153] hub 6-0:1.0: USB hub found
[    5.580160] hub 6-0:1.0: 6 ports detected
[    5.600022] hub 3-0:1.0: unable to enumerate USB device on port 2
[    5.728036] usb 1-3: USB disconnect, address 2
[    5.789940] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.789952] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    5.789986] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    5.790005] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe7f9000
[    5.848140] usb usb7: configuration #1 chosen from 1 choice
[    5.848168] hub 7-0:1.0: USB hub found
[    5.848178] hub 7-0:1.0: 2 ports detected
[    5.856032] usb 2-1: USB disconnect, address 2
[    5.954116] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.954156] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    5.954252] scsi4 : pata_atiixp
[    5.956270] scsi5 : pata_atiixp
[    5.958120] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    5.958123] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    5.985526] usb 2-2: USB disconnect, address 3
[    6.297600] ohci1394 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    6.297614] ohci1394 0000:03:00.0: setting latency timer to 64
[    6.349440] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    6.360059] usb 5-3: new high speed USB device using ehci_hcd and address 2
[    6.371370] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    6.371644] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    6.404430] Driver 'sd' needs updating - please use bus_type methods
[    6.404675] sd 0:0:0:0: [sda] 1250263728 512-byte hardware sectors (640135 MB)
[    6.404693] sd 0:0:0:0: [sda] Write Protect is off
[    6.404696] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.404722] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.404821] sd 0:0:0:0: [sda] 1250263728 512-byte hardware sectors (640135 MB)
[    6.404835] sd 0:0:0:0: [sda] Write Protect is off
[    6.404837] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.404860] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.404864]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    6.415947]  sda1 sda2
[    6.416150] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.519813] usb 5-3: configuration #1 chosen from 1 choice
[    6.634416] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.634423] Uniform CD-ROM driver Revision: 3.20
[    6.634538] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.688034] usb 5-5: new high speed USB device using ehci_hcd and address 4
[    6.821754] usb 5-5: configuration #1 chosen from 1 choice
[    6.932028] usb 6-2: new high speed USB device using ehci_hcd and address 2
[    7.044019] usb 6-2: device descriptor read/64, error 18
[    7.260023] usb 6-2: device descriptor read/64, error 18
[    7.476025] usb 6-2: new high speed USB device using ehci_hcd and address 3
[    7.588023] usb 6-2: device descriptor read/64, error 18
[    7.628207] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0099973900016c20]
[    7.804024] usb 6-2: device descriptor read/64, error 18
[    8.020029] usb 6-2: new high speed USB device using ehci_hcd and address 4
[    8.041141] usb 6-2: device descriptor read/8, error -71
[    8.160372] usb 6-2: device descriptor read/8, error -71
[    8.376024] usb 6-2: new high speed USB device using ehci_hcd and address 5
[    8.397080] usb 6-2: device descriptor read/8, error -71
[    8.516435] usb 6-2: device descriptor read/8, error -71
[    8.620026] hub 6-0:1.0: unable to enumerate USB device on port 2
[    8.744023] usb 6-3: new high speed USB device using ehci_hcd and address 6
[    8.912756] usb 6-3: configuration #1 chosen from 1 choice
[    8.915991] usbcore: registered new interface driver hiddev
[    8.916000] usbcore: registered new interface driver libusual
[    8.923391] Initializing USB Mass Storage driver...
[    9.176025] usb 2-1: new low speed USB device using ohci_hcd and address 4
[    9.341071] usb 2-1: configuration #1 chosen from 1 choice
[    9.604022] usb 3-2: new full speed USB device using ohci_hcd and address 6
[    9.744021] usb 3-2: device descriptor read/64, error 18
[    9.988021] usb 3-2: device descriptor read/64, error 18
[   10.228021] usb 3-2: new full speed USB device using ohci_hcd and address 7
[   10.368021] usb 3-2: device descriptor read/64, error 18
[   10.612021] usb 3-2: device descriptor read/64, error 18
[   10.852021] usb 3-2: new full speed USB device using ohci_hcd and address 8
[   10.876787] usb 3-2: device descriptor read/8, error -71
[   11.000789] usb 3-2: device descriptor read/8, error -71
[   11.240021] usb 3-2: new full speed USB device using ohci_hcd and address 9
[   11.264778] usb 3-2: device descriptor read/8, error -71
[   11.388768] usb 3-2: device descriptor read/8, error -71
[   11.492023] hub 3-0:1.0: unable to enumerate USB device on port 2
[   11.620193] scsi6 : SCSI emulation for USB Mass Storage devices
[   11.621717] usb-storage: device found at 4
[   11.621720] usb-storage: waiting for device to settle before scanning
[   16.620107] usb-storage: device scan complete
[   16.620596] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0 CCS
[   16.621448] sd 6:0:0:0: [sdb] 15682559 512-byte hardware sectors (8029 MB)
[   16.621951] sd 6:0:0:0: [sdb] Write Protect is off
[   16.621955] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
[   16.621958] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   16.623068] sd 6:0:0:0: [sdb] 15682559 512-byte hardware sectors (8029 MB)
[   16.623565] sd 6:0:0:0: [sdb] Write Protect is off
[   16.623568] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
[   16.623570] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   16.623573]  sdb: sdb1
[   16.624382] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   16.624501] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   21.624088] usbhid: timeout initializing reports
[   21.624266] hiddev96hidraw0: USB HID v1.11 Device [Generic USB2.0-CRW] on usb-0000:00:13.2-3
[   21.624391] scsi7 : SCSI emulation for USB Mass Storage devices
[   21.624504] usb-storage: device found at 6
[   21.624508] usb-storage: waiting for device to settle before scanning
[   21.631921] input: USB Optical Mouse as /devices/pci0000:00/0000:00:12.1/usb2/2-1/2-1:1.0/input/input2
[   21.649650] input,hidraw1: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:12.1-1
[   21.650856] usbcore: registered new interface driver usbhid
[   21.650862] usbhid: v2.6:USB HID core driver
[   21.650925] usbcore: registered new interface driver usb-storage
[   21.650937] USB Mass Storage support registered.
[   22.441163] loop: module loaded
[   22.477024] kjournald starting.  Commit interval 5 seconds
[   22.477035] EXT3-fs: mounted filesystem with ordered data mode.
[   26.013312] udevd version 124 started
[   26.319518] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.353744] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   26.373533] ACPI: Power Button (FF) [PWRF]
[   26.373685] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   26.386124] shpchp: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[   26.386131] shpchp: shpc_init: cannot reserve MMIO region
[   26.386190] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.405551] ACPI: Power Button (CM) [PWRB]
[   26.507202] parport_pc 00:08: reported by Plug and Play ACPI
[   26.507923] parport_pc 00:08: disabled
[   26.624302] usb-storage: device scan complete
[   26.629333] scsi 7:0:0:0: Direct-Access     IOI CF/M icroDrive Disk.. 1.09 PQ: 0 ANSI: 0 CCS
[   26.634263] scsi 7:0:0:1: Direct-Access     IOI SM/x D-Picture Disk.. 1.09 PQ: 0 ANSI: 0 CCS
[   26.639122] scsi 7:0:0:2: Direct-Access     IOI SD/M MC Disk ...      1.09 PQ: 0 ANSI: 0 CCS
[   26.643994] scsi 7:0:0:3: Direct-Access     IOI MS/M sPro Disk ...    1.09 PQ: 0 ANSI: 0 CCS
[   26.646274] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[   26.651120] sd 7:0:0:0: Attached scsi generic sg3 type 0
[   26.653660] sd 7:0:0:1: [sdd] Attached SCSI removable disk
[   26.653775] sd 7:0:0:1: Attached scsi generic sg4 type 0
[   26.655444] sd 7:0:0:2: [sde] Attached SCSI removable disk
[   26.655515] sd 7:0:0:2: Attached scsi generic sg5 type 0
[   26.657318] sd 7:0:0:3: [sdf] Attached SCSI removable disk
[   26.658142] sd 7:0:0:3: Attached scsi generic sg6 type 0
[   26.972185] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   27.042643] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   27.063357] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   27.124681] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   27.124712] HDA Intel 0000:01:05.1: setting latency timer to 64
[   29.028020] lp: driver loaded but no devices found
[   29.802070] EXT3 FS on loop0, internal journal
[   45.726165] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:976552k
[   45.890014] type=1505 audit(1233616067.016:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4949
[   46.067293] type=1505 audit(1233616067.192:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4956
[   46.067611] type=1505 audit(1233616067.192:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4956
[   46.186953] ip_tables: (C) 2000-2006 Netfilter Core Team
[   46.740680] ACPI: WMI: Mapper loaded
[   46.990185] powernow-k8: Found 1 AMD Phenom(tm) 9100e Quad-Core Processor processors (4 cpu cores) (version 2.20.00)
[   46.990266] powernow-k8:    0 : pstate 0 (1800 MHz)
[   46.990270] powernow-k8:    1 : pstate 1 (900 MHz)
[   47.612205] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   47.739792] ppdev: user-space parallel port driver
[   49.513690] Bluetooth: Core ver 2.13
[   49.515307] NET: Registered protocol family 31
[   49.515317] Bluetooth: HCI device and connection manager initialized
[   49.515326] Bluetooth: HCI socket layer initialized
[   49.549329] Bluetooth: L2CAP ver 2.11
[   49.549352] Bluetooth: L2CAP socket layer initialized
[   49.588236] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   49.588259] Bluetooth: BNEP filters: protocol multicast
[   49.630297] Bridge firewalling registered
[   49.630813] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   49.649662] Bluetooth: RFCOMM socket layer initialized
[   49.649706] Bluetooth: RFCOMM TTY layer initialized
[   49.649711] Bluetooth: RFCOMM ver 1.10
[   49.665567] Bluetooth: SCO (Voice Link) ver 0.6
[   49.665591] Bluetooth: SCO socket layer initialized
[   50.381294] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   53.773312] sky2 eth0: enabling interface
[   53.985409] hda-intel: Invalid position buffer, using LPIB read method instead.
[  176.665459] rtusb init --->
[  176.665619] usbcore: registered new interface driver rt2870
[  204.276893] type=1503 audit(1233616225.399:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6509/net/" pid=6509 profile="/usr/sbin/cupsd"
[  204.365096] NET: Registered protocol family 10
[  204.366050] lo: Disabled Privacy Extensions
[  204.366924] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  204.368196] type=1503 audit(1233616225.491:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6509 profile="/usr/sbin/cupsd"
[  204.368213] type=1503 audit(1233616225.491:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6509 profile="/usr/sbin/cupsd"
[  204.368225] type=1503 audit(1233616225.491:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6509 profile="/usr/sbin/cupsd"
[  204.368236] type=1503 audit(1233616225.491:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6509 profile="/usr/sbin/cupsd"
[  204.368246] type=1503 audit(1233616225.491:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6509 profile="/usr/sbin/cupsd"
[  204.368258] type=1503 audit(1233616225.491:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6509 profile="/usr/sbin/cupsd"
[  204.368268] type=1503 audit(1233616225.491:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6509 profile="/usr/sbin/cupsd"
[  204.368281] type=1503 audit(1233616225.491:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6509 profile="/usr/sbin/cupsd"
[  204.368401] type=1503 audit(1233616225.491:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/6509/net/dev" pid=6509 profile="/usr/sbin/cupsd"



```

---

### Post by pytheas22 on 2009-02-02
hmmm, I still don't see any errors.  I wonder if it's just a matter of bringing up the interface.  What is the output of:
```

ifconfig -a
```

EDIT: I think I know what's wrong, which is that the source code doesn't identify your wireless card as a supported device, even though Google says it should.  To solve that problem, you can make a simple modification of the source code.  To do so, type:

```
gedit /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/include/rt2870.h
```

A file should open up.  Search it (control-F) for the following string:

```
USB_DEVICE(0x0789,0x0164)
```

This should bring you to line 145.  Immediately after that line, create a new line that looks like this:

```
{USB_DEVICE(0x1737,0x0070)}, /* Linksys */		\
```

In other words, lines 145-147 should look like this when you're done:

```
	{USB_DEVICE(0x0789,0x0164)}, /* Logitec */		\
	{USB_DEVICE(0x1737,0x0070)}, /* Linksys */		\
	{ }/* Terminating entry */                      \
```

Now save and close the file, then run these commands:

```
cd /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0
sudo make clean
sudo make
sudo make install
```

This will allow you to recompile the driver, but with the correct parameters for identifying your device.  When you're done, reboot.  If the card still doesn't work, please post the output of:

```
sudo modprobe rt2870sta
dmesg | grep rt
ifconfig -a
```

---

### Post by Mister J on 2009-02-02
No luck... Here are the results in order...

```
laughingmrj@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:22:68:3a:a3:4f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30448 (30.4 KB)  TX bytes:30448 (30.4 KB)

pan0      Link encap:Ethernet  HWaddr 8a:ab:8b:b8:4f:f8  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

laughingmrj@ubuntu:~$ 


```


```
laughingmrj@ubuntu:~$ gedit /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/include/rt2870.h
laughingmrj@ubuntu:~$ cd /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0
laughingmrj@ubuntu:~/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0$ sudo make clean
[sudo] password for laughingmrj: 
cp -f os/linux/Makefile.6 os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory `/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux'
rm -rf os/linux/Makefile
laughingmrj@ubuntu:~/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0$ sudo make
make -C tools
make[1]: Entering directory `/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/md5.o
In file included from /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/include/rt_config.h:58,
                 from /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/md5.c:40:
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/include/rt2870.h:147: error: expected identifier or ‘(’ before ‘{’ token
/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/include/rt2870.h:148: error: expected identifier or ‘(’ before ‘}’ token
make[2]: *** [/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/md5.o] Error 1
make[1]: *** [_module_/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [LINUX] Error 2
laughingmrj@ubuntu:~/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0$ sudo make install
make -C /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.27-7-generic
make[1]: Leaving directory `/home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux'
laughingmrj@ubuntu:~/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0$ 

```
```

laughingmrj@ubuntu:~$ sudo modprobe rt2870sta
[sudo] password for laughingmrj: 
Sorry, try again.
[sudo] password for laughingmrj: 
laughingmrj@ubuntu:~$ dmesg | grep rt
[    0.000000] KERNEL supported cpus:
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Movable zone start PFN for each node
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at d4000000 (gap: d0000000:2ff00000)
[    0.004000] Checking aperture...
[    0.004000] Node 0: aperture @ 20000000 size 32 MB
[    0.004000] Aperture pointing to e820 RAM. Ignoring.
[    0.004000] Your BIOS doesn't leave a aperture memory hole
[    0.004000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.704299] Booting paravirtualized kernel on bare hardware
[    0.704392] node 0 link 0: io port [1000, ffffff]
[    0.704392] bus: 00 index 0 io port: [0, ffff]
[    0.723169] ACPI: (supports S0 S1 S3 S4 S5)
[    0.760181] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.760184] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.760239] PCI: 0000:00:11.0 reg 10 io port: [b000, b007]
[    0.760246] PCI: 0000:00:11.0 reg 14 io port: [a000, a003]
[    0.760253] PCI: 0000:00:11.0 reg 18 io port: [9000, 9007]
[    0.760261] PCI: 0000:00:11.0 reg 1c io port: [8000, 8003]
[    0.760268] PCI: 0000:00:11.0 reg 20 io port: [7000, 700f]
[    0.760509] pci 0000:00:12.2: supports D1
[    0.760511] pci 0000:00:12.2: supports D2
[    0.760513] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.760723] pci 0000:00:13.2: supports D1
[    0.760725] pci 0000:00:13.2: supports D2
[    0.760726] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.760837] PCI: 0000:00:14.1 reg 10 io port: [0, 7]
[    0.760844] PCI: 0000:00:14.1 reg 14 io port: [0, 3]
[    0.760851] PCI: 0000:00:14.1 reg 18 io port: [0, 7]
[    0.760858] PCI: 0000:00:14.1 reg 1c io port: [0, 3]
[    0.760865] PCI: 0000:00:14.1 reg 20 io port: [ff00, ff0f]
[    0.760969] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.761230] PCI: 0000:01:05.0 reg 14 io port: [c000, c0ff]
[    0.761253] pci 0000:01:05.0: supports D1
[    0.761255] pci 0000:01:05.0: supports D2
[    0.761293] pci 0000:01:05.1: supports D1
[    0.761295] pci 0000:01:05.1: supports D2
[    0.761337] PCI: bridge 0000:00:01.0 io port: [c000, cfff]
[    0.761398] PCI: 0000:02:00.0 reg 18 io port: [d800, d8ff]
[    0.761435] pci 0000:02:00.0: supports D1
[    0.761437] pci 0000:02:00.0: supports D2
[    0.761439] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.761488] PCI: bridge 0000:00:05.0 io port: [d000, dfff]
[    0.761714] PCI: 0000:04:06.0 reg 10 io port: [e800, e8ff]
[    0.761775] pci 0000:04:06.0: PME# supported from D3hot D3cold
[    0.761828] PCI: bridge 0000:00:14.4 io port: [e000, efff]
[    0.769615] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.800688] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.800688] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.824065] system 00:0b: ioport range 0x200-0x20f has been reserved
[    0.824068] system 00:0b: ioport range 0x220-0x233 has been reserved
[    0.824070] system 00:0b: ioport range 0x240-0x253 has been reserved
[    0.824073] system 00:0b: ioport range 0x260-0x273 has been reserved
[    0.824075] system 00:0b: ioport range 0x280-0x293 has been reserved
[    0.824077] system 00:0b: ioport range 0x388-0x389 has been reserved
[    0.824080] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[    0.824082] system 00:0b: ioport range 0x40b-0x40b has been reserved
[    0.824085] system 00:0b: ioport range 0x4d6-0x4d6 has been reserved
[    0.824087] system 00:0b: ioport range 0xb00-0xb0f has been reserved
[    0.824090] system 00:0b: ioport range 0xb30-0xb3f has been reserved
[    0.824092] system 00:0b: ioport range 0xc00-0xc01 has been reserved
[    0.824095] system 00:0b: ioport range 0xc14-0xc14 has been reserved
[    0.824097] system 00:0b: ioport range 0xc50-0xc51 has been reserved
[    0.824099] system 00:0b: ioport range 0xc52-0xc52 has been reserved
[    0.824102] system 00:0b: ioport range 0xc6c-0xc6c has been reserved
[    0.824104] system 00:0b: ioport range 0xc6f-0xc6f has been reserved
[    0.824106] system 00:0b: ioport range 0xcd0-0xcd1 has been reserved
[    0.824109] system 00:0b: ioport range 0xcd2-0xcd3 has been reserved
[    0.824111] system 00:0b: ioport range 0xcd4-0xcd5 has been reserved
[    0.824114] system 00:0b: ioport range 0xcd6-0xcd7 has been reserved
[    0.824116] system 00:0b: ioport range 0xcd8-0xcdf has been reserved
[    0.824119] system 00:0b: ioport range 0x800-0x89f has been reserved
[    0.824122] system 00:0b: ioport range 0xb20-0xb3f could not be reserved
[    0.824124] system 00:0b: ioport range 0x900-0x90f has been reserved
[    0.824127] system 00:0b: ioport range 0x910-0x91f has been reserved
[    0.824130] system 00:0b: ioport range 0xfe00-0xfefe has been reserved
[    0.824146] system 00:0d: ioport range 0xe00-0xe0f has been reserved
[    0.824151] system 00:0d: ioport range 0xe80-0xe8f has been reserved
[    0.824153] system 00:0d: ioport range 0xf40-0xf4f has been reserved
[    0.824155] system 00:0d: ioport range 0xa30-0xa3f has been reserved
[    0.829546] bus: 00 index 0 io port: [0, ffff]
[    0.829551] bus: 01 index 0 io port: [c000, cfff]
[    0.829558] bus: 02 index 0 io port: [d000, dfff]
[    0.829571] bus: 04 index 0 io port: [e000, efff]
[    0.829576] bus: 04 index 3 io port: [0, ffff]
[    1.864199] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    1.864225] pcieport-driver 0000:00:05.0: found MSI capability
[    1.864255] pci_express 0000:00:05.0:pcie00: allocate port service
[    1.864342] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.864366] pcieport-driver 0000:00:06.0: found MSI capability
[    1.864391] pci_express 0000:00:06.0:pcie00: allocate port service
[    1.905761] Linux agpgart interface v0.103
[    1.905766] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.909028] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.909606] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.909613] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.933887] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.933914] rtc0: alarms up to one month, y3k, hpet irqs
[    1.934985] rtc_cmos 00:05: setting system clock to 2009-02-02 17:33:19 UTC (1233595999)
[    2.121749] ACPI: Processor [P001] (supports 8 throttling states)
[    2.498601] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    2.498605] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck led clo pmp pio slum part 
[    2.499330] ata1: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ff900 irq 22
[    2.499333] ata2: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ff980 irq 22
[    2.499337] ata3: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ffa00 irq 22
[    2.499340] ata4: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ffa80 irq 22
[    4.512197] hub 1-0:1.0: 3 ports detected
[    4.777339] hub 2-0:1.0: 3 ports detected
[    4.985591] ehci_hcd 0000:00:12.2: debug port 1
[    5.001519] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.001700] hub 3-0:1.0: 6 ports detected
[    5.269549] hub 4-0:1.0: 3 ports detected
[    5.452017] hub 1-0:1.0: unable to enumerate USB device on port 3
[    5.537565] hub 5-0:1.0: 3 ports detected
[    5.641762] ehci_hcd 0000:00:13.2: debug port 1
[    5.653521] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.653663] hub 6-0:1.0: 6 ports detected
[    6.257999] hub 7-0:1.0: 2 ports detected
[    6.393787] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.393903] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.896026] hub 6-0:1.0: unable to enumerate USB device on port 2
[    9.191498] USB Mass Storage support registered.
[   11.340022] hub 4-0:1.0: unable to enumerate USB device on port 2
[   21.496397] usbhid: timeout initializing reports
[   22.283791] kjournald starting.  Commit interval 5 seconds
[   25.976702] udevd version 124 started
[   26.399140] parport_pc 00:08: reported by Plug and Play ACPI
[   26.399835] parport_pc 00:08: disabled
[   47.534577] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   47.678993] ppdev: user-space parallel port driver
[  158.291742] rtusb init --->
[  158.292100] usbcore: registered new interface driver rt2870
laughingmrj@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:22:68:3a:a3:4f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30448 (30.4 KB)  TX bytes:30448 (30.4 KB)

pan0      Link encap:Ethernet  HWaddr fa:b1:f1:a2:0b:32  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

laughingmrj@ubuntu:~$ 


```

Thank you so much for sticking with me.

---

### Post by pytheas22 on 2009-02-02
It looks like your compilation of the modified source code failed due to some typo in the source file that you modified.  I'm not sure what happened, but please try this:

1. type:
```

gedit /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0/include/rt2870.h
```

2. delete everything in the file that opens and replace it with this:
```

/*
 *************************************************************************
 * Ralink Tech Inc.
 * 5F., No.36, Taiyuan St., Jhubei City,
 * Hsinchu County 302,
 * Taiwan, R.O.C.
 *
 * (c) Copyright 2002-2007, Ralink Technology, Inc.
 *
 * This program is free software; you can redistribute it and/or modify  * 
 * it under the terms of the GNU General Public License as published by  * 
 * the Free Software Foundation; either version 2 of the License, or     * 
 * (at your option) any later version.                                   * 
 *                                                                       * 
 * This program is distributed in the hope that it will be useful,       * 
 * but WITHOUT ANY WARRANTY; without even the implied warranty of        * 
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the         * 
 * GNU General Public License for more details.                          * 
 *                                                                       * 
 * You should have received a copy of the GNU General Public License     * 
 * along with this program; if not, write to the                         * 
 * Free Software Foundation, Inc.,                                       * 
 * 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.             * 
 *                                                                       * 
 *************************************************************************
 */

#ifndef __RT2870_H__
#define __RT2870_H__

//usb header files
#include <linux/usb.h>

/* rtmp_def.h */
//
#if LINUX_VERSION_CODE >= KERNEL_VERSION(2,5,0)
#define BULKAGGRE_ZISE          100
#define RT28XX_DRVDATA_SET(_a)                                             usb_set_intfdata(_a, pAd);
#define RT28XX_PUT_DEVICE                                                  usb_put_dev
#define RTUSB_ALLOC_URB(iso)                                               usb_alloc_urb(iso, GFP_ATOMIC)
#define RTUSB_SUBMIT_URB(pUrb)                                             usb_submit_urb(pUrb, GFP_ATOMIC)
#define	RTUSB_URB_ALLOC_BUFFER(pUsb_Dev, BufSize, pDma_addr)               usb_buffer_alloc(pUsb_Dev, BufSize, GFP_ATOMIC, pDma_addr)
#define	RTUSB_URB_FREE_BUFFER(pUsb_Dev, BufSize, pTransferBuf, Dma_addr)   usb_buffer_free(pUsb_Dev, BufSize, pTransferBuf, Dma_addr)
#else
#define BULKAGGRE_ZISE          60
#define RT28XX_DRVDATA_SET(_a)
#define RT28XX_PUT_DEVICE(dev_p)
#define RTUSB_ALLOC_URB(iso)                                               usb_alloc_urb(iso)
#define RTUSB_SUBMIT_URB(pUrb)                                             usb_submit_urb(pUrb)
#define RTUSB_URB_ALLOC_BUFFER(pUsb_Dev, BufSize, pDma_addr)               kmalloc(BufSize, GFP_ATOMIC)
#define	RTUSB_URB_FREE_BUFFER(pUsb_Dev, BufSize, pTransferBuf, Dma_addr)   kfree(pTransferBuf)
#endif

#define RXBULKAGGRE_ZISE        12
#define MAX_TXBULK_LIMIT        (LOCAL_TXBUF_SIZE*(BULKAGGRE_ZISE-1))
#define MAX_TXBULK_SIZE         (LOCAL_TXBUF_SIZE*BULKAGGRE_ZISE)
#define MAX_RXBULK_SIZE         (LOCAL_TXBUF_SIZE*RXBULKAGGRE_ZISE)
#define MAX_MLME_HANDLER_MEMORY 20
#define	RETRY_LIMIT             10
#define BUFFER_SIZE				2400	//2048
#define	TX_RING					0xa
#define	PRIO_RING				0xc


// Flags for Bulkflags control for bulk out data
//
#define	fRTUSB_BULK_OUT_DATA_NULL				0x00000001
#define fRTUSB_BULK_OUT_RTS						0x00000002
#define	fRTUSB_BULK_OUT_MLME					0x00000004

#define	fRTUSB_BULK_OUT_DATA_NORMAL				0x00010000
#define	fRTUSB_BULK_OUT_DATA_NORMAL_2			0x00020000
#define	fRTUSB_BULK_OUT_DATA_NORMAL_3			0x00040000
#define	fRTUSB_BULK_OUT_DATA_NORMAL_4			0x00080000

#define	fRTUSB_BULK_OUT_PSPOLL					0x00000020
#define	fRTUSB_BULK_OUT_DATA_FRAG				0x00000040
#define	fRTUSB_BULK_OUT_DATA_FRAG_2				0x00000080
#define	fRTUSB_BULK_OUT_DATA_FRAG_3				0x00000100
#define	fRTUSB_BULK_OUT_DATA_FRAG_4				0x00000200

#ifdef RALINK_ATE
#define	fRTUSB_BULK_OUT_DATA_ATE				0x00100000
#endif // RALINK_ATE //

#define RT2870_USB_DEVICES	\
{	\
	{USB_DEVICE(0x148F,0x2770)}, /* Ralink */		\
	{USB_DEVICE(0x148F,0x2870)}, /* Ralink */		\
	{USB_DEVICE(0x148F,0x3070)}, /* Ralink */		\
	{USB_DEVICE(0x0B05,0x1731)}, /* Asus */			\
	{USB_DEVICE(0x0B05,0x1732)}, /* Asus */			\
	{USB_DEVICE(0x0B05,0x1742)}, /* Asus */			\
	{USB_DEVICE(0x0DF6,0x0017)}, /* Sitecom */		\
	{USB_DEVICE(0x0DF6,0x002B)}, /* Sitecom */		\
	{USB_DEVICE(0x0DF6,0x002C)}, /* Sitecom */		\
	{USB_DEVICE(0x0DF6,0x002D)}, /* Sitecom */		\
	{USB_DEVICE(0x14B2,0x3C06)}, /* Conceptronic */		\
	{USB_DEVICE(0x14B2,0x3C28)}, /* Conceptronic */		\
	{USB_DEVICE(0x2019,0xED06)}, /* Planex Communications, Inc. */		\
	{USB_DEVICE(0x2019,0xAB25)}, /* Planex Communications, Inc. RT3070 */		\
	{USB_DEVICE(0x07D1,0x3C09)}, /* D-Link */		\
	{USB_DEVICE(0x07D1,0x3C11)}, /* D-Link */		\
	{USB_DEVICE(0x14B2,0x3C07)}, /* AL */			\
	{USB_DEVICE(0x14B2,0x3C12)}, /* AL */           \
	{USB_DEVICE(0x050D,0x8053)}, /* Belkin */		\
	{USB_DEVICE(0x14B2,0x3C23)}, /* Airlink */		\
	{USB_DEVICE(0x14B2,0x3C27)}, /* Airlink */		\
	{USB_DEVICE(0x07AA,0x002F)}, /* Corega */		\
	{USB_DEVICE(0x07AA,0x003C)}, /* Corega */		\
	{USB_DEVICE(0x07AA,0x003F)}, /* Corega */		\
	{USB_DEVICE(0x18C5,0x0012)}, /* Corega */		\
	{USB_DEVICE(0x1044,0x800B)}, /* Gigabyte */		\
	{USB_DEVICE(0x15A9,0x0006)}, /* Sparklan */		\
	{USB_DEVICE(0x083A,0xB522)}, /* SMC */			\
	{USB_DEVICE(0x083A,0xA618)}, /* SMC */			\
	{USB_DEVICE(0x083A,0x7522)}, /* Arcadyan */		\
	{USB_DEVICE(0x0CDE,0x0022)}, /* ZCOM */			\
	{USB_DEVICE(0x0586,0x3416)}, /* Zyxel */		\
	{USB_DEVICE(0x0CDE,0x0025)}, /* Zyxel */		\
	{USB_DEVICE(0x1740,0x9701)}, /* EnGenius */		\
	{USB_DEVICE(0x1740,0x9702)}, /* EnGenius */		\
	{USB_DEVICE(0x0471,0x200f)}, /* Philips */		\
	{USB_DEVICE(0x14B2,0x3C25)}, /* Draytek */		\
	{USB_DEVICE(0x13D3,0x3247)}, /* AzureWave */	\
	{USB_DEVICE(0x083A,0x6618)}, /* Accton */		\
	{USB_DEVICE(0x15c5,0x0008)}, /* Amit */			\
	{USB_DEVICE(0x0E66,0x0001)}, /* Hawking */		\
	{USB_DEVICE(0x0E66,0x0003)}, /* Hawking */		\
	{USB_DEVICE(0x129B,0x1828)}, /* Siemens */		\
	{USB_DEVICE(0x157E,0x300E)},	/* U-Media */	\
	{USB_DEVICE(0x050d,0x805c)},					\
	{USB_DEVICE(0x1482,0x3C09)}, /* Abocom*/		\
	{USB_DEVICE(0x14B2,0x3C09)}, /* Alpha */		\
	{USB_DEVICE(0x04E8,0x2018)}, /* samsung */  	\
	{USB_DEVICE(0x07B8,0x3070)}, /* AboCom */		\
	{USB_DEVICE(0x07B8,0x3071)}, /* AboCom */		\
	{USB_DEVICE(0x07B8,0x2870)}, /* AboCom */		\
	{USB_DEVICE(0x07B8,0x2770)}, /* AboCom */		\
	{USB_DEVICE(0x7392,0x7711)}, /* Edimax */		\
	{USB_DEVICE(0x5A57,0x0280)}, /* Zinwell */		\
	{USB_DEVICE(0x5A57,0x0282)}, /* Zinwell */		\
	{USB_DEVICE(0x0789,0x0162)}, /* Logitec */		\
	{USB_DEVICE(0x0789,0x0163)}, /* Logitec */		\
	{USB_DEVICE(0x0789,0x0164)}, /* Logitec */		\
	{USB_DEVICE(0x1737,0x0070)}, /* Linksys */		\
	{ }/* Terminating entry */                      \
}

#define	FREE_HTTX_RING(_p, _b, _t)			\
{										\
	if ((_t)->ENextBulkOutPosition == (_t)->CurWritePosition)				\
	{																	\
		(_t)->bRingEmpty = TRUE;			\
	}																	\
	/*NdisInterlockedDecrement(&(_p)->TxCount); */\
}

//
// RXINFO appends at the end of each rx packet.
//
#ifdef RT_BIG_ENDIAN
typedef	struct	PACKED _RXINFO_STRUC {
	UINT32		PlcpSignal:12;
	UINT32		LastAMSDU:1;
	UINT32		CipherAlg:1;
	UINT32		PlcpRssil:1;
	UINT32		Decrypted:1;
	UINT32		AMPDU:1;		// To be moved
	UINT32		L2PAD:1;
	UINT32		RSSI:1;
	UINT32		HTC:1;
	UINT32		AMSDU:1;		// rx with 802.3 header, not 802.11 header.
	UINT32		CipherErr:2;        // 0: decryption okay, 1:ICV error, 2:MIC error, 3:KEY not valid
	UINT32		Crc:1;              // 1: CRC error
	UINT32		MyBss:1;  	// 1: this frame belongs to the same BSSID	
	UINT32		Bcast:1;            // 1: this is a broadcast frame	
	UINT32		Mcast:1;            // 1: this is a multicast frame
	UINT32		U2M:1;              // 1: this RX frame is unicast to me
	UINT32		FRAG:1;
	UINT32		NULLDATA:1;
	UINT32		DATA:1;
	UINT32		BA:1;
}	RXINFO_STRUC, *PRXINFO_STRUC, RT28XX_RXD_STRUC, *PRT28XX_RXD_STRUC;
#else
typedef	struct	PACKED _RXINFO_STRUC {
	UINT32		BA:1;
	UINT32		DATA:1;
	UINT32		NULLDATA:1;
	UINT32		FRAG:1;
	UINT32		U2M:1;              // 1: this RX frame is unicast to me
	UINT32		Mcast:1;            // 1: this is a multicast frame
	UINT32		Bcast:1;            // 1: this is a broadcast frame	
	UINT32		MyBss:1;  	// 1: this frame belongs to the same BSSID	
	UINT32		Crc:1;              // 1: CRC error
	UINT32		CipherErr:2;        // 0: decryption okay, 1:ICV error, 2:MIC error, 3:KEY not valid
	UINT32		AMSDU:1;		// rx with 802.3 header, not 802.11 header.
	UINT32		HTC:1;
	UINT32		RSSI:1;
	UINT32		L2PAD:1;
	UINT32		AMPDU:1;		// To be moved
	UINT32		Decrypted:1;
	UINT32		PlcpRssil:1;
	UINT32		CipherAlg:1;
	UINT32		LastAMSDU:1;
	UINT32		PlcpSignal:12;
}	RXINFO_STRUC, *PRXINFO_STRUC, RT28XX_RXD_STRUC, *PRT28XX_RXD_STRUC;
#endif


//
// TXINFO
//
#ifdef RT_BIG_ENDIAN
typedef	struct	_TXINFO_STRUC {
	// Word	0
	UINT32		USBDMATxburst:1;//used ONLY in USB bulk Aggre. Force USB DMA transmit frame from current selected endpoint
	UINT32		USBDMANextVLD:1;	//used ONLY in USB bulk Aggregation, NextValid  
	UINT32		rsv2:2;  // Software use.
	UINT32		SwUseLastRound:1; // Software use. 
	UINT32		QSEL:2;	// select on-chip FIFO ID for 2nd-stage output scheduler.0:MGMT, 1:HCCA 2:EDCA
	UINT32		WIV:1;	// Wireless Info Valid. 1 if Driver already fill WI,  o if DMA needs to copy WI to correctposition
	UINT32		rsv:8;
	UINT32		USBDMATxPktLen:16;	//used ONLY in USB bulk Aggregation,  Total byte counts of all sub-frame.
}	TXINFO_STRUC, *PTXINFO_STRUC;
#else
typedef	struct	_TXINFO_STRUC {
	// Word	0
	UINT32		USBDMATxPktLen:16;	//used ONLY in USB bulk Aggregation,  Total byte counts of all sub-frame.   
	UINT32		rsv:8;
	UINT32		WIV:1;	// Wireless Info Valid. 1 if Driver already fill WI,  o if DMA needs to copy WI to correctposition
	UINT32		QSEL:2;	// select on-chip FIFO ID for 2nd-stage output scheduler.0:MGMT, 1:HCCA 2:EDCA
	UINT32		SwUseLastRound:1; // Software use. 
	UINT32		rsv2:2;  // Software use.
	UINT32		USBDMANextVLD:1;	//used ONLY in USB bulk Aggregation, NextValid  
	UINT32		USBDMATxburst:1;//used ONLY in USB bulk Aggre. Force USB DMA transmit frame from current selected endpoint
}	TXINFO_STRUC, *PTXINFO_STRUC;
#endif

#define TXINFO_SIZE				4
#define RXINFO_SIZE				4
#define TXPADDING_SIZE			11

//
// Management ring buffer format
//
typedef	struct	_MGMT_STRUC	{
	BOOLEAN		Valid;
	PUCHAR		pBuffer;
	ULONG		Length;
}	MGMT_STRUC, *PMGMT_STRUC;


/* ----------------- EEPROM Related MACRO ----------------- */
#define RT28xx_EEPROM_READ16(pAd, offset, var)					\
	do {														\
		RTUSBReadEEPROM(pAd, offset, (PUCHAR)&(var), 2);		\
		var = le2cpu16(var);									\
	}while(0)

#define RT28xx_EEPROM_WRITE16(pAd, offset, var)					\
	do{															\
		USHORT _tmpVar;											\
		_tmpVar = cpu2le16(var);								\
		RTUSBWriteEEPROM(pAd, offset, (PUCHAR)&(_tmpVar), 2);	\
	}while(0)

/* ----------------- TASK/THREAD Related MACRO ----------------- */
#define RT28XX_TASK_THREAD_INIT(pAd, Status)		\
	Status = CreateThreads(net_dev);


/* ----------------- Frimware Related MACRO ----------------- */
#if 0
#define RT28XX_FIRMUD_INIT(pAd)		\
	{	UINT32	MacReg;				\
		RTUSBReadMACRegister(pAd, MAC_CSR0, &MacReg); }

#define RT28XX_FIRMUD_END(pAd)	\
	RTUSBWriteMACRegister(pAd, 0x7014, 0xffffffff);	\
	RTUSBWriteMACRegister(pAd, 0x701c, 0xffffffff);	\
	RTUSBFirmwareRun(pAd);
#else
#define RT28XX_WRITE_FIRMWARE(_pAd, _pFwImage, _FwLen)		\
	RTUSBFirmwareWrite(_pAd, _pFwImage, _FwLen)
#endif

/* ----------------- TX Related MACRO ----------------- */
#define RT28XX_START_DEQUEUE(pAd, QueIdx, irqFlags)				\
			{													\
				RTMP_IRQ_LOCK(&pAd->DeQueueLock[QueIdx], irqFlags);		\
				if (pAd->DeQueueRunning[QueIdx])						\
				{														\
					RTMP_IRQ_UNLOCK(&pAd->DeQueueLock[QueIdx], irqFlags);\
					printk("DeQueueRunning[%d]= TRUE!\n", QueIdx);		\
					continue;											\
				}														\
				else													\
				{														\
					pAd->DeQueueRunning[QueIdx] = TRUE;					\
					RTMP_IRQ_UNLOCK(&pAd->DeQueueLock[QueIdx], irqFlags);\
				}														\
			}
#define RT28XX_STOP_DEQUEUE(pAd, QueIdx, irqFlags)						\
			do{															\
				RTMP_IRQ_LOCK(&pAd->DeQueueLock[QueIdx], irqFlags);		\
				pAd->DeQueueRunning[QueIdx] = FALSE;					\
				RTMP_IRQ_UNLOCK(&pAd->DeQueueLock[QueIdx], irqFlags);	\
			}while(0)

			
#define	RT28XX_HAS_ENOUGH_FREE_DESC(pAd, pTxBlk, freeNum, pPacket) \
		(RTUSBFreeDescriptorRequest(pAd, pTxBlk->QueIdx, (pTxBlk->TotalFrameLen + GET_OS_PKT_LEN(pPacket))) == NDIS_STATUS_SUCCESS)

#define RT28XX_RELEASE_DESC_RESOURCE(pAd, QueIdx)			\
		do{}while(0)

#define NEED_QUEUE_BACK_FOR_AGG(_pAd, _QueIdx, _freeNum, _TxFrameType) 		\
		((_TxFrameType == TX_RALINK_FRAME) && (RTUSBNeedQueueBackForAgg(_pAd, _QueIdx)))	



#define fRTMP_ADAPTER_NEED_STOP_TX		\
		(fRTMP_ADAPTER_NIC_NOT_EXIST | fRTMP_ADAPTER_HALT_IN_PROGRESS |	\
		 fRTMP_ADAPTER_RESET_IN_PROGRESS | fRTMP_ADAPTER_BULKOUT_RESET | \
		 fRTMP_ADAPTER_RADIO_OFF | fRTMP_ADAPTER_REMOVE_IN_PROGRESS)


#define HAL_WriteSubTxResource(pAd, pTxBlk, bIsLast, pFreeNumber)	\
			RtmpUSB_WriteSubTxResource(pAd, pTxBlk, bIsLast, pFreeNumber)
			
#define HAL_WriteTxResource(pAd, pTxBlk,bIsLast, pFreeNumber)	\
			RtmpUSB_WriteSingleTxResource(pAd, pTxBlk,bIsLast, pFreeNumber)

#define HAL_WriteFragTxResource(pAd, pTxBlk, fragNum, pFreeNumber) \
			RtmpUSB_WriteFragTxResource(pAd, pTxBlk, fragNum, pFreeNumber)
			
#define HAL_WriteMultiTxResource(pAd, pTxBlk,frameNum, pFreeNumber)	\
			RtmpUSB_WriteMultiTxResource(pAd, pTxBlk,frameNum, pFreeNumber)
	
#define HAL_FinalWriteTxResource(pAd, pTxBlk, totalMPDUSize, TxIdx)	\
			RtmpUSB_FinalWriteTxResource(pAd, pTxBlk, totalMPDUSize, TxIdx)

#define HAL_LastTxIdx(pAd, QueIdx,TxIdx) \
			/*RtmpUSBDataLastTxIdx(pAd, QueIdx,TxIdx)*/
	
#define HAL_KickOutTx(pAd, pTxBlk, QueIdx)	\
			RtmpUSBDataKickOut(pAd, pTxBlk, QueIdx)


#define HAL_KickOutMgmtTx(pAd, QueIdx, pPacket, pSrcBufVA, SrcBufLen)	\
			RtmpUSBMgmtKickOut(pAd, QueIdx, pPacket, pSrcBufVA, SrcBufLen)

#define HAL_KickOutNullFrameTx(_pAd, _QueIdx, _pNullFrame, _frameLen)	\
			RtmpUSBNullFrameKickOut(_pAd, _QueIdx, _pNullFrame, _frameLen)
			
#define RTMP_PKT_TAIL_PADDING 	11 // 3(max 4 byte padding) + 4 (last packet padding) + 4 (MaxBulkOutsize align padding)

extern UCHAR EpToQueue[6];


#ifdef RT2870
#define GET_TXRING_FREENO(_pAd, _QueIdx) 	(_QueIdx) //(_pAd->TxRing[_QueIdx].TxSwFreeIdx)
#define GET_MGMTRING_FREENO(_pAd) 			(_pAd->MgmtRing.TxSwFreeIdx)
#endif // RT2870 //


/* ----------------- RX Related MACRO ----------------- */
//#define RT28XX_RX_ERROR_CHECK				RTMPCheckRxWI

#if 0
#define RT28XX_RCV_INIT(pAd)					\
	pAd->TransferBufferLength = 0;				\
	pAd->ReadPosition = 0;						\
	pAd->pCurrRxContext = NULL;
#endif

#define RT28XX_RV_ALL_BUF_END(bBulkReceive)		\
	/* We return STATUS_MORE_PROCESSING_REQUIRED so that the completion */	\
	/* routine (IofCompleteRequest) will stop working on the irp. */		\
	if (bBulkReceive == TRUE)	RTUSBBulkReceive(pAd);


/* ----------------- ASIC Related MACRO ----------------- */
#if 0
#define RT28XX_DMA_WRITE_INIT(GloCfg)			\
	{	GloCfg.field.EnTXWriteBackDDONE = 1;	\
		GloCfg.field.EnableRxDMA = 1;			\
		GloCfg.field.EnableTxDMA = 1; }

#define RT28XX_DMA_POST_WRITE(_pAd)				\
	do{	USB_DMA_CFG_STRUC	UsbCfg;				\
		UsbCfg.word = 0;						\
		/* for last packet, PBF might use more than limited, so minus 2 to prevent from error */ \
		UsbCfg.field.RxBulkAggLmt = (MAX_RXBULK_SIZE /1024)-3;	\
		UsbCfg.field.phyclear = 0;								\
		/* usb version is 1.1,do not use bulk in aggregation */	\
		if (_pAd->BulkInMaxPacketSize == 512)					\
			UsbCfg.field.RxBulkAggEn = 1;						\
		UsbCfg.field.RxBulkEn = 1;								\
		UsbCfg.field.TxBulkEn = 1;								\
		UsbCfg.field.RxBulkAggTOut = 0x80; /* 2006-10-18 */		\
		RTUSBWriteMACRegister(_pAd, USB_DMA_CFG, UsbCfg.word); 	\
	}while(0)
#endif

// reset MAC of a station entry to 0xFFFFFFFFFFFF
#define RT28XX_STA_ENTRY_MAC_RESET(pAd, Wcid)					\
	{	RT_SET_ASIC_WCID	SetAsicWcid;						\
		SetAsicWcid.WCID = Wcid;								\
		SetAsicWcid.SetTid = 0xffffffff;						\
		SetAsicWcid.DeleteTid = 0xffffffff;						\
		RTUSBEnqueueInternalCmd(pAd, CMDTHREAD_SET_ASIC_WCID, 	\
				&SetAsicWcid, sizeof(RT_SET_ASIC_WCID));	}

// add this entry into ASIC RX WCID search table
#define RT28XX_STA_ENTRY_ADD(pAd, pEntry)							\
	RTUSBEnqueueInternalCmd(pAd, CMDTHREAD_SET_CLIENT_MAC_ENTRY, 	\
							pEntry, sizeof(MAC_TABLE_ENTRY));

// remove Pair-wise key material from ASIC
// yet implement
#define RT28XX_STA_ENTRY_KEY_DEL(pAd, BssIdx, Wcid)

// add Client security information into ASIC WCID table and IVEIV table
#define RT28XX_STA_SECURITY_INFO_ADD(pAd, apidx, KeyID, pEntry)						\
	{	RT28XX_STA_ENTRY_MAC_RESET(pAd, pEntry->Aid);								\
		if (pEntry->Aid >= 1) {														\
			RT_SET_ASIC_WCID_ATTRI	SetAsicWcidAttri;								\
			SetAsicWcidAttri.WCID = pEntry->Aid;									\
			if ((pEntry->AuthMode <= Ndis802_11AuthModeAutoSwitch) &&				\
				(pEntry->WepStatus == Ndis802_11Encryption1Enabled))				\
			{																		\
				SetAsicWcidAttri.Cipher = pAd->SharedKey[apidx][KeyID].CipherAlg;	\
			}																		\
			else if (pEntry->AuthMode == Ndis802_11AuthModeWPANone)					\
			{																		\
				SetAsicWcidAttri.Cipher = pAd->SharedKey[apidx][KeyID].CipherAlg;	\
			}																		\
			else SetAsicWcidAttri.Cipher = 0;										\
            DBGPRINT(RT_DEBUG_TRACE, ("aid cipher = %ld\n",SetAsicWcidAttri.Cipher));       \
			RTUSBEnqueueInternalCmd(pAd, CMDTHREAD_SET_ASIC_WCID_CIPHER, 			\
							&SetAsicWcidAttri, sizeof(RT_SET_ASIC_WCID_ATTRI)); } }

// Insert the BA bitmap to ASIC for the Wcid entry
#define RT28XX_ADD_BA_SESSION_TO_ASIC(_pAd, _Aid, _TID)					\
		do{																\
			RT_SET_ASIC_WCID	SetAsicWcid;							\
			SetAsicWcid.WCID = (_Aid);									\
			SetAsicWcid.SetTid = (0x10000<<(_TID));						\
			SetAsicWcid.DeleteTid = 0xffffffff;							\
			RTUSBEnqueueInternalCmd((_pAd), CMDTHREAD_SET_ASIC_WCID, &SetAsicWcid, sizeof(RT_SET_ASIC_WCID));	\
		}while(0)

// Remove the BA bitmap from ASIC for the Wcid entry
#define RT28XX_DEL_BA_SESSION_FROM_ASIC(_pAd, _Wcid, _TID)				\
		do{																\
			RT_SET_ASIC_WCID	SetAsicWcid;							\
			SetAsicWcid.WCID = (_Wcid);									\
			SetAsicWcid.SetTid = (0xffffffff);							\
			SetAsicWcid.DeleteTid = (0x10000<<(_TID) );					\
			RTUSBEnqueueInternalCmd((_pAd), CMDTHREAD_SET_ASIC_WCID, &SetAsicWcid, sizeof(RT_SET_ASIC_WCID));	\
		}while(0)

		
/* ----------------- PCI/USB Related MACRO ----------------- */
#define RT28XX_HANDLE_DEV_ASSIGN(handle, dev_p)			\
	((POS_COOKIE)handle)->pUsb_Dev = dev_p;

// no use
#define RT28XX_UNMAP()
#define RT28XX_IRQ_REQUEST(net_dev)
#define RT28XX_IRQ_RELEASE(net_dev)
#define RT28XX_IRQ_INIT(pAd)
#define RT28XX_IRQ_ENABLE(pAd)


/* ----------------- MLME Related MACRO ----------------- */
#define RT28XX_MLME_HANDLER(pAd)			RTUSBMlmeUp(pAd)

#define RT28XX_MLME_PRE_SANITY_CHECK(pAd)								\
	{	if ((pAd->CommonCfg.bHardwareRadio == TRUE) && 					\
			(!RTMP_TEST_FLAG(pAd, fRTMP_ADAPTER_NIC_NOT_EXIST)) &&		\
			(!RTMP_TEST_FLAG(pAd, fRTMP_ADAPTER_HALT_IN_PROGRESS))) {	\
			RTUSBEnqueueInternalCmd(pAd, CMDTHREAD_CHECK_GPIO, NULL, 0); } }

#define RT28XX_MLME_STA_QUICK_RSP_WAKE_UP(pAd)	\
	{	RTUSBEnqueueInternalCmd(pAd, CMDTHREAD_QKERIODIC_EXECUT, NULL, 0);	\
		RTUSBMlmeUp(pAd); }

#define RT28XX_MLME_RESET_STATE_MACHINE(pAd)	\
		        MlmeEnqueue(pAd, MLME_CNTL_STATE_MACHINE, MT2_RESET_CONF, 0, NULL);	\
		        RTUSBMlmeUp(pAd);

#define RT28XX_HANDLE_COUNTER_MEASURE(_pAd, _pEntry)		\
	{	RTUSBEnqueueInternalCmd(_pAd, CMDTHREAD_802_11_COUNTER_MEASURE, _pEntry, sizeof(MAC_TABLE_ENTRY));	\
		RTUSBMlmeUp(_pAd);									\
	}


/* ----------------- Power Save Related MACRO ----------------- */
#define RT28XX_PS_POLL_ENQUEUE(pAd)						\
	{	RTUSB_SET_BULK_FLAG(pAd, fRTUSB_BULK_OUT_PSPOLL);	\
		RTUSBKickBulkOut(pAd); }

#define RT28xx_CHIP_NAME            "RT2870"
#define USB_CYC_CFG                 0x02a4
#define STATUS_SUCCESS				0x00
#define STATUS_UNSUCCESSFUL 		0x01
#define NT_SUCCESS(status)			(((status) > 0) ? (1):(0))
#define InterlockedIncrement 	 	atomic_inc
#define NdisInterlockedIncrement 	atomic_inc
#define InterlockedDecrement		atomic_dec
#define NdisInterlockedDecrement 	atomic_dec
#define InterlockedExchange			atomic_set
//#define NdisMSendComplete			RTMP_SendComplete
#define NdisMCancelTimer			RTMPCancelTimer
#define NdisAllocMemory(_ptr, _size, _flag)	\
									do{_ptr = kmalloc((_size),(_flag));}while(0)
#define NdisFreeMemory(a, b, c) 	kfree((a))
#define NdisMSleep					RTMPusecDelay		/* unit: microsecond */


#define USBD_TRANSFER_DIRECTION_OUT		0
#define USBD_TRANSFER_DIRECTION_IN		0
#define USBD_SHORT_TRANSFER_OK			0
#define PURB			purbb_t

#define RTUSB_FREE_URB(pUrb)	usb_free_urb(pUrb)

//#undef MlmeAllocateMemory
//#undef MlmeFreeMemory

typedef int				NTSTATUS;
typedef struct usb_device	* PUSB_DEV;

/* MACRO for linux usb */
typedef struct urb *purbb_t;
typedef struct usb_ctrlrequest devctrlrequest;
#define PIRP		PVOID
#define PMDL		PVOID
#define NDIS_OID	UINT
#ifndef USB_ST_NOERROR
#define USB_ST_NOERROR     0
#endif

// vendor-specific control operations
#define CONTROL_TIMEOUT_JIFFIES ( (100 * HZ) / 1000)
#define UNLINK_TIMEOUT_MS		3

/* unlink urb	*/
#if LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,7)
#define RTUSB_UNLINK_URB(pUrb)		usb_kill_urb(pUrb)
#else
#define RTUSB_UNLINK_URB(pUrb)		usb_unlink_urb(pUrb)
#endif

// Prototypes of completion funuc.
#if LINUX_VERSION_CODE < KERNEL_VERSION(2,5,0)
#define RTUSBBulkOutDataPacketComplete(purb, pt_regs)    RTUSBBulkOutDataPacketComplete(purb)
#define RTUSBBulkOutMLMEPacketComplete(pUrb, pt_regs)    RTUSBBulkOutMLMEPacketComplete(pUrb)
#define RTUSBBulkOutNullFrameComplete(pUrb, pt_regs)     RTUSBBulkOutNullFrameComplete(pUrb)
#define RTUSBBulkOutRTSFrameComplete(pUrb, pt_regs)      RTUSBBulkOutRTSFrameComplete(pUrb)
#define RTUSBBulkOutPsPollComplete(pUrb, pt_regs)        RTUSBBulkOutPsPollComplete(pUrb)
#define RTUSBBulkRxComplete(pUrb, pt_regs)               RTUSBBulkRxComplete(pUrb)
#endif


VOID RTUSBBulkOutDataPacketComplete(purbb_t purb, struct pt_regs *pt_regs);
VOID RTUSBBulkOutMLMEPacketComplete(purbb_t pUrb, struct pt_regs *pt_regs);
VOID RTUSBBulkOutNullFrameComplete(purbb_t pUrb, struct pt_regs *pt_regs);
VOID RTUSBBulkOutRTSFrameComplete(purbb_t pUrb, struct pt_regs *pt_regs);
VOID RTUSBBulkOutPsPollComplete(purbb_t pUrb, struct pt_regs *pt_regs);
VOID RTUSBBulkRxComplete(purbb_t pUrb, struct pt_regs *pt_regs);


#define RTUSBMlmeUp(pAd)	        \
{								    \
	POS_COOKIE pObj = (POS_COOKIE) pAd->OS_Cookie;	\
	CHECK_PID_LEGALITY(pObj->MLMEThr_pid)		    \
        up(&(pAd->mlme_semaphore)); \
}

#define RTUSBCMDUp(pAd)	                \
{									    \
	POS_COOKIE pObj = (POS_COOKIE) pAd->OS_Cookie;	\
	CHECK_PID_LEGALITY(pObj->RTUSBCmdThr_pid)	    \
	    up(&(pAd->RTUSBCmd_semaphore)); \
}


static inline NDIS_STATUS RTMPAllocateMemory(
	OUT PVOID *ptr,
	IN size_t size)
{
	*ptr = kmalloc(size, GFP_ATOMIC);
	if(*ptr)
		return NDIS_STATUS_SUCCESS;
	else
		return NDIS_STATUS_RESOURCES;
}

/* rtmp.h */
#define	BEACON_RING_SIZE                2
#define DEVICE_VENDOR_REQUEST_OUT       0x40
#define DEVICE_VENDOR_REQUEST_IN        0xc0
#define INTERFACE_VENDOR_REQUEST_OUT    0x41
#define INTERFACE_VENDOR_REQUEST_IN     0xc1
#define MGMTPIPEIDX						0	// EP6 is highest priority

#define BULKOUT_MGMT_RESET_FLAG				0x80

#define RTUSB_SET_BULK_FLAG(_M, _F)				((_M)->BulkFlags |= (_F))
#define RTUSB_CLEAR_BULK_FLAG(_M, _F)			((_M)->BulkFlags &= ~(_F))
#define RTUSB_TEST_BULK_FLAG(_M, _F)			(((_M)->BulkFlags & (_F)) != 0)

#define EnqueueCmd(cmdq, cmdqelmt)		\
{										\
	if (cmdq->size == 0)				\
		cmdq->head = cmdqelmt;			\
	else								\
		cmdq->tail->next = cmdqelmt;	\
	cmdq->tail = cmdqelmt;				\
	cmdqelmt->next = NULL;				\
	cmdq->size++;						\
}

typedef struct   _RT_SET_ASIC_WCID {
	ULONG WCID;          // mechanism for rekeying: 0:disable, 1: time-based, 2: packet-based
	ULONG SetTid;        // time-based: seconds, packet-based: kilo-packets
	ULONG DeleteTid;        // time-based: seconds, packet-based: kilo-packets
	UCHAR Addr[MAC_ADDR_LEN];	// avoid in interrupt when write key
} RT_SET_ASIC_WCID,*PRT_SET_ASIC_WCID;

typedef struct   _RT_SET_ASIC_WCID_ATTRI {
	ULONG	WCID;          // mechanism for rekeying: 0:disable, 1: time-based, 2: packet-based
	ULONG	Cipher;        // ASIC Cipher definition
	UCHAR	Addr[ETH_LENGTH_OF_ADDRESS];	
} RT_SET_ASIC_WCID_ATTRI,*PRT_SET_ASIC_WCID_ATTRI;

typedef struct _MLME_MEMORY_STRUCT {
	PVOID                           AllocVa;    //Pointer to the base virtual address of the allocated memory
	struct _MLME_MEMORY_STRUCT      *Next;      //Pointer to the next virtual address of the allocated memory
}   MLME_MEMORY_STRUCT, *PMLME_MEMORY_STRUCT;

typedef struct  _MLME_MEMORY_HANDLER {
	BOOLEAN                 MemRunning;         //The flag of the Mlme memory handler's status
	UINT                    MemoryCount;        //Total nonpaged system-space memory not size
	UINT                    InUseCount;         //Nonpaged system-space memory in used counts
	UINT                    UnUseCount;         //Nonpaged system-space memory available counts
	INT                    PendingCount;       //Nonpaged system-space memory for free counts
	PMLME_MEMORY_STRUCT     pInUseHead;         //Pointer to the first nonpaed memory not used
	PMLME_MEMORY_STRUCT     pInUseTail;         //Pointer to the last nonpaged memory not used
	PMLME_MEMORY_STRUCT     pUnUseHead;         //Pointer to the first nonpaged memory in used
	PMLME_MEMORY_STRUCT     pUnUseTail;         //Pointer to the last nonpaged memory in used
	PULONG                  MemFreePending[MAX_MLME_HANDLER_MEMORY];   //an array to keep pending free-memory's pointer (32bits)
}   MLME_MEMORY_HANDLER, *PMLME_MEMORY_HANDLER;

typedef	struct _CmdQElmt	{
	UINT				command;
	PVOID				buffer;
	ULONG				bufferlength;
	BOOLEAN				CmdFromNdis;
	BOOLEAN				SetOperation;
	struct _CmdQElmt	*next;
}	CmdQElmt, *PCmdQElmt;

typedef	struct	_CmdQ	{
	UINT		size;
	CmdQElmt	*head;
	CmdQElmt	*tail;
	UINT32		CmdQState;
}CmdQ, *PCmdQ;

// 
// For WPA SUPPLICANT: WIRELESS EXT support wireless events: v14 or newer
//
#if WIRELESS_EXT >= 14
//#define WPA_SUPPLICANT_SUPPORT  1
#endif

/* oid.h */
// Cipher suite type for mixed mode group cipher, P802.11i-2004
typedef enum _RT_802_11_CIPHER_SUITE_TYPE {
	Cipher_Type_NONE,
	Cipher_Type_WEP40,
	Cipher_Type_TKIP,
	Cipher_Type_RSVD,
	Cipher_Type_CCMP,
	Cipher_Type_WEP104
} RT_802_11_CIPHER_SUITE_TYPE, *PRT_802_11_CIPHER_SUITE_TYPE;

//CMDTHREAD_MULTI_READ_MAC
//CMDTHREAD_MULTI_WRITE_MAC
//CMDTHREAD_VENDOR_EEPROM_READ
//CMDTHREAD_VENDOR_EEPROM_WRITE
typedef	struct	_CMDHandler_TLV	{
	USHORT		Offset;
	USHORT		Length;
	UCHAR		DataFirst;
}	CMDHandler_TLV, *PCMDHandler_TLV;

// New for MeetingHouse Api support
#define CMDTHREAD_VENDOR_RESET                      0x0D730101	// cmd
#define CMDTHREAD_VENDOR_UNPLUG                     0x0D730102	// cmd
#define CMDTHREAD_VENDOR_SWITCH_FUNCTION            0x0D730103	// cmd
#define CMDTHREAD_MULTI_WRITE_MAC                   0x0D730107	// cmd
#define CMDTHREAD_MULTI_READ_MAC                    0x0D730108	// cmd
#define CMDTHREAD_VENDOR_EEPROM_WRITE               0x0D73010A	// cmd
#define CMDTHREAD_VENDOR_EEPROM_READ                0x0D73010B	// cmd
#define CMDTHREAD_VENDOR_ENTER_TESTMODE             0x0D73010C	// cmd
#define CMDTHREAD_VENDOR_EXIT_TESTMODE              0x0D73010D	// cmd
#define CMDTHREAD_VENDOR_WRITE_BBP                  0x0D730119	// cmd
#define CMDTHREAD_VENDOR_READ_BBP                   0x0D730118	// cmd
#define CMDTHREAD_VENDOR_WRITE_RF                   0x0D73011A	// cmd
#define CMDTHREAD_VENDOR_FLIP_IQ                    0x0D73011D	// cmd
#define CMDTHREAD_RESET_BULK_OUT                    0x0D730210	// cmd
#define CMDTHREAD_RESET_BULK_IN                     0x0D730211	// cmd
#define CMDTHREAD_SET_PSM_BIT_SAVE                  0x0D730212	// cmd
#define CMDTHREAD_SET_RADIO                         0x0D730214	// cmd
#define CMDTHREAD_UPDATE_TX_RATE                    0x0D730216	// cmd
#define CMDTHREAD_802_11_ADD_KEY_WEP                0x0D730218	// cmd
#define CMDTHREAD_RESET_FROM_ERROR                  0x0D73021A	// cmd
#define CMDTHREAD_LINK_DOWN                         0x0D73021B	// cmd
#define CMDTHREAD_RESET_FROM_NDIS                   0x0D73021C	// cmd
#define CMDTHREAD_CHECK_GPIO                        0x0D730215	// cmd
#define CMDTHREAD_FORCE_WAKE_UP                     0x0D730222	// cmd
#define CMDTHREAD_SET_BW                            0x0D730225	// cmd
#define CMDTHREAD_SET_ASIC_WCID                     0x0D730226	// cmd
#define CMDTHREAD_SET_ASIC_WCID_CIPHER              0x0D730227	// cmd
#define CMDTHREAD_QKERIODIC_EXECUT                  0x0D73023D	// cmd
#define RT_CMD_SET_KEY_TABLE                        0x0D730228  // cmd
#define RT_CMD_SET_RX_WCID_TABLE                    0x0D730229  // cmd
#define CMDTHREAD_SET_CLIENT_MAC_ENTRY              0x0D73023E	// cmd
#define CMDTHREAD_802_11_QUERY_HARDWARE_REGISTER    0x0D710105	// cmd
#define CMDTHREAD_802_11_SET_PHY_MODE               0x0D79010C	// cmd
#define CMDTHREAD_802_11_SET_STA_CONFIG             0x0D790111	// cmd
#define CMDTHREAD_802_11_SET_PREAMBLE               0x0D790101	// cmd
#define CMDTHREAD_802_11_COUNTER_MEASURE			0x0D790102	// cmd


#define WPA1AKMBIT	    0x01
#define WPA2AKMBIT	    0x02
#define WPA1PSKAKMBIT   0x04
#define WPA2PSKAKMBIT   0x08
#define TKIPBIT         0x01
#define CCMPBIT         0x02


#define RT28XX_STA_FORCE_WAKEUP(pAd, bFromTx) \
    RT28xxUsbStaAsicForceWakeup(pAd, bFromTx);

#define RT28XX_STA_SLEEP_THEN_AUTO_WAKEUP(pAd, TbttNumToNextWakeUp) \
    RT28xxUsbStaAsicSleepThenAutoWakeup(pAd, TbttNumToNextWakeUp);

#define RT28XX_MLME_RADIO_ON(pAd) \
    RT28xxUsbMlmeRadioOn(pAd);

#define RT28XX_MLME_RADIO_OFF(pAd) \
    RT28xxUsbMlmeRadioOFF(pAd);

#endif //__RT2870_H__
```

3. save and close the file, then try recompiling again by typing:
```

cd /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0
sudo make clean
sudo make
sudo make install
```

This should work--I just tested it on my own machine with the modification to the source code that I made above, and it compiles without a problem.

If you get any errors while trying to compile the module, please post them.  If compilation succeeds, then please reboot and see if the card works.  If not, please post:
```

sudo modprobe rt2870sta
ifconfig -a
dmesg | grep -e rt -e ra
```

Sorry this is proving to be so tricky, but we'll get there...

---

### Post by Mister J on 2009-02-03
Pytheas22, I think you'll be very pleased to know that I'm typing this message using Firefox within Ubuntu. SUCCESS! Thank you so much, this was a HUGE help to me. Also, a special thanks to you, Ugm6hr.

Now that that buisness is out of the, I remembered you mentioning that the fix isn't permanent? In my own research I found that a certain driver that automatically installs from the Linksys hardware needs to be blocked to be able to run consistently. But I did get on the net from a reboot, so maybe it's a moot point. Anyways, Thanks again!

Mister J hereby awards Pytheas22 an "Epic win" trophy, to be displayed in your signature if you so choose.

---

### Post by ugm6hr on 2009-02-03
To correct that error you had earlier:
```
sudo apt-get install -f
```

The driver should load automatically.  If it doesn't, a simple:
```
sudo modprobe rt2870sta
```

If you have to do that manually, you should be able to add a line to /etc/modules to auto-load it at boot:
```
gksudo gedit /etc/modules
```
And add: **rt2870sta** to a separate line at the bottom

---

### Post by pytheas22 on 2009-02-03
I'm very glad to hear it's finally working!  Sorry it took so long to figure it out, but the fact that the source code was missing your device ID was not obvious at first.

As ugm6hr writes above, the driver actually should be permanently installed--when I said that it was only temporary, it was because I didn't think that the driver had a built-in way of installing itself permanently (no 'make install' on the Makefile), but that assumption turned out to be incorrect.  So if the card automatically works through reboots, you should be all set.  If not, follow ugm6hr's instructions about adding the line 'rt2870sta' to your /etc/modules file.

The last thing I should point out is that if you update your kernel via Ubuntu updates--a new kernel generally gets pushed out about once a month--you will need to recompile the wireless driver in order for it to work with the new kernel.  So you should keep the source code on hand (with the modified file containing your device ID), and if you upgrade kernels, cd into the source-code directory (right now, it's at /home/laughingmrj/Desktop/2008_0925_RT2870_Linux_STA_v1.4.0.0) and type:
```

sudo make clean
sudo make
sudo make install
```

to compile it against the newer kernel.

Eventually, this driver should be built into the Linux kernel itself, obviating the need to do all this manual installation and making your wireless card a truly 'no hassle' device.

---

### Post by Mister J on 2009-02-03
Aww, man. I downloaded a bunch of updates, and now my Internet is broken. I typed cd /home/laughingmrj (etc.) and it says "no such file or directory". I'm so sorry but I don't know how to fix it.

---

### Post by ugm6hr on 2009-02-03
> **Mister J said:**
> Aww, man. I downloaded a bunch of updates, and now my Internet is broken. I typed cd /home/laughingmrj (etc.) and it says "no such file or directory". I'm so sorry but I don't know how to fix it.

Where is the folder?  Just find it again with nautilus

---

### Post by Mister J on 2009-02-03
What is nautilus? If it's a program, I don't think I have it and I no longer have Internet in Ubuntu.

---

### Post by ugm6hr on 2009-02-03
> **Mister J said:**
> What is nautilus? If it's a program, I don't think I have it and I no longer have Internet in Ubuntu.

It is the File Browser.

And I know you don't have internet on Ubuntu. You don't need it.

You need to find where you put that folder (previously on your Desktop).

Then just open a Terminal in that folder and run the commands as advised.

The reason you got a folder not found is because:
1. You moved the folder.
2. You typed the directory name in wrongly.

If 2. - use the tab key to help...

In Terminal: type:
```
cd Desk <press Tab key> /2008 <press Tab key>
```

---

### Post by Mister J on 2009-02-03
Oh ****. I still needed that? I trashed it. What was the name of the file again? I'll put it back

Edit: Found it. I'll put it back.

2nd edit: I put the all the files back where they were, navigated to them, ran the 3 codes, and rebooted. Still no internet. I have no idea what went wrong. (Besides my idiocy in clearing off my desktop)

3rd edit: I followed the advice ugm6hr gave for if I didn't get internet on subsequent reboots. Everything is exactly as it was, except for the new update. I ran a couple commands in the hopes someone might catch an error or something. 


```
laughingmrj@ubuntu:~$ sudo modprobe rt2870sta
[sudo] password for laughingmrj: 
laughingmrj@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:22:68:3a:a3:4f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

pan0      Link encap:Ethernet  HWaddr a2:e7:6e:21:a6:73  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ra0       Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

laughingmrj@ubuntu:~$ dmesg |
> 
> 
> dmesg | grep -e rt -e ra
[    0.000000] KERNEL supported cpus:
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Zone PFN ranges:
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at d4000000 (gap: d0000000:2ff00000)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.004000] Checking aperture...
[    0.004000] Node 0: aperture @ 20000000 size 32 MB
[    0.004000] Aperture pointing to e820 RAM. Ignoring.
[    0.004000] Your BIOS doesn't leave a aperture memory hole
[    0.004000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 3600.14 BogoMIPS (lpj=7200292)
[    0.004036] Security Framework initialized
[    0.011483] ACPI: Checking initramfs for custom DSDT
[    0.432028] APIC timer calibration result 12500517
[    0.004000] Calibrating delay using timer specific routine.. 3600.42 BogoMIPS (lpj=7200858)
[    0.004000] Calibrating delay using timer specific routine.. 3600.30 BogoMIPS (lpj=7200617)
[    0.004000] Calibrating delay using timer specific routine.. 3600.32 BogoMIPS (lpj=7200641)
[    0.708296] Booting paravirtualized kernel on bare hardware
[    0.708403] node 0 link 0: io port [1000, ffffff]
[    0.708403] bus: 00 index 0 io port: [0, ffff]
[    0.708403] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.708403] PCI: Using configuration type 1 for base access
[    0.708403] PCI: Using configuration type 1 for extended access
[    0.726847] ACPI: (supports S0 S1 S3 S4 S5)
[    0.726943] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.764874] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.764874] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.764874] PCI: 0000:00:11.0 reg 10 io port: [b000, b007]
[    0.764874] PCI: 0000:00:11.0 reg 14 io port: [a000, a003]
[    0.764874] PCI: 0000:00:11.0 reg 18 io port: [9000, 9007]
[    0.764874] PCI: 0000:00:11.0 reg 1c io port: [8000, 8003]
[    0.764874] PCI: 0000:00:11.0 reg 20 io port: [7000, 700f]
[    0.764874] pci 0000:00:12.2: supports D1
[    0.764874] pci 0000:00:12.2: supports D2
[    0.764874] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.764874] pci 0000:00:13.2: supports D1
[    0.764874] pci 0000:00:13.2: supports D2
[    0.764874] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.764874] PCI: 0000:00:14.1 reg 10 io port: [0, 7]
[    0.764874] PCI: 0000:00:14.1 reg 14 io port: [0, 3]
[    0.764874] PCI: 0000:00:14.1 reg 18 io port: [0, 7]
[    0.764874] PCI: 0000:00:14.1 reg 1c io port: [0, 3]
[    0.764874] PCI: 0000:00:14.1 reg 20 io port: [ff00, ff0f]
[    0.764973] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.768246] PCI: 0000:01:05.0 reg 14 io port: [c000, c0ff]
[    0.768270] pci 0000:01:05.0: supports D1
[    0.768271] pci 0000:01:05.0: supports D2
[    0.768310] pci 0000:01:05.1: supports D1
[    0.768311] pci 0000:01:05.1: supports D2
[    0.768353] PCI: bridge 0000:00:01.0 io port: [c000, cfff]
[    0.768415] PCI: 0000:02:00.0 reg 18 io port: [d800, d8ff]
[    0.768453] pci 0000:02:00.0: supports D1
[    0.768454] pci 0000:02:00.0: supports D2
[    0.768456] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.768505] PCI: bridge 0000:00:05.0 io port: [d000, dfff]
[    0.768730] PCI: 0000:04:06.0 reg 10 io port: [e800, e8ff]
[    0.768791] pci 0000:04:06.0: PME# supported from D3hot D3cold
[    0.768839] pci 0000:00:14.4: transparent bridge
[    0.768844] PCI: bridge 0000:00:14.4 io port: [e000, efff]
[    0.777502] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.800057] NetLabel:  unlabeled traffic allowed by default
[    0.800689] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.800689] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.806848] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.824064] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.824068] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.824076] system 00:0b: ioport range 0x200-0x20f has been reserved
[    0.824079] system 00:0b: ioport range 0x220-0x233 has been reserved
[    0.824082] system 00:0b: ioport range 0x240-0x253 has been reserved
[    0.824084] system 00:0b: ioport range 0x260-0x273 has been reserved
[    0.824086] system 00:0b: ioport range 0x280-0x293 has been reserved
[    0.824089] system 00:0b: ioport range 0x388-0x389 has been reserved
[    0.824091] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[    0.824094] system 00:0b: ioport range 0x40b-0x40b has been reserved
[    0.824096] system 00:0b: ioport range 0x4d6-0x4d6 has been reserved
[    0.824099] system 00:0b: ioport range 0xb00-0xb0f has been reserved
[    0.824101] system 00:0b: ioport range 0xb30-0xb3f has been reserved
[    0.824104] system 00:0b: ioport range 0xc00-0xc01 has been reserved
[    0.824106] system 00:0b: ioport range 0xc14-0xc14 has been reserved
[    0.824108] system 00:0b: ioport range 0xc50-0xc51 has been reserved
[    0.824111] system 00:0b: ioport range 0xc52-0xc52 has been reserved
[    0.824113] system 00:0b: ioport range 0xc6c-0xc6c has been reserved
[    0.824116] system 00:0b: ioport range 0xc6f-0xc6f has been reserved
[    0.824118] system 00:0b: ioport range 0xcd0-0xcd1 has been reserved
[    0.824121] system 00:0b: ioport range 0xcd2-0xcd3 has been reserved
[    0.824123] system 00:0b: ioport range 0xcd4-0xcd5 has been reserved
[    0.824126] system 00:0b: ioport range 0xcd6-0xcd7 has been reserved
[    0.824129] system 00:0b: ioport range 0xcd8-0xcdf has been reserved
[    0.824131] system 00:0b: ioport range 0x800-0x89f has been reserved
[    0.824134] system 00:0b: ioport range 0xb20-0xb3f could not be reserved
[    0.824137] system 00:0b: ioport range 0x900-0x90f has been reserved
[    0.824140] system 00:0b: ioport range 0x910-0x91f has been reserved
[    0.824143] system 00:0b: ioport range 0xfe00-0xfefe has been reserved
[    0.824146] system 00:0b: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.824149] system 00:0b: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.824160] system 00:0d: ioport range 0xe00-0xe0f has been reserved
[    0.824165] system 00:0d: ioport range 0xe80-0xe8f has been reserved
[    0.824167] system 00:0d: ioport range 0xf40-0xf4f has been reserved
[    0.824170] system 00:0d: ioport range 0xa30-0xa3f has been reserved
[    0.824179] system 00:10: iomem range 0xe0000000-0xefffffff has been reserved
[    0.824185] system 00:11: iomem range 0x0-0x9ffff could not be reserved
[    0.824188] system 00:11: iomem range 0xc0000-0xcffff has been reserved
[    0.824190] system 00:11: iomem range 0xe0000-0xfffff could not be reserved
[    0.824193] system 00:11: iomem range 0x100000-0xcfffffff could not be reserved
[    0.824196] system 00:11: iomem range 0xfed45000-0xffffffff could not be reserved
[    0.829568] bus: 00 index 0 io port: [0, ffff]
[    0.829572] bus: 01 index 0 io port: [c000, cfff]
[    0.829580] bus: 02 index 0 io port: [d000, dfff]
[    0.829594] bus: 04 index 0 io port: [e000, efff]
[    0.829599] bus: 04 index 3 io port: [0, ffff]
[    0.888285] checking if image is initramfs... it is
[    1.876223] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    1.876249] pcieport-driver 0000:00:05.0: found MSI capability
[    1.876279] pci_express 0000:00:05.0:pcie00: allocate port service
[    1.876369] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.876394] pcieport-driver 0000:00:06.0: found MSI capability
[    1.876418] pci_express 0000:00:06.0:pcie00: allocate port service
[    1.921072] Linux agpgart interface v0.103
[    1.921077] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.924336] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.924943] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.924952] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.949882] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.949910] rtc0: alarms up to one month, y3k, hpet irqs
[    1.951002] rtc_cmos 00:05: setting system clock to 2009-02-03 15:21:35 UTC (1233674495)
[    1.970356] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.220076] ACPI: Processor [P001] (supports 8 throttling states)
[    2.513719] usb usb1: configuration #1 chosen from 1 choice
[    2.513765] hub 1-0:1.0: 3 ports detected
[    2.793779] usb usb2: configuration #1 chosen from 1 choice
[    2.793844] hub 2-0:1.0: 3 ports detected
[    3.061681] usb usb3: configuration #1 chosen from 1 choice
[    3.061725] hub 3-0:1.0: 3 ports detected
[    3.079611] usb 1-3: configuration #1 chosen from 1 choice
[    3.328109] usb usb4: configuration #1 chosen from 1 choice
[    3.328147] hub 4-0:1.0: 3 ports detected
[    3.393617] usb 2-1: configuration #1 chosen from 1 choice
[    3.428357] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    3.428361] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck led clo pmp pio slum part 
[    3.429053] ata1: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ff900 irq 22
[    3.429057] ata2: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ff980 irq 22
[    3.429061] ata3: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ffa00 irq 22
[    3.429065] ata4: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ffa80 irq 22
[    3.697346] usb 2-2: configuration #1 chosen from 1 choice
[    5.372052] ehci_hcd 0000:00:12.2: debug port 1
[    5.384022] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.384143] usb usb5: configuration #1 chosen from 1 choice
[    5.384185] hub 5-0:1.0: 6 ports detected
[    5.593858] ehci_hcd 0000:00:13.2: debug port 1
[    5.604027] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.604128] usb usb6: configuration #1 chosen from 1 choice
[    5.604166] hub 6-0:1.0: 6 ports detected
[    5.660032] hub 3-0:1.0: unable to enumerate USB device on port 2
[    5.872120] usb usb7: configuration #1 chosen from 1 choice
[    5.872158] hub 7-0:1.0: 2 ports detected
[    6.442343] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.442474] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.572439] usb 5-3: configuration #1 chosen from 1 choice
[    6.672592] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.873739] usb 5-5: configuration #1 chosen from 1 choice
[    7.117754] usb 6-2: configuration #1 chosen from 1 choice
[    7.402078] usb 6-3: configuration #1 chosen from 1 choice
[    7.411593] Initializing USB Mass Storage driver...
[    7.833492] usb 2-1: configuration #1 chosen from 1 choice
[    7.835741] scsi6 : SCSI emulation for USB Mass Storage devices
[    7.835855] usb-storage: device found at 4
[    7.835859] usb-storage: waiting for device to settle before scanning
[    7.835939] scsi7 : SCSI emulation for USB Mass Storage devices
[    7.836019] usb-storage: device found at 2
[    7.836021] usb-storage: waiting for device to settle before scanning
[   12.832237] usb-storage: device scan complete
[   12.836189] usb-storage: device scan complete
[   17.836151] usbhid: timeout initializing reports
[   17.836338] hiddev96hidraw0: USB HID v1.11 Device [Generic USB2.0-CRW] on usb-0000:00:13.2-3
[   17.836488] scsi8 : SCSI emulation for USB Mass Storage devices
[   17.836616] usb-storage: device found at 3
[   17.836620] usb-storage: waiting for device to settle before scanning
[   17.861661] input,hidraw1: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:12.1-1
[   17.862946] usbcore: registered new interface driver usb-storage
[   17.862952] USB Mass Storage support registered.
[   18.701420] kjournald starting.  Commit interval 5 seconds
[   22.836217] usb-storage: device scan complete
[   23.066444] udevd version 124 started
[   23.589013] parport_pc 00:08: reported by Plug and Play ACPI
[   23.589699] parport_pc 00:08: disabled
[   23.888147] rtusb init --->
[   23.889443] usbcore: registered new interface driver rt2870
[   36.316649] type=1505 audit(1233703329.440:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4774
[   36.496634] type=1505 audit(1233703329.617:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4779
[   36.496968] type=1505 audit(1233703329.620:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4779
[   38.453381] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   38.634129] ppdev: user-space parallel port driver
laughingmrj@ubuntu:~$ 

```

---

### Post by ugm6hr on 2009-02-03
Simplest thing for now - reboot into the old kernel.

Don't know how to do that?

When you boot - there will be a 3 sec countdown when you can press Escape to enter the Grub menu.  Press Escape and select the third entry (probably) - or whichever is the second non-recovery option.

That should get you back online for now, until someone more knowledgeable comes along.

Also - assuming that works, complete the build-essential install:
```
sudo apt-get install build-essential
```

PS: When you put all the files back, are you sure you put back the "edited" files as instructed by pytheas?  It is likely that one of the files you restored was incorrect.  Once back online, re-download fresh copies and re-edit as instructed through this thread.  Then save the edited driver files somewhere for future use!

---

### Post by Mister J on 2009-02-03
Okay, I still don't know what I did, but my internet is back on. And honestly, whether it was providence, the help of others, or blunder, it's back. Thanks guys.

---

### Post by pytheas22 on 2009-02-03
Glad the networking is working again (whatever the reason is); let us know if you have any more trouble.

---

### Post by Mister J on 2009-02-04
It's a minor issue, but now I have 5 files cluttering my desktop. Is there any way to safely move them somewhere else without causing my network to screw up?

---

### Post by pytheas22 on 2009-02-05
Sure, you can put those files wherever you want now--the important parts were copied into the system directories when you typed 'sudo make install'.  Just keep a copy of the source code on hand somewhere for the next time you have to recompile the driver (i.e., when you get a new kernel).

---

### Post by Mister J on 2009-02-05
Awesome. Thanks. This OS is so much more fun than Vista, and it doesn't have nearly as many annoyances. Me being less paranoid about viruses is a bonus too.

---

