---
title: "Error when Compiling compat-wireless-2011-04-17"
date: 2011-04-18
forum: Networking &amp; Wireless
---

### Post by MSwal2846 on 2011-04-18
I have an issue with the Linux Kernel that comes from Ubuntu 10.10 on my Lenovo X200 and my wireless device.  What has worked very well in the past has been to execute these instructions:

  1) first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2"
  2) sudo apt-get update
  3) sudo apt-get install build-essential
  4) cd ~/Desktop
  5) tar -xjvf compat-wireless-2.6.tar.bz2
  6) cd compat-wireless*
  7) make
  8) sudo make unload
  9) sudo make load
  10)sudo make install

Unfortunately, whenever the Kernel gets updated, I need to redo these instructions.

When I do this for the "make" step (step 7), I get this error:

```
mswallow-> make
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.35-28-generic-pae/build M=/home/mswallow/Desktop/compat-wireless-2011-04-17 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic-pae'
  LD      /home/mswallow/Desktop/compat-wireless-2011-04-17/compat/built-in.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/compat/main.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/compat/compat-2.6.36.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/compat/kfifo.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/compat/compat-2.6.37.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/compat/compat-2.6.38.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/compat/compat-2.6.39.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/compat/kstrtox.o
  LD [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/compat/compat.o
  LD      /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/built-in.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/hci_vhci.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/btmrvl_main.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/btmrvl_debugfs.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/hci_ldisc.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/hci_h4.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/hci_bcsp.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/hci_ll.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/hci_ath.o
  LD [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/hci_uart.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/bcm203x.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/bpa10x.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/bfusb.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/dtl1_cs.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/bt3c_cs.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/bluecard_cs.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/btuart_cs.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/btusb.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/btsdio.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/ath3k.o
  LD [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/btmrvl.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/btmrvl_sdio.o
  LD      /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/misc/eeprom/built-in.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/misc/eeprom/eeprom_93cx6.o
  LD      /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/built-in.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/b44.o
/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/b44.c:13: warning: "pr_fmt" redefined
include/linux/kernel.h:381: note: this is the location of the previous definition
  LD      /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/built-in.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/atl1c_main.o
/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/atl1c_main.c: In function ‘atl1c_change_mtu’:
/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/atl1c_main.c:527: error: implicit declaration of function ‘netdev_update_features’
/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/atl1c_main.c: At top level:
/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/atl1c_main.c:2595: error: unknown field ‘ndo_fix_features’ specified in initializer
/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/atl1c_main.c:2595: warning: initialization from incompatible pointer type
/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/atl1c_main.c: In function ‘atl1c_init_netdev’:
/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/atl1c_main.c:2616: error: ‘struct net_device’ has no member named ‘hw_features’
/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/atl1c_main.c:2621: error: ‘struct net_device’ has no member named ‘hw_features’
make[4]: *** [/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/atl1c_main.o] Error 1
make[3]: *** [/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c] Error 2
make[2]: *** [/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net] Error 2
make[1]: *** [_module_/home/mswallow/Desktop/compat-wireless-2011-04-17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic-pae'
make: *** [modules] Error 2
```

Any ideas on what is going wrong?  It worked with the last upgrade, but is not with this one.

---

### Post by MSwal2846 on 2011-04-19
bump.... any help?

---

### Post by uncaspi on 2011-04-19
Seems to be a compiling conflict due to that different versions of the gcc compiler is used. You could try to upgrade your gcc compiler. sudo apt-get upgrade gcc
The driver source code seems to be fairly new and you get these errors when compiling with and older version of gcc than the driver source code is written for.

---

### Post by MSwal2846 on 2011-04-20
Mmmm, no joy:

mswallow-> sudo apt-get upgrade gcc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  agnclient
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
[~]

---

### Post by chili555 on 2011-04-20
Did the compat-wireless package in the Ubuntu repositories not work or otherwise meet your needs? I can't see anything you are missing or doing wrong and, therefore I suggest you ask the compat developers.

---

### Post by MSwal2846 on 2011-04-20
I had to go this route due to issues with my machine (x200) and the Intel wireless device and compiling this compat-wireless set was the only thing that help ... which was day and night in usability.  

