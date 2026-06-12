---
title: "Wireless adapter not showing"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by mmeisam on 2009-04-09
Hello,

I have searched all over for the answer to this problem and i have found a few threads on other forums but none of them have an answer. 

So i bought this no name USB wireless adapter and it came with a CD with the drivers on it. So i install Ndiswrapper and get the .inf installed with no errors during the installation of the drivers. 

From what i understand after installing the drivers i should see wlan0 when i run ifconfig, but that doesnt show up. I know for a fact that it is plugged in and ubuntu can see the adapter but it doesnt do anything. Any help will be appreciated.

```
root@meisam-desktop:/home/meisam# lsusb
Bus 005 Device 005: ID 0416:0035 Winbond Electronics Corp. W89C35 802.11bg WLAN Adapter
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 046d:c309 Logitech, Inc. Internet Keyboard
Bus 002 Device 005: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 041e:400d Creative Technology, Ltd WebCam PD1001
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
root@meisam-desktop:/home/meisam# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0e:a6:49:ee:2a  
          inet addr:70.79.98.236  Bcast:70.79.99.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:68031 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10988501 (10.9 MB)  TX bytes:1504213 (1.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

pan0      Link encap:Ethernet  HWaddr 66:dc:86:9b:0d:6c  
          inet6 addr: fe80::64dc:86ff:fe9b:d6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)

```

---

### Post by Ayuthia on 2009-04-09
Can you post the results of:
```
ndiswrapper -l
lsmod|grep ndiswrapper
dmesg|grep ndiswrapper
```

---

### Post by mmeisam on 2009-04-12
```
root@meisam-desktop:/home/meisam# ndiswrapper -l
dm9usb : driver installed
	device (0416:0035) present
```

```
root@meisam-desktop:/home/meisam# lsmod|grep ndiswrapper
ndiswrapper           196380  0 
usbcore               149488  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
```

```
root@meisam-desktop:/home/meisam# dmesg|grep ndiswrapper
[  253.434017] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  253.997099] ndiswrapper: driver dm9usb (SHANTOU., Inc.,03/12/2002, 1.90.0312.2002) loaded
[  254.000381] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[  254.000398] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[  254.000420] ndiswrapper (mp_halt:262): device de7c2480 is not initialized - not halting
[  254.000427] ndiswrapper: device eth%d removed
[  254.009093] ndiswrapper: probe of 5-7:1.0 failed with error -22
[  254.018653] usbcore: registered new interface driver ndiswrapper


```

---

### Post by Ayuthia on 2009-04-13
Based on the results in dmesg, ndiswrapper does not seem to like that driver.  You will most likely need to find another driver.

---

