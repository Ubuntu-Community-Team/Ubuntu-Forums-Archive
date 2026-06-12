---
title: "Ubuntu 13.04 + WiFi-adapter USB TP-LINK TL-WN8200ND (RTL8192CU). How to connect?"
date: 2013-06-05
forum: Networking &amp; Wireless
---

### Post by AlekseyEii on 2013-06-05
All steps below didn't help me :-\
What else?

Adapter TP-LINK TL-WN8200ND 802.11n Wireless USB: [http://www.tp-linkru.com/products/details/?categoryid=215&model=TL-WN8200ND](http://www.tp-linkru.com/products/details/?categoryid=215&model=TL-WN8200ND)
Chipset RTL8192CU: [http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=277](http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=277)
OS Ubuntu 13.04 all updates installed
On another notebook with Win7 It works fine
It notebook already has internal WiFi, I bought this adapter to connect to another Wireless networks with low level signal

Ours device: Device 004: ID 2357:0100
```
lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 2357:0100
Bus 001 Device 003: ID 2232:1028
```

```
modprobe -c | grep -i 0bda | grep 8176
alias usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*in* rtl8192cu

```

It nothing says:
```
lsmod | grep "^rtl8\|^8"
```

These errors show when I tried to install drivers from Realtek's website. I cut list of unpacked file to short message.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=277&DownTypeID=3&GetDown=false&Downloads=true)
```
sudo /home/mwa/r/install.sh 
[sudo] password for mwa: 
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105.tar.gz
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/clean
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ieee80211.h
...
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/hal_init.c
clean
core
hal
ifcfg-wlan0
include
Kconfig
Makefile
os_dep
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105
wlan0dhcp
/home/mwa/r/install.sh: line 25: cd: clean: It isn't folder
Authentication requested [root] for make clean:
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
rm -fr Module.markers ; rm -fr modules.order
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8192c/usb ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8192c ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
Authentication requested [root] for make driver:
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.8.0-23-generic/build M=/home/mwa/r/driver  modules
make[1]: Enter in folder `/usr/src/linux-headers-3.8.0-23-generic'
  CC [M]  /home/mwa/r/driver/core/rtw_cmd.o
In file included from /home/mwa/r/driver/core/rtw_cmd.c:23:0:
/home/mwa/r/driver/include/osdep_service.h: In function «thread_enter»:
/home/mwa/r/driver/include/osdep_service.h:575:2: error: implicit declaration of function «daemonize» [-Werror=implicit-function-declaration]
cc1: Some warnings are treated as errors
make[2]: *** [/home/mwa/r/driver/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/mwa/r/driver] Error 2
make[1]: Exit form folder `/usr/src/linux-headers-3.8.0-23-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################

```

To blacklist added, reboot, It didn't help
```
blacklist rtl8192c_common
blacklist rtlwifi
blacklist rtl8192cu
```

---

### Post by ahallubuntu on 2013-06-05
~

---

### Post by AlekseyEii on 2013-06-12
I installed this package.
[LIST=1]
[*]nothing changes
[*]I can't find how to uninstall it ))
[/LIST]

> **ahallubuntu said:**
> Try the patch of this driver (post #9) or the Debian package in the post (#10) right below:

[http://ubuntuforums.org/showthread.php?t=2092934&p=12620866#post12620866](http://ubuntuforums.org/showthread.php?t=2092934&p=12620866#post12620866)

---

### Post by AlekseyEii on 2013-06-13
Maybe some good man gives an advice to me? What can I do else?

---

### Post by jordanroszmann on 2013-09-24
I struggled all day to get mine working, and in the end NDISwrapper worked for me in Ubuntu 12.04 LTS and Linux kernel 3.2.0, with i686 (32 bit) architecture

 I don't know if this will help you with Linux 13.04, but it seems possible, and I want to write down my steps because there seem to be many of us struggling to use this adapter with linux.
[B]
NOTE:  I do not fully understand (or remember) exactly what I did.  I will appreciate any corrections.
[/B]
The steps that worked for me: 
 
1)   Build and install ndiswrapper 1.58  (Version 1.57 from Synaptic did not work for me.)[INDENT]i) Download the tar.gz:  [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)[/INDENT]
[INDENT]ii) Use the terminal extract and then move the resulting folder to /usr/src: [/INDENT]
  ```

cd Downloads
tar -zxvf ndiswrapper-1.58.tar.gz
sudo mv ndiswrapper-1.58 /usr/src 
cd /usr/src/ndiswrapper
```[INDENT]iii) Build and install.[/INDENT]
```

make
make install
```

2) Install the ndiswrapper gui using the Software Center:[INDENT]"Windows Wireless Drivers" (Ndiswrapper driver installation tool)

[/INDENT]
3) Install the windows XP driver using the gui.[INDENT]i) Open "Windows Wireless Drivers"
ii) Click "Install New Driver
iii) I used the installation CD that came with the WN8200ND:[/INDENT]
[INDENT=2]CD166A2/TL-WN8200ND/Driver Files/Windows XP 32bit/netrtwlanu.inf[/INDENT]
[INDENT]iv) The window now says "Hardware present:Yes"
[/INDENT]

4) After rebooting the USB adapter is working.

I also have an integrated wireless adapter which I turned off by blacklisting its driver.

1) Find the driver:  The following command in the terminal shows the USB adapter with driver "ndiswrapper+netrtwlanu" and the integrated card with driver "b43".
```
  sudo lshw -c network 
```
2) blacklist the integrated driver[INDENT]i) Open the blacklist[/INDENT]
[INDENT]```
 sudo gedit /etc/modprobe.d/blacklist.conf 
```
ii) Add a line at the end (for me the driver name is b43):
blacklist b43[/INDENT]
3) reboot

           
Final notes:  Even with the ndiswrapper, lsusb does not identify the USB adapter by name.  A patch for this appears to be in the pipe, and it looks like full support is on the way eventually.

---

### Post by pete_moss2 on 2013-09-29
SOLUTION for 3.8 Kernel!

I had been fighting with this issue for days and found a patched version of Realtek's drivers wrapped up in a DEB for 3.8 & 3.9 kernels.

[https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/](https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/)

Please "sticky" this, or share this link on other topic-related forum threads so everyone dealing with this issue can find this patched driver!

---

### Post by MIJ-VI on 2013-09-30
Solution #2:

(Post #7) Realtek RTL8192CU Driver works under 13.10-beta2

[ubuntu] Realtek RTL8192CU Driver issues under 13.04
[http://ubuntuforums.org/showthread.php?t=2148130](http://ubuntuforums.org/showthread.php?t=2148130)

---

