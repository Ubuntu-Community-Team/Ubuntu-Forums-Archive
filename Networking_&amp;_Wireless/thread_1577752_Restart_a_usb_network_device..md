---
title: "Restart a usb network device."
date: 2010-09-19
forum: Networking &amp; Wireless
---

### Post by odror on 2010-09-19
Hi,

I have a usb network device that does not function when the system starts, but as soon as I unplug then plug the device it works fine. (unplugging/plunging) the Ethernet cable does not help.

Apparently after reboot it is not able to get an IP address from the DHCP server. 

restarting the device by software (i.e. ifdown eth0; ifup eth0) does not help. As soon as I unplug and then plug the device I am able to get a network address and use the device.

Is there a way to fix it or a work around the problem.
is there a way to do the operation of plunging/unplugging by software.

OS version: Ubuntu 10.10
Hardware: usb network adaptor Trendnet tu2-et100

ifconfig before unplugging:
> eth0      Link encap:Ethernet  HWaddr 00:50:b6:07:dc:41  
          inet6 addr: fe80::250:b6ff:fe07:dc41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:694602 errors:717008 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48 (48.0 B)  TX bytes:4539 (4.5 KB)



after plugging back:
> eth0      Link encap:Ethernet  HWaddr 00:50:b6:07:dc:41  
          inet addr:192.168.0.62  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:b6ff:fe07:dc41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2910 (2.9 KB)  TX bytes:11875 (11.8 KB)



Thanks for any help.

---

### Post by mikewhatever on 2010-09-19
Bring it down first with ifdown, then reload the module with modprobe.

ifdown device-name
modprobe -r module name #removes module
modprobe module-name #loads module
ifup device-name

---

### Post by odror on 2010-09-19
I am not sure what is the module name I think it is **usbnet**.

Whem I do that

> ifdown eth0
modprobe -vr usbnet

I get the following error:

**FATAL: Module usbnet is in use.**

Am I using the wrong module name or there is something else that uses this module that I do not know.

-Thanks

---

### Post by mikewhatever on 2010-09-19
Are you sure eth0 is the right interface? While that usb device is working, what's the output of ifconfig?

---

### Post by odror on 2010-09-19
while the device is working the ifconfig for eth0 is:
> eth0      Link encap:Ethernet  HWaddr 00:50:b6:07:dc:41  
          inet addr:76.93.6.148  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: fe80::250:b6ff:fe07:dc41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:467 errors:0 dropped:0 overruns:0 frame:0
          TX packets:270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:320859 (320.8 KB)  TX bytes:51960 (51.9 KB)


and when it is not working it is:
> eth0      Link encap:Ethernet  HWaddr 00:50:b6:07:dc:41  
          inet6 addr: fe80::250:b6ff:fe07:dc41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:848 (848.0 B)  TX bytes:5722 (5.7 KB)


---

### Post by mikewhatever on 2010-09-19
Odd indeed. Usually, eth0 is the ethernet. Anyway, the second part of the output shows that eth0, although disconnected, is not down, as it should have disappeared completely.
What happens if you use **sudo ifconfig eth0 down/up** instead if ifdown/up eth0?

---

### Post by odror on 2010-09-19
using eth0 up/down does not solve the error message with 

 modprobe -vr usbnet

is usbnet the correct kernel module? is there a different module?

-Oz

---

### Post by mikewhatever on 2010-09-19
Each device has its own module. Why did you think 'usbnet' was the one in the first place?

---

### Post by odror on 2010-09-19
ok the module name that I need to use is **asix**
which is dependednt on **usbnet**. So when it is unloaded from the kernel **usbnet **is also unloaded.

But doing all of that does not solve the problem. It is not the equivalent of plugging and unplugging the USB network device.


-Oz

---

