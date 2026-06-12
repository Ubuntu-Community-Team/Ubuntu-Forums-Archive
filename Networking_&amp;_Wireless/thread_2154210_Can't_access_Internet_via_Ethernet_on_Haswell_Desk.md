---
title: "Can't access Internet via Ethernet on Haswell Desktop"
date: 2013-06-13
forum: Networking &amp; Wireless
---

### Post by Stephen Vincent on 2013-06-13
(Sorry I've tried suggestions made in related threads but no joy)

I have a new desktop (Haswell i5-4430 with Asrock Z87 Pro3 motherboard) on which I've installed Ubuntu 12.04.02. However the Ethernet connection doesn't seem to be recognized: attempts to enable networking result in the error message "Network disconnected - you are now offline". The hardware was tested on a Windows system before I got it and Ethernet was working.

Any help would be much appreciated.

 Some diagnostics:

[COLOR=#ff0000]cat /etc/network/interfaces[/COLOR]
auto lo
iface lo inet loopback
iface eth0 inet dynamic


[COLOR=#ff0000]ifconfig -a[/COLOR]
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr ee:0a:87:0b:aa:60  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


[COLOR=#ff0000]lshw -class network[/COLOR]
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ee:0a:87:0b:aa:60
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A 
multicast=yes

---

### Post by chili555 on 2013-06-14
> cat /etc/network/interfaces
auto lo
iface lo inet loopback
iface eth0 inet dynamic

Please open a terminal and do:```
gksudo gedit /etc/network/interfaces
```Comment out the incorrect line:```
auto lo
iface lo inet loopback
**#**iface eth0 inet dynamic
```Proofread, save and close gedit. Reboot. Now, again in a terminal, let's gather some information:```
lspci -nn | grep 0200
dmesg | grep e100
```Please post the result.

---

### Post by Stephen Vincent on 2013-06-14
Tx, chili555.

After commenting out the suggested line in /etc/network/interfaces. the output of those commands is:

$ lspci -nn | grep 0200
00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:153b] (rev 04)
$ dmesg | grep e100
$

---

### Post by chili555 on 2013-06-14
> Ethernet controller [0200]: Intel Corporation Device [8086:153b] (rev 04)Your device is claimed by the driver e1000e, let's do some checking:```
modinfo e1000e | grep 153B
sudo modprobe e1000e
dmesg | grep e100
```

---

### Post by Stephen Vincent on 2013-06-14
$ modinfo e1000e | grep 153B
$ sudo modprobe e1000e
$ dmesg | grep e100
[16102.093168] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[16102.093169] e1000e: Copyright (c) 1999-2008 Intel Corporation.

---

### Post by chili555 on 2013-06-14
>  modinfo e1000e | grep 153BWhen it comes back empty, that tells us the device ID isn't listed in the Ubuntu version you installed, 12.04 LTS. You could install Ubuntu 13.04 and be all set. You could compile and install the latest version of e1000e. That requires several prerequisites that are very difficult to install without a working internet connection.

Do you have or can you borrow a working wireless device?

---

### Post by Stephen Vincent on 2013-06-14
> **chili555 said:**
> When it comes back empty, that tells us the device ID isn't listed in the Ubuntu version you installed, 12.04 LTS. You could install Ubuntu 13.04 and be all set. You could compile and install the latest version of e1000e. That requires several prerequisites that are very difficult to install without a working internet connection.

Do you have or can you borrow a working wireless device?

I'll try installing 13.04: looks like the most attractive option. Thanks for the help.

---

### Post by Stephen Vincent on 2013-06-15
Upgrading to 13.04 did the trick! Thanks again.

---

