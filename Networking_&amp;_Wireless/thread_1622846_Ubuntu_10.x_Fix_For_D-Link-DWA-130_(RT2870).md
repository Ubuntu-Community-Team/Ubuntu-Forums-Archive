---
title: "Ubuntu 10.x Fix For D-Link-DWA-130 (RT2870)"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by Interix5 on 2010-11-16
The D-Link DWA-130 should be recognised 'out of the box' on Ubuntu 10.04  and 10.10, using the rt2800usb module, yet does not work properly when  you try to connect to networks. To fix this we need to blacklist the  rt2800usb module and instead use the rt2870sta module. 

While this directed at users of the D-Link DWA-130 USB adapter, it may help others with the RT2870 chipset get up and running with Ubuntu 10.x or similar variant. 

This was comprised of collaborated efforts of linux users throughout the web, and I was glad I got mine working, so I decided to write up what I did. I hope it helps. 

```
ID 07d1:3c13 D-Link System DWA-130 802.11n Wireless N Adapter(rev.B) [Ralink RT2870]

```First add 'blacklist rt2800usb' to the end of the /etc/modprobe.d/blacklist.conf file.
```
sudo nano /etc/modprobe.d/blacklist.conf
```Save and restart.

Next we need to compile a new Ralink RT2870USB driver. Download it from here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Extract it and change your terminal directory to the main driver folder which should be called '2010_0709_RT2870_Linux_STA_v2.4.0.1'.

Enter the following command (Thanks to linuxcrew.de)
```
wget -qO- http://www.linuxcrew.de/wp-content/uploads/2010/10/rt2870sta_usb_kernel2635.patch | patch -ul -p0
```It should echo 'patching file ./include/os/rt_linux.h'. 

Next we need to edit config.mk which is located in the /os/linux/ directory.
```
sudo nano /os/linux/config.mk
```Change the value for HAS_WPA_SUPPLICANT and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT from n to y as follows:
```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

```We are all finished patching the driver for installation, yet we need to edit the RT2870STA.dat file so we don't have to later. It will be located at /etc/Wireless/RT2870STA/RT2870STA.dat once the installation is finished.
```
sudo nano RT2870STA.dat
```Change the file to what you see fit, for more information on the .dat file configuration check out this page: [https://wiki.archlinux.org/index.php/Rt2870](https://wiki.archlinux.org/index.php/Rt2870) (Note: This part may not be necessary to connect to WPA2 or wireless N networks, you can always try without it)

Remove the rt2870STA.ko in /lib/modules/2.6.35-22-generic/kernel/drivers/staging/rt2870/ if it exists. 

Now we can compile the driver. Make sure you have build-essential installed. 
```
sudo apt-get install build-essential

sudo make

sudo make install
```Once it has finished compiling enter the following commands, after you should which you should be able to connect with no issues to any network! **(Note: This is for D-Link DWA-130 USB device ID 07d1 3c13, If you have a different device ID switch it with the one you receive from the 'lsusb' output in the first command within the following.) **
```

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo  "07d1 3c13" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee  /etc/modprobe.d/rt2870sta.conf

sudo modprobe -rf rt2870sta

sudo modprobe rt2870sta

dmesg | egrep 'rt28|usb|Phy'

iwconfig

```iwconfig should now show the connection ra0. Add 'rt2870sta' to the end of /etc/modules.
```
sudo nano /etc/modules
```

---

### Post by havarha on 2010-11-22
What speed do you get with your DWA-130? I think 10.10 uses the rt2870sta as default, and it seems to only supprt 802.11g, and not 802.11n.

I've been using one of these for a while now, and I only get 54Mbps. Too bad, when I should be getting 200+.

Are there any other drivers, which maybe supports N? If not, what other wireless devices is there out there that works on linux with N?

---

### Post by Interix5 on 2010-12-26
Mine is running at 150, as thats the max my router supports, but it should work all the way up to 300 Mbps.

The point of what I wrote is to deviate from the stock wireless driver for this adapter, and to configure and compile a new one to use in it's place which supports wireless N.

---

### Post by mdwy62 on 2011-03-13
Interix5 - Thanks for these instructions. My make (and subsequently make install) produced errors. I am running ubuntu 10.04. I am running make in the ~/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/ folder. 

I blacklisted blacklist rt2800usb in /etc/modprobe.d/blacklist.conf

I forgot to restart. I have tried restarting and I believe I get the same make errors. The errors below are those that were generated after the restart.

I downloaded the driver RT2870USB from the ralink webisite link above.

I ran the linuxcrew.de patch

I made the Supplicant settings changes to config.mk

I did not make changes to the dat file.

I removed the rt2870STA.ko in /lib/modules/2.6.32-29-generic/kernel/drivers/staging/rt2870/

build-essential was already installed. I ran sudo apt-get install build-essential anyway. It indicated that some packages were installed and no longer needed and to run apt-get auto-remove. So I did. make creates 2 errors. 

Thanks for any suggestions.

sudo make
make -C tools
make[1]: Entering directory `/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools/bin2h
cp -f os/linux/Makefile.6 /home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/Makefile
make -C /lib/modules/2.6.32-29-generic/build SUBDIRS=/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-29-generic'
  CC [M]  /home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocUsbBulkBufStruct’:
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function ‘usb_alloc_coherent’
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52: warning: assignment makes pointer from integer without a cast
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeUsbBulkBufStruct’:
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:78: error: implicit declaration of function ‘usb_free_coherent’
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:234: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:241: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:278: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
make[2]: *** [/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/d/temp/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-29-generic'
make: *** [LINUX] Error 2

---

### Post by mdwy62 on 2011-03-19
When I insert the dwa-130, lsmod does not show any additional modules being loaded. My built in wireless g card is iwl3945. Should I use modprobe to uninstall this first to get an rt module to load? Even after sudo modprobe -r iwl3945, no new  module is loaded when the dwa-130 is inserted.
I have also run sudo modprobe rt2870sta. This shows the rt2870sta with lsmod, but no dwa-130 activity.The dwa-130 shows up with lsusb:
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 005: ID 04d9:1400 Holtek Semiconductor, Inc. 
Bus 006 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 07d1:3300 D-Link System 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by chili555 on 2011-03-19
> 07d1:3300 D-Link System This is not an rt2870sta device. ```
modinfo [COLOR="Blue"]r8192s_usb[/COLOR] | grep 3300
alias:          usb:v[COLOR="Red"]07D1[/COLOR]p[COLOR="Red"]3300[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```What about your 3945 is not working correctly?

---

### Post by Talon2 on 2011-03-19
> **mdwy62 said:**
> When I insert the dwa-130, lsmod does not show any additional modules being loaded.

You might take a look at this bug report as it have suggestions:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801)

You might even subscribe to this bug in an effort to get some attention to this bug.

Unfortunately the problem with RT2870 chipset usb devices is a REGRESSION.  They worked in 9.04 but have been broken since.  Launchpad and this forum are littered with reports but nothing had been done.  The unfortunate thing is that the drivers are available but at no point in the distro or kernel development process is this being addressed.

---

### Post by mdwy62 on 2011-03-20
Thanks for this. I have tried some of the suggestions there, and posted some comments, and subscribed to the bug. Think in the mean time I will return the dwa-130. Any suggests for a usb-wireless N card that works with Lucid?

---

