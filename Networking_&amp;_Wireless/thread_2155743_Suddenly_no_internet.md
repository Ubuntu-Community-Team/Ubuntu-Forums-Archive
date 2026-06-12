---
title: "Suddenly no internet"
date: 2013-06-19
forum: Networking &amp; Wireless
---

### Post by makamba on 2013-06-19
Hi,

Because I had bad sectors on my home drive I decided to move it using [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving). Now that I get everything more or less working again, I noticed I don't have internet. How comes? And more important, what can I do to remedy that?

TIA,
Makamba

---

### Post by 2F4U on 2013-06-19
How do you usually connect to the internet (wireless, wired)? Do you use a router, dial-up or something else? If there is a router, can you ping it?

---

### Post by makamba on 2013-06-19
> **2F4U said:**
> How do you usually connect to the internet (wireless, wired)? Do you use a router, dial-up or something else? If there is a router, can you ping it?

1. I'm connected by wire to my wireless router. 
2. I'm using cable internet. 
3. The problem IS situated in my Ubuntu OS. When I run Life CD or Windows I can connect to the internet without a problem. 
4. I booted my system specifically to be able to ping the router. However, my system froze so I was not able to ping the router. However, I could ping the PC from my mobile (through the router) when it was frozen.

---

### Post by makamba on 2013-06-20
At the moment I'am considering to reinstall Ubuntu. But in the mean time, here is some information others asked in other posts:
```

me@home:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1c:25:0a:35:a5  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe0a:35a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12754 (12.7 KB)  TX bytes:9801 (9.8 KB)
          Interrupt:23 Base address:0xc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:796 errors:0 dropped:0 overruns:0 frame:0
          TX packets:796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63948 (63.9 KB)  TX bytes:63948 (63.9 KB)

me@home: sudo lshw -C network
[sudo] password: 
  *-network               
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth0
       version: 10
       serial: 00:1c:25:0a:35:a5
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:23 ioport:e800(size=256) memory:febffc00-febffcff memory:febc0000-febdffff

me@home:~$ sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 2735

```

r8169 should be my ethernet driver (me thinks)
```

me@home:~$ lsmod | grep -i r8169
r8169                  62154  0 

me@home:~$ sudo modprobe r8169
me@home:

```
I'm not clear what should happen with modprobe

```

me@home:~$ me@home:~$ dmesg | grep -i r8169
[    1.843041] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.843080] r8169 0000:02:04.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.843111] r8169 0000:02:04.0: (unregistered net_device): not PCI Express
[    1.843588] r8169 0000:02:04.0: eth0: RTL8169sc/8110sc at 0xffffc90000610c00, 00:1c:25:0a:35:a5, XID 18000000 IRQ 23
[    1.843591] r8169 0000:02:04.0: eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
[  123.775090] r8169 0000:02:04.0: eth0: link down
[  123.775098] r8169 0000:02:04.0: eth0: link down
[  125.463162] r8169 0000:02:04.0: eth0: link up
[  929.068817] r8169 0000:02:04.0: eth0: link down
[  929.068835] r8169 0000:02:04.0: eth0: link down
[  930.861807] r8169 0000:02:04.0: eth0: link up

me@home:~$ sudo ifconfig eth0 down # Wired network - Disconnected - you are now offline
me@home:~$ sudo ifconfig eth0 up   # Wired network - You are now connected
me@home:~$ 

```
And then?

Lastly:
```
me@home:~$ uname -r
3.2.0-48-generic

Do I start with reinstalling Ubuntu?

```

---

### Post by praseodym on 2013-06-20
Check:
```

route -n
cat /etc/resolv.conf
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```

---

### Post by makamba on 2013-06-20
> **praseodym said:**
> Check:
```

route -n
cat /etc/resolv.conf
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```

I wrote this in Windows, so I was able to paste the text you saw in my  previous post. I need to reboot back to Linux, which has no Internet  connection. So can you please explain what information the previous instructions will give me, and what I have to do after that?

Thanks.

---

### Post by praseodym on 2013-06-20
Save the outputs into a text file and upload it (or paste the content)

---

### Post by makamba on 2013-06-20
Here is the output

```
me@home:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
```
Is this good?

```
me@home:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
```
What does this tell me?

```
me@home:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```
And this?
```
me@home:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false
```

Now what to do?

---

### Post by praseodym on 2013-06-20
Obviously you are receiving an IP address and the router is recognized. Try to shutdown all components (router, PC, etc.) currentless for 10 minutes and replug it again.

If it doesnt work, uninstall tghe package "resolvconf" and reboot.

---

### Post by makamba on 2013-06-20
> **praseodym said:**
> Obviously you are receiving an IP address and the router is recognized. 

Well that is something.

> **praseodym said:**
> Try to shutdown all components (router, PC, etc.) currentless for 10 minutes and replug it again.

As I am typing this in Windows, using the same router I don't think that powering down the router and PC will help me much. But it does not hurt to try.

> **praseodym said:**
> If it doesnt work, uninstall the package "resolvconf" and reboot.
As a last resort.

Thanks praseodym

---

### Post by makamba on 2013-06-20
Nope. No luck. I just reset my router to factory settings.

Edit:
And I removed the 'resolvconf' and rebooted. No joy in that department either.

---

### Post by makamba on 2013-06-21
And now I have Internet again. The fairies seem to have given me back my Internet connection. Thanks for your help praseodym.

---

### Post by jdthood on 2013-06-21
If you removed the resolvconf package you should now probably reinstall it.

---

