---
title: "Wireless issues"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by KernelKnight on 2010-03-04
I recently reinstalled Karmic. However, I can't seem to install my wireless drivers properly. I was told that all that was needed was to use the command

```
sudo apt-get install b43-fwcutter
```

I check in "Hardware Drivers" under System>Administration, and it reads as installed and in use, but the wireless does not work? What am I doing wrong?

---

### Post by Deadite81 on 2010-03-04
Are you sure your device is supported?

What output do you get from this command in a terminal?

```
lspci -vnn | grep 14e4
```

What device are you using?

---

### Post by KernelKnight on 2010-03-04
I know the device is suported. I have had this activated before. I need it for packet injection so STA driver is not an option. 

Here's the output:

```
atomsk@mobilegear:~$ lspci -vnn | grep 14e4
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

```

---

### Post by Deadite81 on 2010-03-04
Hmm, it is compatible, as you say.

Is your device itself claiming to be connected?
You can find out with this:

```
sudo lshw -C network
```

Also, this may seem silly, but have you restarted your computer?

Irrelevant Side Note: I don't use my Broadcom card anymore, it broke (I think it just burned out).
I use a little $20 Trendnet USB stick with wicd.  Once I finally got it working it actally seems faster!

---

### Post by KernelKnight on 2010-03-04
Yes, I restarted my comp. Here's the output:

```

       *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f6cfc000-f6cfffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:21:70:72:0e:c2
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v2.09 ip=129.107.73.243 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:f69f0000-f69fffff

```

---

### Post by bkratz on 2010-03-04
> **KernelKnight said:**
> I know the device is suported. I have had this activated before. I need it for packet injection so STA driver is not an option. 

Here's the output:

```
atomsk@mobilegear:~$ lspci -vnn | grep 14e4
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

```

Do you know which kernel you are using? If not you can find out with:

```
uname -mr
```

From this website  
[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

it says that your device is not supported by b43 in less than kernel 2.6.32 

14e4:4315
supported 2.6.32 and later
BCM4312
b/g
LP
b43

I believe you might want to look at  the open source version

[http://ubuntuforums.org/showthread.php?t=1055078&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=1055078&highlight=BCM4318)

and see if anyone has had luck.

---

### Post by KernelKnight on 2010-03-04
Okay, I forgot to install the 2.6.32 kernel. Let's see if it works on. Thanks :)

---

### Post by Deadite81 on 2010-03-04
Ah, using 9.10 with all upgrades I didn't even look at the kernel...:o

---

### Post by KernelKnight on 2010-03-04
It works now. Thanks!

---

### Post by bkratz on 2010-03-04
> **KernelKnight said:**
> It works now. Thanks!

Please mark the thread solved in the thread tools, a lot of people will probably look at this one!

congratulations!

---

