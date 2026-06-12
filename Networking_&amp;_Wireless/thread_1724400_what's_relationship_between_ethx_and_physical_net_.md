---
title: "what's relationship between ethx and physical net cards"
date: 2011-04-08
forum: Networking &amp; Wireless
---

### Post by richard_wu0313 on 2011-04-08
Hi forks,
Do you know what's relationship between ethx and physical net cards? such as i have three net cards in the PC, named A, B, C. In which config file  i could know that eth0 -> A, eth1 -> B, and eth2 -> C. Would the mapping relationship change after reboot? Is there any method i could change the mapping?

---

### Post by chili555 on 2011-04-08
The mapping is in /etc/udev/rules.d/70-persistent-net.rules. Here is an example from my machine:> # PCI device 0x8086:0x109a (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:16:41:e6:99:99", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4227 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:19:d2:c2:99:99", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"



# USB device 0x1740:0x9801 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:02:6f:6f:99:99", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"As you can see, my USB wireless device is mapped to wlan1 and my built-in is wlan0. I am pretty sure you can edit the file to change the mapping and immediately reboot.

You can learn the MAC address in:```
sudo lshw -C network
```For example:> *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: [COLOR="Red"]00:19:d2:c2:99:99[/COLOR]
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-28-generic firmware=15.32.2.9 ip=192.168.1.108 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:edf00000-edf00fff

---

### Post by richard_wu0313 on 2011-04-08
thanks, very detail. one more question, eth0, or wlan0 would be the first name system would use?  is it possible system would use eth1, eth2, and so on, and skip eth0 to map physical net card?  because yesterday i boot up a ubuntu10.04 OS and found no eth0, but started from eth1. could i change the rule?  i mean to start from eth1 or eth2 and so on.

---

### Post by chili555 on 2011-04-08
Not likely, unless you had a working eth0, eth1, eth2, etc. and then retired the first card. The system doesn't know if the retirement is permanent or temporary and so reserves eth0 for its possible return. The mapping of MAC address to driver to interface should remain intact.

---

### Post by richard_wu0313 on 2011-04-08
that's very strange. yesterday i tried to install ubuntu 10.04 by PXE, i had two net cards in my machine, one was for PXE network, the other was for common network, But when i selected to boot from network, and boot kernel need to first download kickstart file from PXE network, boot kernel failed and complained "couldn't connect to PXE network from eth0", and even after i switched the network of physical net cards. of  course, all these happen was before login. after i login in, the two net cards could have IP address, but they were eth1 and eth2, instead of eth0 and eth1.

---

### Post by chili555 on 2011-04-09
I can't say I've seen this behavior before. I am suspicious it has to do with the failure to boot smoothly and install from PXE. There is nothing inherently wrong with eth1 and eth2. I am fairly certain you could simply ignore it and go forward. If you are a bit OCD, like many of us are, you could certainly amend /etc/udev/rules.d/70-persistent-net.rules to suit your needs. I suggest you reboot immediately to avoid any networking issues.

---

