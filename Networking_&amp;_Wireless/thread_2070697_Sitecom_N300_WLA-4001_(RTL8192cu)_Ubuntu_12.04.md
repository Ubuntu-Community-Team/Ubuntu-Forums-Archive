---
title: "Sitecom N300 WLA-4001 (RTL8192cu) Ubuntu 12.04"
date: 2012-10-13
forum: Networking &amp; Wireless
---

### Post by daud566 on 2012-10-13
Hey guyz,

I just bought a sitecom N300 wireless USB adapter, WLA-4001 and couldn't get it to work on my ubuntu 12.04 LTS 64bit(kernel 3.2.0-31) til now. The output from my lsusb is as follows;
```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0df6:0061 Sitecom Europe B.V.
Bus 004 Device 002: ID 04ca:002f Lite-On Technology Corp. 
Bus 004 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
```

Now i did some checking around to see which chipset it uses and on the windows installation CD it came with, indicated that it was realtek RTL8192cu, USB\VID_0DF6&PID_0061. 
It worked very well on WINXP so i figured it wasn't a hardware problem. 

I had tried the following procedure to install it got from [http://ubuntuforums.org/showthread.php?t=1972694](http://ubuntuforums.org/showthread.php?t=1972694) since they use similar drivers. This is the procedure i used:
```
// i disconnected the usb card & ran this command:
sudo gedit /etc/udev/rules.d/network_drivers.rules 

//And added this line to the file (which was empty) and saved:

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0df6 0061", ATTR{idProduct}=="0061", RUN+="/sbin/modprobe -qba rtl8192cu"

//Then ran this command:
sudo gedit /etc/modprobe.d/network_drivers.conf 

// And added this file (and saved)
install rtl8192cu /sbin/modprobe --ignore-install rtl8192cu $CMDLINE_OPTS; /bin/echo "0df6 0061" > /sys/bus/usb/drivers/rtl819cu/new_id

// Finally, i download this file:
[http://anonscm.debian.org/viewvc/kernel/dists/trunk/firmware-nonfree/realtek/rtlwifi/rtl8192cufw.bin?revision=17442&view=co&pathrev=19436](http://anonscm.debian.org/viewvc/kernel/dists/trunk/firmware-nonfree/realtek/rtlwifi/rtl8192cufw.bin?revision=17442&view=co&pathrev=19436)

// Then created this directory
sudo mkdir directory /lib/firmware/RTL8192CU/
//and copied the dowloaded file to that directory(/lib/firmware/RTL8192CU/)
// Everything ran correctly upto this point.

```

Then ran 
```
sudo modprobe rtl8192cu 
```
which ran okay. I then restarted the machine. Now, the card could detect wireless connections but couldn't connect to them so i didn't understand what was happening.
I further probed with iwconfig and dmesg and this is what i got
```
iwconfig

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated Tx-   Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
```

```
dmesg | grep 8192

[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88022fc00000 s83136 r8192 d23360 u262144
[    0.000000] pcpu-alloc: s83136 r8192 d23360 u262144 alloc=1*2097152
[   12.120114] rtl8192cu: MAC address: 00:0c:f6:ef:e7:c5
[   12.120119] rtl8192cu: Board Type 0
[   12.193078] usbcore: registered new interface driver rtl8192cu
[   14.647935] rtl8192cu: MAC auto ON okay!
[   14.681940] rtl8192cu: Tx queue select: 0x05
[   14.682700] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
```

So as at this point i'm stuck and would greatly appreciate your help. Maybe i'm missing something so obvious. Thanks in advance.

---

### Post by chili555 on 2012-10-13
I can refer you to many threads with the exact same problem with rtl8192cu: it sees networks but won't connect. You can jump to the conclusion here: [http://ubuntuforums.org/showpost.php?p=12291112&postcount=130](http://ubuntuforums.org/showpost.php?p=12291112&postcount=130)

If you need some additional guidance, please post back.

---

### Post by daud566 on 2012-10-17
thanks chili555. Mine is 64 bit ubuntu 12.04 so which arch code should i use?

---

### Post by chili555 on 2012-10-17
I've attached the files you need. Please post back if you need some assistance installing.

---

