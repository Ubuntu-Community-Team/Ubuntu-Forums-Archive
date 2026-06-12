---
title: "Networks show up, but I cannot connect on Ubuntu 10.04"
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by eirikkri on 2010-08-27
I just installed Ubuntu 10.04 on my girlfriend's computer, a HP nc6220.

When trying to connect to wireless networks all neighborhood networks shows up, but when I try to connect to our unsecure network it tries for 10 seconds before I get the message "Disconnected - you are now offline". I get the same problem when I try a wired connection - it is recognized but I cannot connect. It is no problem to connect to the same network with another (Windows XP) computer.

Please tell me if you want more information - I haven't posted too much because I am (obviously, with no network) writing on another computer. 

What is my next step?

I will be thankful for all help, and hope to show my girlfriend that Linux is not as scary as she thinks...

---

### Post by Iowan on 2010-08-27
From a terninal (Applications>Accessories>Terminal), **sudo lshw -C network** will provide more information about your interfaces (more than you'd probably want to copy by hand...)  Also from the terminal, try **sudo dhclient**. You'll *probably* get information ending with something like: ```
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```Otherwise, what IP address is returned (for eth?) by **ifconfig -a**

---

### Post by bkratz on 2010-08-27
> **Iowan said:**
> From a terninal (Applications>Accessories>Terminal), **sudo lshw -C network** will provide more information about your interfaces (more than you'd probably want to copy by hand...)  Also from the terminal, try **sudo dhclient**. You'll *probably* get information ending with something like: ```
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```Otherwise, what IP address is returned (for eth?) by **ifconfig -a**

since you are essentially off-line---if you (just a suggestion)

```
sudo lshw -C network > hardware.txt

```

Then you will find a text document in your /home/user directory, in this case hardware.txt, which you can drag-n-drop onto a flash drive and see it in Windows with, IIRC, wordpad

---

### Post by eirikkri on 2010-08-29
Thanks for your quick reply, both of you.

Iowan, you are right, "sudo dhclient" returns "No DHCPOFFERS received". 

"sudo lshw -C network" returns
```

  *-network
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 11
       serial: 00:15:60:c4:2c:72
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5751m-v3.29a latency=0 link=no multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:d0000000-d000ffff
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:90:9c:df
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: irq:21 memory:d0400000-d0400fff

```


What is my next step?

---

### Post by MaindotC on 2010-08-29
You can also follow the steps in the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  It appears that you have the correct driver installed for your wireless card and your card is operating.  Please keep following the guide and let us know precisely at what point you are having difficulty, or answer Iowan's question about ip address and other information.

---

