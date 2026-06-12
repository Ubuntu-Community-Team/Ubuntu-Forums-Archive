---
title: "Help networking openmoko freerunner"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by bennybobw on 2009-04-18
So I just got a new openmoko freerunner, but am having trouble sshing into it from my Ubuntu 8.10 (recently upgraded from Hardy). I followed the instructions here: 
[http://wiki.openmoko.org/wiki/USB_Networking#Debian.2C_Ubuntu_and_others](http://wiki.openmoko.org/wiki/USB_Networking#Debian.2C_Ubuntu_and_others)

Here is my /etc/network/interfaces
```

iface lo inet loopback

# freerunner
allow-hotplug usb0
 iface usb0 inet static
 address 192.168.0.200
 netmask 255.255.255.192
 post-up /etc/network/freerunner start
 pre-down /etc/network/freerunner stop

```

The code for /etc/network/freerunner.sh is in the page above.

Per one users instructions I installed wicd because I was having trouble with the network manager hijacking the connection.

Has anyone had any luck connecting 
But when I ping -I usb0 192.168.0.202 I get
> 
From 10.0.1.198 icmp_seq=1 Destination Host Unreachable

Has anyone had any success working through this?

Thanks :D

---

### Post by bennybobw on 2009-04-18
So I restarted my computer with the freerunner connected and it works. I'll post tomorrow with more details.

---

### Post by bennybobw on 2009-04-19
OK so I flashed the freerunner with android, and now I simply cannot connect via usb again. I've tried restarting the computer with the device connected as well as starting up the phone while it was connected via usb.

sudo ifup usb0 gives me
> 
usb0: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device


My settings are the same as they were before...

---