The latest issue is (was) my machine not wanting to wake up the wireless device from suspend.  However, since posting, I've not experienced this issue.  So  I'm still hanging in there...

---

### Post by chili555 on 2011-04-20
What Intel device do you have? What is it's problem?

---

### Post by MSwal2846 on 2011-04-21
Hi Chili555,

This thread documents the whole "sorted affair" :D :  [http://ubuntuforums.org/showthread.php?t=1203594&highlight=mswal2846&page=6](http://ubuntuforums.org/showthread.php?t=1203594&highlight=mswal2846&page=6)

---

### Post by chili555 on 2011-04-21
Did you try to install the compat-wireless package from the repositories on your Maverick install? What does this tell us?```
dmesg | grep iwl
```Does this help?```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn swcrypto=1
sudo ifconfig wlan0 up
```

---

### Post by MSwal2846 on 2011-04-22
Here are the command results:

dmesg | grep iwl

```
mswallow-> dmesg | grep iwl
[   10.014093] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   10.014096] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   10.014162] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.014171] iwlagn 0000:03:00.0: setting latency timer to 64
[   10.014204] iwlagn 0000:03:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   10.033392] iwlagn 0000:03:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   10.033394] iwlagn 0000:03:00.0: Device SKU: 0Xb
[   10.033420] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   10.033544] iwlagn 0000:03:00.0: irq 46 for MSI/MSI-X
[   10.885066] iwlagn 0000:03:00.0: loaded firmware version 8.83.5.1 build 33692
[   11.759976] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 7674.496827] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100506)
[10550.392828] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100506)
[12124.592827] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100506)
[~]
```

sudo ifconfig wlan0 down

```
mswallow-> sudo ifconfig wlan0 down
[sudo] password for mswallow: 
[~]
```


sudo rmmod -f iwlagn

```
mswallow-> sudo rmmod -f iwlagn
[~]
```

sudo modprobe iwlagn swcrypto=1

```
mswallow-> sudo modprobe iwlagn swcrypto=1
[~]
```

sudo ifconfig wlan0 up

```
mswallow-> sudo ifconfig wlan0 up
[~]
```

I've not altered what I've been doing since upgrading to Maverick as it was working great and didn't need to change anything.  But your point concerning trying the backports is a good one and I will explore it if my problem persists.  I've not experienced this problem in the past week despite numerous suspends/resumes.

---

### Post by chili555 on 2011-04-23
> sudo modprobe iwlagn swcrypto=1After this, did stability improve?

---

### Post by MSwal2846 on 2011-04-24
So far so good ... I'll post regular updates over the next week.  Thank you!

---

### Post by chili555 on 2011-04-25
The change will disappear on reboot and have to be re-done. If it helps and you'd like to make it permanent, we'll need to write one file.

---

### Post by MSwal2846 on 2011-04-30
Wow!  I'm impressed by the stability.  What will have to be done for 11.4?

---

### Post by chili555 on 2011-04-30
> **MSwal2846 said:**
> Wow!  I'm impressed by the stability.  What will have to be done for 11.4?Exactly the same:```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn swcrypto=1
sudo ifconfig wlan0 up
```However:> The change will disappear on reboot and have to be re-done. If it helps and you'd like to make it permanent, we'll need to write one file. Are you ready to write a permanent file?

---

### Post by MSwal2846 on 2011-05-03
Yes, please....

---

### Post by chili555 on 2011-05-03
Alrighty, then:```
sudo gedit /etc/modprobe.d/iwlagn.conf
```A new empty text file will open; add one line:```
options iwlagn swcrypto=1
```Proofread carefully, save and close gedit.

You should be all set.

---

### Post by MSwal2846 on 2011-05-05
Thanks, Chili555!

---

### Post by milind8a on 2012-04-13
Hi 

I am seeing the same problem compiling compat-wireless-2012-02-27 on Ubuntu 11.04.

How did you fix your compile problem?

Thx and cheers.

Milind

> **MSwal2846 said:**
> I have an issue with the Linux Kernel that comes from Ubuntu 10.10 on my Lenovo X200 and my wireless device.  What has worked very well in the past has been to execute these instructions:

  1) first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2"
  2) sudo apt-get update
  3) sudo apt-get install build-essential
  4) cd ~/Desktop
  5) tar -xjvf compat-wireless-2.6.tar.bz2
  6) cd compat-wireless*
  7) make
  8) sudo make unload
  9) sudo make load
  10)sudo make install

Unfortunately, whenever the Kernel gets updated, I need to redo these instructions.

When I do this for the "make" step (step 7), I get this error:

```
mswallow-> make
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.35-28-generic-pae/build M=/home/mswallow/Desktop/compat-wireless-2011-04-17 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic-pae'
  LD      /home/mswallow/Desktop/compat-wireless-2011-04-17/compat/built-in.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/compat/main.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/compat/compat-2.6.36.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/compat/kfifo.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/compat/compat-2.6.37.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/compat/compat-2.6.38.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/compat/compat-2.6.39.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/compat/kstrtox.o
  LD [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/compat/compat.o
  LD      /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/built-in.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/hci_vhci.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/btmrvl_main.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/btmrvl_debugfs.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/hci_ldisc.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/hci_h4.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/hci_bcsp.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/hci_ll.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/hci_ath.o
  LD [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/hci_uart.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/bcm203x.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/bpa10x.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/bfusb.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/dtl1_cs.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/bt3c_cs.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/bluecard_cs.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/btuart_cs.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/btusb.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/btsdio.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/ath3k.o
  LD [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/btmrvl.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/bluetooth/btmrvl_sdio.o
  LD      /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/misc/eeprom/built-in.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/misc/eeprom/eeprom_93cx6.o
  LD      /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/built-in.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/b44.o
/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/b44.c:13: warning: "pr_fmt" redefined
include/linux/kernel.h:381: note: this is the location of the previous definition
  LD      /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/built-in.o
  CC [M]  /home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/atl1c_main.o
/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/atl1c_main.c: In function ‘atl1c_change_mtu’:
/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/atl1c_main.c:527: error: implicit declaration of function ‘netdev_update_features’
/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/atl1c_main.c: At top level:
/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/atl1c_main.c:2595: error: unknown field ‘ndo_fix_features’ specified in initializer
/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/atl1c_main.c:2595: warning: initialization from incompatible pointer type
/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/atl1c_main.c: In function ‘atl1c_init_netdev’:
/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/atl1c_main.c:2616: error: ‘struct net_device’ has no member named ‘hw_features’
/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/atl1c_main.c:2621: error: ‘struct net_device’ has no member named ‘hw_features’
make[4]: *** [/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c/atl1c_main.o] Error 1
make[3]: *** [/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net/atl1c] Error 2
make[2]: *** [/home/mswallow/Desktop/compat-wireless-2011-04-17/drivers/net] Error 2
make[1]: *** [_module_/home/mswallow/Desktop/compat-wireless-2011-04-17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic-pae'
make: *** [modules] Error 2
```

Any ideas on what is going wrong?  It worked with the last upgrade, but is not with this one.

---

### Post by chili555 on 2012-04-13
> **milind8a said:**
> Hi 

I am seeing the same problem compiling compat-wireless-2012-02-27 on Ubuntu 11.04.

How did you fix your compile problem?

Thx and cheers.

MilindI doubt that compiling is really needed. The packages are included in linux-backports-modules-[COLOR="Red"]**cw**[/COLOR]. Can you install it from Synaptic?

What are you trying to accomplish? Maybe there is an easier way.

---

### Post by milind8a on 2012-04-24
> **chili555 said:**
> I doubt that compiling is really needed. The packages are included in linux-backports-modules-[COLOR="Red"]**cw**[/COLOR]. Can you install it from Synaptic?

What are you trying to accomplish? Maybe there is an easier way.

Hi 
Many thanks for response.
I am using a compat-wireless-02-27 tarball customized by someone.
The standard backports stuff from Ubuntu distribution does not have those features.

Wondering any insights?
Appreciate any help.

Thanks and cheers.

Milind

---

### Post by chili555 on 2012-04-24
> I am using a compat-wireless-02-27 tarball customized by someone.Frankly, I'd ask them.

---

