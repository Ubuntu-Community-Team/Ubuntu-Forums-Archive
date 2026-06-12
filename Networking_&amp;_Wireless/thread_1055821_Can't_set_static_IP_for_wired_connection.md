---
title: "Can't set static IP for wired connection"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by Zalbor on 2009-01-31
Hello, I'm using Kubuntu 8.10.
My computer is connected to my router via ethernet, and I want to set a static IP for it like I always do. So I clicked on the taskbar icon and configured a new connection on the eth0 device, setting its IP to 192.168.1.2.
Then I noticed that my port forwarding wasn't working correctly. Checking ifconfig, it says my IP is 192.168.1.5, which says to me that it got its IP from my router's DHCP (its pool starts at .1.3, and .1.3 and .1.4 are used by other devices).
Clicking on the icon again and then on the connection I set up seems to be doing absolutely nothing.

Can someone tell me what I'm doing wrong, and how to set my computer's IP to .1.2?

---

### Post by Iowan on 2009-01-31
Check/post contents of */etc/network/interfaces* file.  It may also be necessary to disable **dhclient**.

---

### Post by Zalbor on 2009-02-10
Sorry for the delay...
The interfaces file is as follows:
```
auto lo
iface lo inet loopback
```

I don't really know what to do with it...

---

### Post by DiGiTGOD on 2009-02-10
how about adding something like this

```
auto eth0
iface eth0 inet static
        address 192.168.1.71
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```

then do 
```
sudo /etc/init.d/networking restart
```

Let me know if it helps... and remember to change the values to something that is meaningful to your network...

---

### Post by Zalbor on 2009-02-10
That seems to have worked, thanks!

Can you maybe also tell me how to do it for a wireless network? I also need that (on another computer) to use static IP, but I also have to set its WPA key etc...

---

