---
title: "Wireless is not working on 9.10"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by jarame on 2009-12-12
A few weeks ago there was some system update on Ubuntu 9.10 and after the update my wireless card stopped working. So I switched over to Windows for wireless (because that's where is seems to work). I'm using a wired connection right now so I can try to fix this issue but I'm stuck. I'm going through this process right now:

```

                                                                         Ubuntu supports a system known as NDISWrapper. This allows you to use a Windows wireless device driver under Ubuntu.
                                    
[LIST=1]
[*]                       Obtain the Windows Driver for your system and locate the file that ends with .inf.
[*]                       Install the **ndisgtk** package.
[*]                       Open **ndisgtk** (System &#8594; Administration &#8594; Windows Wireless Drivers).
[*]                       Select *Install new driver*.
[*]                       Choose the location of your Windows .inf file and click **Install**.
[*]                       Click **OK**.
[/LIST]

```but I cannot find the *.inf *file that is mentioned. I found a folder called *inf *but it is empty. Is there another way I can fix my wireless card, or is there a way to obtain this file?

If it helps, this is what I have found in my terminal:
```
jarame@ubuntu:~$ sudo lshw -C network
[sudo] password for jarame: 
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=80 maxlatency=28 mingnt=10
       resources: memory:c0200000-c020ffff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:2c:19:ed
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:20 ioport:a000(size=256) memory:c0211000-c02110ff
```

---

### Post by s3MA00RRNY on 2009-12-12
Are you sure you need to use NDIS wrapper? The Atheros drivers that come with Ubuntu should be able to support your card.

---

### Post by jarame on 2009-12-12
> **pcdude2143 said:**
> Are you sure you need to use NDIS wrapper? The Atheros drivers that come with Ubuntu should be able to support your card.

I dont know what I need. I've installed the Drivers for my wireless card once before, but then some system update made it to where my wireless card is useless. I was just following the steps of some tutorial to see if i could get working, but I have no idea where the "inf" file is located. So I'm stuck with Windows unless someone knows of another way to fix this :[

---

### Post by s3MA00RRNY on 2009-12-12
Does the Karmic Live CD work with your wireless card? If it does, do an lsmod at the terminal.

---

### Post by nitnat56 on 2009-12-12
I also could not get wireless to work on 9.10, until I tried manually setting up a connection under Network Connections. Click Add and enter the ESSID, as well as any key or password for security settings. It connected and still works after rebooting.

---

### Post by jarame on 2009-12-12
> **pcdude2143 said:**
> Does the Karmic Live CD work with your wireless card? If it does, do an lsmod at the terminal.

I do not have a working CD/DVD Drive at the moment, unfortunately.

> **nitnat56 said:**
> I also could not get wireless to work on 9.10, until I tried manually setting up a connection under Network Connections. Click Add and enter the ESSID, as well as any key or password for security settings. It connected and still works after rebooting

I too have tried this. I've tried it about 10 times. Still nothing :[ So I thought I would try to get the INF file through Windows and install the drivers that way, but I cannot locate the .inf file. So I'm at a stand still

---

### Post by linux6994 on 2009-12-12
I also had wireless troubles with fresh install of 9.1, after many fruitless atempts I loaded Linux Mint 8 which is Karmic Gnome based and all is well.

---

