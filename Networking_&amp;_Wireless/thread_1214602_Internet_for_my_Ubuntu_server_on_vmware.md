---
title: "Internet for my Ubuntu server on vmware"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by henkhenk_ on 2009-07-16
hi guys: 
 
- I have ubuntu server 6.10 runing on my vmware player on Host OS win xp sp3.
- Internet works fine on host OS
- Internet do now work on Ubuntu but ping works.
 
the following are some of my setting in diffrent files:
 
/etc/network/interfaces
**auto lo**
**iface lo inet loopback**
 
**auto eth0**
**iface eth inet dhcp**
 
**auto eth1**
**iface eth1 inet dhcp**
 
*ifconfig :*
**eth1 Link encap:Ethernet HWaddr 00:0C:..... **
**inet addr:192.16.... Bcast:192. Mask:255.255.255.0**
**inet6 addr: fe80::20c:29ff:......./64 Scope:Link**
**UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1**
**RX packets:136 errors:0 dropped:0 overruns:0 frame:0**
**TX packets:195 errors:0 dropped:0 overruns:0 carrier:0**
**collisions:0 txqueuelen:1000 **
**RX bytes:16583 (16.1 KiB) TX bytes:23040 (22.5 KiB)**
**Interrupt:177 Base address:0x1400 **
 
**lo Link encap:Local Loopback **
**inet addr:127.0.0.1 Mask:255.0.0.0**
**inet6 addr: ::1/128 Scope:Host**
**UP LOOPBACK RUNNING MTU:16436 Metric:1**
**RX packets:0 errors:0 dropped:0 overruns:0 frame:0**
**TX packets:0 errors:0 dropped:0 overruns:0 carrier:0**
**collisions:0 txqueuelen:0 **
**RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)**
 
etc/environment
**http_proxy = 10.28..... :80 #my host IP address**
**export "http_proxy"**
 
On Host PC I have the following setting:
**Windows IP Configuration**
 
**Host Name . . . . . . . . . . . . : xxxx**
**Primary Dns Suffix . . . . . . . : xxxxx**
**Node Type . . . . . . . . . . . . : Unknown**
**IP Routing Enabled. . . . . . . . : No**
**WINS Proxy Enabled. . . . . . . . : No**
**DNS Suffix Search List. . . . . . : xxxx**
 
**Ethernet adapter VMware Network Adapter VMnet8:**
 
**Connection-specific DNS Suffix . : **
**Description . . . . . . . . . . . : VMware Virtual Ethernet Adapter for VMnet8**
**Physical Address. . . . . . . . . : 00-50-56-xxxxx**
**Dhcp Enabled. . . . . . . . . . . : No**
**IP Address. . . . . . . . . . . . : 192.168.xxxxx**
**Subnet Mask . . . . . . . . . . . : 255.255.255.0**
**Default Gateway . . . . . . . . . : **
 
**Ethernet adapter VMware Network Adapter VMnet1:**
 
**Connection-specific DNS Suffix . : **
**Description . . . . . . . . . . . : VMware Virtual Ethernet Adapter for VMnet1**
**Physical Address. . . . . . . . . : 00-50-56-xxxxx**
**Dhcp Enabled. . . . . . . . . . . : Yes**
**Autoconfiguration Enabled . . . . : Yes**
**IP Address. . . . . . . . . . . . : 192.168.xxxx**
**Subnet Mask . . . . . . . . . . . : 255.255.255.0**
**Default Gateway . . . . . . . . . : **
**DHCP Server . . . . . . . . . . . : 192.168.xxxxx**
**Lease Obtained. . . . . . . . . . : 16 july 2009 11:31:16**
**Lease Expires . . . . . . . . . . : 16 july 2009 12:01:16**
 
**Ethernet adapter Local Area Connection:**
 
**Connection-specific DNS Suffix . : xxxxx**
**Description . . . . . . . . . . . : Intel(R) PRO/1000 CT Network Connection**
**Physical Address. . . . . . . . . : 00-30-xxxxxx**
**Dhcp Enabled. . . . . . . . . . . : Yes**
**Autoconfiguration Enabled . . . . : Yes**
**IP Address. . . . . . . . . . . . : 10.28.xxxxxx**
**Subnet Mask . . . . . . . . . . . : 255.255.255.0**
**Default Gateway . . . . . . . . . : 10.xxxxx**
**DHCP Server . . . . . . . . . . . : 10.28.1xxxxx**
**DNS Servers . . . . . . . . . . . : 10.28.xxxxx**
**10.28xxxxx**
**Lease Obtained. . . . . . . . . . : 16 july 2009 10:30:14**
**Lease Expires . . . . . . . . . . : 24 july 2009 10:30:14**
 
Please help... I have spend days already on this. and please ask if you need any more clarification.
 
henk;)

---

### Post by 696f6e6963 on 2009-07-16
When you say ping works - do you mean that you can ping other hosts or that other hosts can ping you?

---

### Post by henkhenk_ on 2009-07-16
> **696f6e6963 said:**
> When you say ping works - do you mean that you can ping other hosts or that other hosts can ping you?
 
I can ping my host IP address and I can ping other IP or URLs too. and I can ping also from the host to the vmwere.

---

### Post by henkhenk_ on 2009-07-16
I have some more info to add.
 
I have a proxy server also, and on the seting it needs the proxy address. but I couldnt find the proxy address because it is configured to use an automatic configuration script.
 
does any one know how to get a proxy address from the automatic confguration script? like I can see the script if I open it with my web browser.
 
tanks
henk

---

### Post by henkhenk_ on 2009-07-16
> **henkhenk_ said:**
> I have some more info to add.
 
I have a proxy server also, and on the seting it needs the proxy address. but I couldnt find the proxy address because it is configured to use an automatic configuration script.
 
does any one know how to get a proxy address from the automatic confguration script? like I can see the script if I open it with my web browser.
 
tanks
henk
 
so now when I try to conect to the net like with the following comand
 
links [www.google.com]("http://www.google.com")
 
it show the following error:
 
Unable to retrive proxy://10.28.xx.xx:80/http://www.google.com/:
Error reading from socket

---

