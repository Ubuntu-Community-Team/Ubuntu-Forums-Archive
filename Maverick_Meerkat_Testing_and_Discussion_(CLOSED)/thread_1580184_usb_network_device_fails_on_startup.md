---
title: "usb network device fails on startup"
date: 2010-09-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by odror on 2010-09-23
I have a usb network device that does not function when the system starts, but as soon as I unplug then plug the device it works fine. (unplugging/plunging) the Ethernet cable does not help.

Apparently after reboot it is not able to get an IP address from the DHCP server.

restarting the device by software 
(i.e.
> ifdown eth0; 
modprobe -r module asix
modprobe module asix
ifup eth0
) does not help. As soon as I unplug and then plug the device I am able to get a network address and use the device.

ifconfig before unplugging:

> eth0 Link encap:Ethernet HWaddr 00:50:b6:07:dc:41
inet6 addr: fe80::250:b6ff:fe07:dc41/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:694602 errors:717008 dropped:0 overruns:0 frame:0
TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:48 (48.0 B) TX bytes:4539 (4.5 KB)

after plugging back:

> eth0 Link encap:Ethernet HWaddr 00:50:b6:07:dc:41
inet addr:192.168.0.62 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::250:b6ff:fe07:dc41/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:39 errors:0 dropped:0 overruns:0 frame:0
TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2910 (2.9 KB) TX bytes:11875 (11.8 KB)

OS version: Ubuntu 10.10 64bit
Hardware: usb network adaptor Trendnet tu2-et100

Thanks

---

### Post by dino99 on 2010-09-23
look at logs, you might find some usefull errors

sudo update-usbids && sudo update-pciids

---

### Post by odror on 2010-09-24
> **dino99 said:**
> look at logs, you might find some usefull errors

sudo update-usbids && sudo update-pciids

I tried that it did not help.

No error in /var/log/message

---

### Post by odror on 2010-09-26
I have a usb ethernet device (using **asix **kernel module) (OS 10.10 64 bit)

After booting it is not able to retrieve the IP address from the server.

ifconfig:
> eth0 Link encap:Ethernet HWaddr 00:50:b6:07:dc:41
inet6 addr: fe80::250:b6ff:fe07:dc41/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:694602 errors:717008 dropped:0 overruns:0 frame:0
TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:48 (48.0 B) TX bytes:4539 (4.5 KB) 

I have to unplug and plug the device (after boot) to make it work. The ifconfig is then

> eth0 Link encap:Ethernet HWaddr 00:50:b6:07:dc:41
inet addr:192.168.0.62 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::250:b6ff:fe07:dc41/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:39 errors:0 dropped:0 overruns:0 frame:0
TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2910 (2.9 KB) TX bytes:11875 (11.8 KB) 

When I try to emulate the plugging/unplugging by software.
i.e:
> ifdown eth0;
modprobe -r module asix
modprobe module asix
ifup eth0 

It does not work

Is there a way to debug this problem. Is there a different way of unplgging/plugging the device by software instead physically doing it.

Thanks

---

### Post by cariboo on 2010-09-26
Please don't create multiple threads on the same subject, I have merged your two threads.

If your thread falls off the front page, it is OK to bump it after 24 hours has elapsed.

---

