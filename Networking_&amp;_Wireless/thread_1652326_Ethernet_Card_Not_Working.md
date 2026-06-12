---
title: "Ethernet Card Not Working"
date: 2010-12-24
forum: Networking &amp; Wireless
---

### Post by gonzmi on 2010-12-24
I just finished installing Ubuntu 10.10 (64bit) and can not get the network up and running. Before the install I tryied the LiveCD and the internet worked, but on the hard drive install it does not. I went back to the LiveCD boot and wrote down all the configuration stuff (mac address, etc.) for the wired connection and entered them in the HDD version, but still nothing.
 
On a "for Dummies" book I have (*I'm a newbie*) I found the following command to test the driver was loaded correctly:
gonzmi@Punkin:~$ **dmesg|grep eth0**
[ 1.626762] r8169 0000:05:00.0: eth0: RTL8168d/8111d at 0xffffc9000067e000, 6c:f0:49:7c:d7:c2, XID 083000c0 IRQ 45
[ 8.346494] r8169 0000:05:00.0: eth0: [COLOR=red]link down[/COLOR]
[ 8.346843] ADDRCONF(NETDEV_UP): eth0: [COLOR=red]link is not ready[/COLOR]

[COLOR=black]From the "link down" and "link is not ready", I'm guessing the card is the issue. Can someone help with the steps to fix this?[/COLOR]

---

### Post by dineshs on 2010-12-24
What do you get for```
sudo lshw -C network
```Pl post the result

---

### Post by gonzmi on 2010-12-25
Here's what I get:
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: [EMAIL="pci@0000:05:00.0"]pci@0000:05:00.0[/EMAIL]
       logical name: eth0
       version: 03
       serial: *[COLOR=red]xx:xx:xx:xx:xx:xx[/COLOR]*
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:45 ioport:be00(size=256) memory:fd5ff000-fd5fffff memory:fd5f8000-fd5fbfff memory:fd500000-fd51ffff
 
I purposely removed the mac address, something I saw suggested on another thread for security...???  But the address is correct.

---

### Post by WA1DH on 2010-12-25
I'm having the exact same problem. I have a new system with a M4A87TD EVO Asus motherboard with the RTL8111/8168B Gigabit NIC onboard. No network connection. Hoping this can be fixed..

---

### Post by dineshs on 2010-12-25
sudo lshw -C network says link=no
Please see[COLOR="Red"] post #10[/COLOR]   [here ]("http://ubuntuforums.org/showthread.php?t=1648140&highlight=link%3Dno")
or #14 and #15 [here]("http://ubuntuforums.org/showthread.php?t=1480328&page=2")
Another link
[http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)

---

### Post by gonzmi on 2010-12-25
Thank you for the help!  The solution on the second link work.

[LIST=1]
[*]Powered down the modem
[*]Unplugged the network cable
[*]Rebooted the computer
[*]Powered the modem and plugged the cable
[*]Tada! it worked
[/LIST]
My wife had a good laugh, cause here boss is always telling here to cycle power to solve all her computer issues.   Now I can proceed with the rest of the new install.

---

### Post by dineshs on 2010-12-25
Please mark the thread as solved via thread tools.

---

