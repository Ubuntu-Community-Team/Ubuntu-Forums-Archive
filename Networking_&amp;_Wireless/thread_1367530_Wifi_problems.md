---
title: "Wifi problems"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by Nkosinathi on 2009-12-29
Hi everyone, I have wifi problems on Ubuntu. I have installed the same type of card in another computer and there was no problem. The card uses a 3DSP USB driver and on the other computer it uses a Ralink RT2500 driver. 

I have tried to install the rt2500 driver on windows but it would work so I'm stuck with the 3DSP USB driver and I can't fingure how to troubleshoot it. Please help me on troubleshooting the wireless issue 

my ifconfig shows 

```
userxp@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:12:37:14:94  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:12ff:fe37:1494/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16553 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14719 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20398107 (20.3 MB)  TX bytes:1667502 (1.6 MB)
          Interrupt:26 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

userxp@ubuntu:~$ 
```My iwconfig shows

```

userxp@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

userxp@ubuntu:~$ 
```Here is my lspci output

```
userxp@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
userxp@ubuntu:~$ 


```Here is my lsusb output

```
userxp@ubuntu:~$ lsusb
Bus 001 Device 004: ID 05e1:0100 Syntek Semiconductor Co., Ltd 
Bus 001 Device 003: ID 0984:0060 Apricorn 
Bus 001 Device 002: ID 0c45:6310 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
userxp@ubuntu:~$ 
```lshw -C Network shows 

```

userxp@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:24:12:37:14:94
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.4 latency=0 multicast=yes
       resources: irq:26 ioport:ec00(size=256) memory:febff000-febfffff memory:febc0000-febdffff(prefetchable)
userxp@ubuntu:~$ 

```

---

### Post by Nkosinathi on 2009-12-31
bump

---

### Post by PaulReaver on 2010-04-05
try [[SIZE="2"][COLOR="Blue"]here[/COLOR][/SIZE]]("ftp://3dsp_lpkt_usb@3dsp.com.cn/")

---

### Post by PaulReaver on 2010-04-05
That is the ftp site for 3dsp. on there you should find up to date drivers for windows, ubuntu, fedora, debian and some not so up to date for suse.

I wish someone would redo the 3dsp drivers as they dont work with network manager,  it comes with "wifi radar".

If anyone wants the source code you can find it [[COLOR="Blue"]here[/COLOR]]("http://www1021.megaupload.com/files/7edeb19427074f012f482f2a500d555a/BlueW-2310U_2.0.0.rar") on megaupload.

---

