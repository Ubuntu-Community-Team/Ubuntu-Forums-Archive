---
title: "diagnose faulty ethernet port"
date: 2012-05-30
forum: Networking &amp; Wireless
---

### Post by christon74 on 2012-05-30
Hello again  
Is there a line of command I could type into the Terminal to diagnose my ethernet port? 
OS= ubuntu 12.04 LTS

I have found this page but I suspect the commands found here are Windows and not Linux



[http://www.stat.ufl.edu/system/man/portmaster/trouble/hardware.fm.html#10175](http://www.stat.ufl.edu/system/man/portmaster/trouble/hardware.fm.html#10175)

Thanks. ;)

---

### Post by chili555 on 2012-05-30
Please try these commands:```
ifconfig
sudo lshw -C network
nm-tool
```

---

### Post by christon74 on 2012-05-30
description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: d0:27:88:05:b1:32
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:febe0000-febfffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth1
       serial: 00:00:e8:00:15:3e
       size: 100Mbit/s
       capacity: 100Mbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=pegasus driverversion=v0.6.14 (2006/09/27) duplex=full ip=192.168.1.34 link=yes multicast=yes port=MII speed=100Mbit/s

---

### Post by christon74 on 2012-05-30
IPv4 Settings:
    Address:         192.168.1.34
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        D0:27:88:05:B1:32

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

Could it be I have got the wrong driver? ... My Network card is a Realtek 8111/8168 B PCI Ethernet controller.

---

### Post by chili555 on 2012-05-30
I think Network Manager is the culprit. You have a wired ethernet connection:> description: Ethernet interface
physical id: 1
logical name: eth1
serial: 00:00:e8:00:15:3e
size: 100Mbit/s
capacity: 100Mbit/s
capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=pegasus driverversion=v0.6.14 (2006/09/27) duplex=full [COLOR="Red"]ip=192.168.1.34 [/COLOR][COLOR="Red"]link=yes[/COLOR] multicast=yes port=MII speed=100Mbit/s
And I think NM made the connection and sat down. Do you have two ethernet cables attached? Do you *NEED* two ethernet cables attached? If so, NM is not the way to do whatever it is you're trying to do.

NM is designed for most users to yippy skippy down to the coffee shop and connect to any network for which they have a password. Although it has been and is improving with every release, there are, as with all tools, some tasks for which it it unsuitable.> Could it be I have got the wrong driver? ... My Network card is a Realtek 8111/8168 B PCI Ethernet controller.In most cases, r8169 is correct.

---

### Post by christon74 on 2012-05-30
cannot remove the wrong driver. rmmod r8169 gives the following:
ERROR: Module r8169 does not exist in /proc/modules!

duh!

---

### Post by christon74 on 2012-05-30
Hello again Chili 
No no, I do not have two ethernet attached! I have Network Manager yes + Wicd. I juggle two computers. One runs Windows XP (hp nc 4200) the bigger one runs Ubuntu 12.04 LTS.
Ok, so I understand I can keep Module r 8169. 
Anyway, the USB ethernet concentrator allows me to connect for the moment and who knows, someday I might get back my connection ... just like by magic, eh? 

Thanks for all the info ;)

---

