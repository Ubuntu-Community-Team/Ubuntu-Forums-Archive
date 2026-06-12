---
title: "Ubuntu 10.04 Kernel 3.2.5 Realtek RTL8188S WLAN Adapter doesn't work"
date: 2012-12-26
forum: Networking &amp; Wireless
---

### Post by gsedsd on 2012-12-26
Ubuntu 10.04 with kernal 3.2.5. I have an issue with which I've been struggling for 3 days. The problem with my wifi usb device (Realtek RTL8188S WLAN Adapter). It doesn't work properly. Actually, it doesn't work at all. I can't figure out why.
When I call ifconfig up, I'm getting the error below

```

root@kiosk:/etc/apt# sudo ifconfig wlan1 up
SIOCSIFFLAGS: Operation not permitted

```from syslog I got this

```

Dec 26 09:50:30 kiosk kernel: [ 1056.833471] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
Dec 26 09:50:30 kiosk kernel: [ 1056.834616] r8712u: Unable to load firmware
Dec 26 09:50:30 kiosk kernel: [ 1056.834618] r8712u: Install latest linux-firmware

```I checked the packet manager and it says that I've already have the latest linux-firmware on my computer. However, there is no rtl8712u.bin file in /lib/firmware/rtlwife directory. How can I get it? The installation of drivers from realtek site creates completely different files there. 

additional information:

```

root@kiosk:/etc/apt# iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

wlan1     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````

root@kiosk:/etc/apt# cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"

``````

root@kiosk:/etc/apt# uname -r
3.2.5-030205-generic

``````
55: USB 00.0: 0282 WLAN controller
  [Created at usb.122]
  Unique ID: lX5h.USeKJTMSyaA
  Parent ID: FKGF.4Nx_qoDfSd7
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0
  SysFS BusID: 2-1.4:1.0
  Hardware Class: network
  Model: "Realtek RTL8188S WLAN Adapter"
  Hotplug: USB
  Vendor: usb 0x0bda "Realtek Semiconductor Corp."
  Device: usb 0x8171 "RTL8188S WLAN Adapter"
  Revision: "2.00"
  Serial ID: "00e04c000001"
  Driver: "r8712u"
  Driver Modules: "r8712u"
  Device File: wlan1
  Features: WLAN
  Speed: 480 Mbps
  HW Address: 08:10:76:1d:c3:b5
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13 14
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457
```

```

admin@kiosk:/lib/firmware/rtlwifi$ ls
Realtek-Firmware-License.txt  rtl8192defw_12.bin   rtl8723fw_B.bin
rtl8192cfw.bin                rtl8192defw.bin      rtl8723fw.bin
rtl8192cfwU_B.bin             rtl8192sefw.bin
rtl8192cfwU.bin               rtl8192sefw.old.bin

```

---

### Post by ahallubuntu on 2012-12-26
Download the driver from here:

[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

and build it in a terminal.  There is probably a "Readme" file in the root directory of the downloaded driver (after you unzip it) with separate instructions for older and newer kernels.

---

### Post by gsedsd on 2012-12-26
I've already tried all drivers from this page

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU)

Many of them doesn't build since kernel version is different.

This one was succesfully installed
```
RTL8192SE Linux driver for kernel 2.6.24 (and later, up to 3.2.x)	0005.1230.2011
```

Didn't solve my problem.

---

### Post by gsedsd on 2012-12-26
Moreover, I tried to add 8712u driver to blacklist /etc/modprobe.d/blacklist.conf

It made the situation even worse. Device disappeared from iwconfig and all GUI controls as well.

I assume that my issue related to this one - [https://bugs.archlinux.org/task/27996](https://bugs.archlinux.org/task/27996). But it's for archlinux, so I'm not sure.

---

### Post by gsedsd on 2012-12-26
up, really need to solve this problem

---

### Post by hans75 on 2013-02-16
Is there a solution? I have exactly the same problem. Also 10.04LTE ant the LogiLinkWL0085 with the rtl8188S Chip.

---

