---
title: "Windows Mobile Phone disconnects Wireless Network?"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by dgaud on 2010-05-19
Hello,
I've read a lot info here and on the internet, but so far nobody's described my strange problem. Is there any reason why when my phone is connected to the PC (HTC FUZE) as a Storage Device (WM5 Storage, USB 2 PC) or thru SYNCE, the network connection is lost immediately and I cant use my wireless device? I'm using a D-LINK 2340 USB adapter and Wicd. I did the usual and lsusb shows the D-LINK adapter connected, ndiswrapper says the driver is loaded and the device present and lshw shows only wlan0 as the network adapter.
At this point I'm almost convinced I have a problem with the USB ports on my PC. Anyway, in case somebody has seen this before. Thanks,

---

### Post by alexfish on 2010-05-19
hi

it is possible if the device has more than one control port

can you post the results of this command from the terminal 

Code:

dmesg | grep -e "modem" -e "tty"

and

ls -al /dev/ttyU*

---

### Post by dgaud on 2010-05-19
Here is the output of:
dmesg | grep -e "modem" -e "tty"
```
[    0.000000] console [tty0] enabled
[    0.725647] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.726152] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```

Here is the output of:
ls -al /dev/ttyU*:
```
ls: cannot access /dev/ttyU*: No such file or directory
```

This is lshw -C Network right after I CONNECT the phone:
```
  *-network               
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:1e:58:97:92:4f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+neta5agu driverversion=1.55+D-Link,05/08/2006,1.5.202.2 ip=192.168.1.110 multicast=yes wireless=IEEE 802.11g
```

This is lshw -C Network right after I DISCONNECT the phone:
```
  *-network               
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1e:58:97:92:4f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+neta5agu driverversion=1.55+D-Link,05/08/2006,1.5.202.2 ip=192.168.1.110 multicast=yes wireless=IEEE 802.11g
```

Most of the time it comes back by itself after a while. Sometimes I have to completely shutdown the PC. If you try to disconnect / reconnect with Wicd, it just says **Connection Failed: Bad Password** every time. 

Thanks for the help.

---

