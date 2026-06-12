---
title: "No network devices have been found"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by andy@linux on 2009-09-23
I just installed ubuntu-9.04 on my box which has Windows Vista installed also. But when entering ubuntu, Network Manager says "No network devices have been found". I tried using Ubuntu and fedora livecd but the same problem occurred. However, it works under Vista.

By using lspci and dmesg, there is no information about the network adapter. It seems that Ubuntu has not found the hardware.

Any idea?

Info:
OS: Ubuntu-9.04 Desktop
Kernel: 2.6.28-11-generic
Network Adapter: Intel 82578DM Gigabit Network Connection

---

### Post by tgeer43 on 2009-09-23
Very rare to get zero results from Google but that's what I get when using the search term "Intel 82578DM Ubuntu".

But from what I can gather, you need the e1000e Linux driver for this network adapter which can be found here:

_[COLOR=Blue][http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&keyword=%22e1000-%22](http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&keyword=%22e1000-%22)[/COLOR]_

tgeer

---

### Post by andy@linux on 2009-09-23
> **tgeer43 said:**
> Very rare to get zero results from Google but that's what I get when using the search term "Intel 82578DM Ubuntu".

But from what I can gather, you need the e1000e Linux driver for this network adapter which can be found here:

_[COLOR=Blue][http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&keyword=%22e1000-%22](http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&keyword=%22e1000-%22)[/COLOR]_

tgeer

Acctually I have e1000e driver on my distibution. See below
```
root@u9-desktop:/lib/modules/2.6.28-11-generic# ls kernel/drivers/net/e* -l
-rw-r--r-- 1 root root 55504 2009-04-17 11:42 kernel/drivers/net/e100.ko
-rw-r--r-- 1 root root 17356 2009-04-17 11:42 kernel/drivers/net/e2100.ko
-rw-r--r-- 1 root root 51064 2009-04-17 11:42 kernel/drivers/net/eepro100.ko
-rw-r--r-- 1 root root 26420 2009-04-17 11:42 kernel/drivers/net/eepro.ko
-rw-r--r-- 1 root root 28176 2009-04-17 11:42 kernel/drivers/net/eexpress.ko
-rw-r--r-- 1 root root 34504 2009-04-17 11:42 kernel/drivers/net/epic100.ko
-rw-r--r-- 1 root root 16960 2009-04-17 11:42 kernel/drivers/net/eql.ko
-rw-r--r-- 1 root root 16944 2009-04-17 11:42 kernel/drivers/net/es3210.ko
-rw-r--r-- 1 root root 24656 2009-04-17 11:42 kernel/drivers/net/eth16i.ko
-rw-r--r-- 1 root root 29644 2009-04-17 11:42 kernel/drivers/net/ewrk3.ko

kernel/drivers/net/e1000:
total 156
-rw-r--r-- 1 root root 159160 2009-04-17 11:42 e1000.ko

kernel/drivers/net/e1000e:
total 144
-rw-r--r-- 1 root root 146284 2009-04-17 11:42 e1000e.ko

kernel/drivers/net/enic:
total 60
-rw-r--r-- 1 root root 58180 2009-04-17 11:42 enic.ko
```I tried
```
demsg| grep -i network
```I can see the driver is loaded.
However, there is still no eth0 in ifconfig.

```
root@u9-desktop:/lib/modules/2.6.28-11-generic# ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr 1a:11:07:d5:b6:99  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```

---

### Post by andy@linux on 2009-09-24
The problem has been solved after I install Ubuntu 9.10 Alpha 6. The NIC is working.
However, a new problem is that the new OS often goes to be halted and unresponsive. I am not sure whether it is a problem from OS or my hardware.

---

