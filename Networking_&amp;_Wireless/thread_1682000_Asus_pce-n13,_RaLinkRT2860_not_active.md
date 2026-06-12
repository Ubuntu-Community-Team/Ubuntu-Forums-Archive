---
title: "Asus pce-n13, RaLink/RT2860 not active"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by kc7rwx on 2011-02-05
Just built a new computer and I think I somehow need to activate my wireless card to get it working.

The hardware seems to show up.  I get "Wireless Networks" in my network manager but it is grayed out and says disconnected.

I think it is an easy fix I just cannot find it.

Thanks for any help you can provide. 

Here is some diagnostic. 

```
~$ hwinfo --wlan
> hal.1: read hal dataprocess 2841: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
34: PCI 500.0: 0282 WLAN controller                             
  [Created at pci.318]
  Unique ID: y9sn.1pkKwSYwma0
  Parent ID: bSAa.q_6W8Iijw6D
  SysFS ID: /devices/pci0000:00/0000:00:0a.0/0000:05:00.0
  SysFS BusID: 0000:05:00.0
  Hardware Class: network
  Model: "RaLink RT2860"
  Vendor: pci 0x1814 "RaLink"
  Device: pci 0x0781 "RT2860"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x130f 
  Driver: "rt2800pci"
  Driver Modules: "rt2800pci"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xfe4f0000-0xfe4fffff (rw,non-prefetchable)
  IRQ: 47 (no events)
  HW Address: 70:71:bc:df:df:2a
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13 14
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472 2.484
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v00001814d00000781sv00001043sd0000130Fbc02sc80i00"
  Driver Info #0:
    Driver Status: rt2800pci is active
    Driver Activation Cmd: "modprobe rt2800pci"
  Driver Info #1:
    Driver Status: rt2860sta is active
    Driver Activation Cmd: "modprobe rt2860sta"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #7 (PCI bridge)

```

```
~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

usb0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

```
$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 6c:62:6d:59:6a:d3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:81 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 6c:62:6d:59:6a:d5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:83 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

usb0      Link encap:Ethernet  HWaddr 2a:ad:c0:fb:b7:a4  
          inet addr:192.168.42.164  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::28ad:c0ff:fefb:b7a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15872 errors:5 dropped:0 overruns:0 frame:5
          TX packets:14017 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10031617 (10.0 MB)  TX bytes:3480538 (3.4 MB)

```

---

### Post by kc7rwx on 2011-02-05
Quick note:
This wireless card works right from boot with Knoppix.

---

### Post by kc7rwx on 2011-02-05
Still struggling with this.
I came up with some new info today.

```
~$ ifconfig wlan0 up
SIOCSIFFLAGS: Permission denied

```

Don't have any idea what this means.

```
~$ iwlist wlan0 power 
wlan0     Current mode:off
```

It is a pcie card it does not have a power switch.

Any thoughts?

---

### Post by kc7rwx on 2011-02-05
I meant to run it with sudo but still no good

```
~$ sudo ifconfig wlan0 up
 
SIOCSIFFLAGS: Device or resource busy

```

---

### Post by kc7rwx on 2011-02-05
Found my solution in this bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/594866](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/594866)

added:
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib

to /etc/modprobe.d/blacklist.conf, than reboot


Everything is working fine now.

---

