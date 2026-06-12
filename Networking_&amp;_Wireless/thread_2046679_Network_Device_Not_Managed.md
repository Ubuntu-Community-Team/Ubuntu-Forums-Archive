---
title: "Network Device Not Managed?"
date: 2012-08-23
forum: Networking &amp; Wireless
---

### Post by chrisl121212 on 2012-08-23
I just got done installing Ubuntu 12.04. I had instant internet access on the Live Cd, but when I booted up my installation, I had an empty triangle and I clicked it and it said Network Device Not Managed. Here's where it gets weird. I went back to the live cd and wrote down what it did to connect in the Edit Connections. I made the same wired connection on my installation. Then it said under the Last Used "Never". Also when in System Monitor, there are small spikes of network activity and my Linksys Workgroup Switcher is lighting up saying that theres connection. What's going on?

---

### Post by Iowan on 2012-08-23
I presume */etc/network/interfaces* contains only definition for "lo"...

---

### Post by chrisl121212 on 2012-08-24
Is this what you mean?
[IMG]http://s17.postimage.org/cba1ybrqn/Screenshot_from_2012_08_24_13_11_46.png[/IMG]
How can I fix this?

---

### Post by steeldriver on 2012-08-24
Your /etc/network/interfaces file is fine assuming you are using the standard desktop installation (which uses NetworkManager instead of the older networking service)

Let's see what network hardware you have:

```

rfkill list

sudo lshw -C network

lspci -nnv | grep -A2 -E '\[02[08]0\]'
```

---

### Post by chrisl121212 on 2012-08-24
```
ubuntu@ubuntu:~$ rfkill list
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 12
       serial: 00:15:58:8c:00:4d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full firmware=N/A ip=192.168.1.123 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:fd9fc000-fd9fffff ioport:ce00(size=256) memory:fde00000-fde1ffff
ubuntu@ubuntu:~$ lspci -nnv | grep -A2 -E '\ [02[08]0\]'
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 

```

---

### Post by steeldriver on 2012-08-24
I don't really know anything about the Marvel controllers - is there anything in dmesg?

```
dmesg | grep sky2
```

---