### Post by chili555 on 2012-05-30
> who knows, someday I might get back my connection ... just like by magic, eh?Not by magic, no. If you'd care to troubleshoot, remove the USB ethernet device, attach the cable to the built-in and run the tests again. Please add:```
dmesg | grep -e r8169 -e eth0
```

---

### Post by christon74 on 2012-05-31
Hello again Chili :)
Here is what the terminal displays:

Device: eth1  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            pegasus
  State:             connected
  Default:           yes
  HW Address:        00:00:E8:00:15:3E

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.34
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        D0:27:88:05:B1:32

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


root@christophe-TPS01:/home/christon74# dmesg | grep -e r8169 -e eth0
[    1.728835] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.728895] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.728952] r8169 0000:02:00.0: setting latency timer to 64
[    1.729042] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.735629] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xf841e000, d0:27:88:05:b1:32, XID 083000c0 IRQ 42
[    1.735643] r8169 0000:02:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   18.284786] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.644214] r8169 0000:02:00.0: eth0: link down
[   19.644915] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.646085] ADDRCONF(NETDEV_UP): eth0: link is not ready
root@christophe-TPS01:/home/christon74#

---

### Post by chili555 on 2012-05-31
> If you'd care to troubleshoot, remove the USB ethernet device, However, isn't this the USB ethernet device?> Device: eth1 [Wired connection 2] -------------------------------------------
Type: Wired
Driver: pegasus
State: connected
Default: yes
HW Address: 00:00:E8:00:15:3E

Capabilities:
Carrier Detect: yes
Speed: 100 Mb/s

Wired Properties
Carrier: onHow are we going to troubleshoot the Realtek r8169 device with no cable attached to it?

---

### Post by christon74 on 2012-05-31
Hello again Chili  :)

Yes, yes, you are right. I will try again to fix it this week-end. At the moment, I am listening to BBC radio Scotland. I am really hooked on 'Get it on with Bryan Burnett' 

:)

---

### Post by christon74 on 2012-06-01
Hello again Chili  :)
I very much appreciate your efforts and patience to help me fix this, but the only way I can connect is via this pegasus ethernet concentrator. Or I can use my wee hp nc 4200 which runs XP.

I don't remember if I have already posted this screen:
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: d0:27:88:05:b1:32
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:febe0000-febfffff

---

### Post by chili555 on 2012-06-01
> the only way I can connect is via this pegasus ethernet concentrator. Or I can use my wee hp nc 4200 which runs XP.No problem. Run the tests with the ethernet cable attached to the Realtek and copy and paste the terminal output to a text document in order to post it here. Then connect the Pegasus, connect to the internet and post. May I assume this was done with the ethernet cable _attached_?> *-network
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 03
serial: d0:27:88:05:b1:32
size: 100Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw latency=0 [COLOR="Red"]link=no[/COLOR] multicast=yes port=MII speed=100Mbit/s
resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:febe0000-febfffff
Does this machine dual-boot with Windows? Is this the issue? [https://wiki.archlinux.org/index.php/Configuring_Network](https://wiki.archlinux.org/index.php/Configuring_Network)

> **Realtek no link / WOL issue**

Users with Realtek 8168 8169 8101 8111(C) based NICs (cards / and on-board) may notice an issue where the NIC seems to be disabled on boot and has no Link light. This can usually be found on a dual boot system where Windows is also installed. It seems that using the offical Realtek drivers (dated anything after May 2007) under Windows is the cause. These newer drivers disable the Wake-On-LAN feature by disabling the NIC at Windows shutdown time, where it will remain disabled until the next time Windows boots. You will be able to notice if this issue is affecting you if the Link light remains off until Windows boots up; during Windows shutdown the Link light will switch off. Normal operation should be that the link light is always on as long as the system is on, even during POST. This issue will also affect other operative systems without newer drivers (eg. Live CDs).

---

### Post by christon74 on 2012-06-01
Yes, yes, yes, the test was done with  ethernet cable attached [not to the pegasus] but to the realtek.
One thing I have just found out on opening the network tools is that it fist displayed loopback interface and not eth0. I have just got back on line using the pegaus concentrator to download nmap.
One thing I must stress is that there is no Windows OS installed on this PC. When I bought it, there was no OS. I have tried to install XP at least 15 times but it just would not. Each and every time, I got to this blue screen warning me that if I insisted this install could damage my PC. And so, I decided to install Meerkat. Now I have both Pangolin (12.04 LTS)  and Meerkat and I can choose between both on load.

---

### Post by chili555 on 2012-06-01
Since Wake-on-LAN seems to be a clue, would you please check in the computer's BIOS and change WOL to whatever it isn't; that is, off if now on or on if now off. Reboot with the ethernet cable attached to the Realtek and check again:```
sudo lshw -C network
```Is *link=no* changed?

The Doc is now warming up the autoclave for surgery...

---

### Post by christon74 on 2012-06-02
Hello hello Chili :)
Ouch! Well ok.... I think I know how to do that...
Uh, surgery? really?

---

### Post by christon74 on 2012-06-02
Awwww. Cannot find WOL (wake on lan) I have been to the BIOS and I have found another option (Lan controller?) I have tried enabling it / disabling it but this does not change anything. Still no ethernet connection.
:(

---

### Post by christon74 on 2012-06-02
Still link= no

:(

---

### Post by christon74 on 2012-06-02
Hello again Chili :)
Connection is back. Ethernet cable attached to the right port, no need of the ethernet concentrator any longer. Machine has NEVER loaded with windows (no windows OS present). Aaaaah the mysteries of Ubuntu ! (for somebody who like me is neither a developper nor an analyst....)
I cannot find the words to say how grateful I feel to know my network card is not '******' !!! :)
Conclusion: problem solved _ And I am fully aware I can take no credit for it _

---

### Post by chili555 on 2012-06-02
> And I am fully aware I can take no credit for it And neither can I!> Uh, surgery? really? Yes. If the card and driver combination misbehave again, there is an alternate driver available that we can try. It's a bit complex but do-able. For now, let's hope whatever gremlins there were are gone for good.

[http://www.rvdavid.net/how-to-get-gigabit-speeds-from-rtl81118168b-pci-express-gigabit-ethernet-controller-on-ubuntu-linux/](http://www.rvdavid.net/how-to-get-gigabit-speeds-from-rtl81118168b-pci-express-gigabit-ethernet-controller-on-ubuntu-linux/)

---

