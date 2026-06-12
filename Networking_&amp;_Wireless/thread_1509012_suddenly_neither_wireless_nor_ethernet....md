---
title: "suddenly neither wireless nor ethernet..."
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by cespinal on 2010-06-13
I thought long away were the days where I would turn on my pc and say WTF HAPPENED IN HERE?...these days are back

Just turned on my pc. (hp dv9000 with broadcom wireless) and resulted that my wireless was down, displaying the tyipical orange led. I usually solve this by reinstalling the driver in a minute. But this it went diffent. Here is the output im transcribing from a terminal (lshw- network) 


```
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:2c:50:e6
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:20 memory:f2588000-f2588fff ioport:30f8(size=8) memory:f2589c00-f2589cff memory:f2589800-f258980f
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f2200000-f2203fff memory:f2000000-f20fffff(prefetchable)
```

the hell hapenned??? I am aware that i just need to get back the wireless driver to get wireless working but I cant even use an ethernet cable to get online :(....these things only hapenned when using Hardy :(. 

Also I dont dual boot so I really dont know how to switch between kernels should that would be a workaround for this. 

I really hope you can help me sort this out. last two weeks at graduate school and just cant afford speding the whole day offline :(

cheers!

---

### Post by PRC09 on 2010-06-13
If you press and hold the shift key during the boot process it should bring up the Grub menu and allow you to select which kernel you wish to boot.....

---

### Post by chili555 on 2010-06-13
> **PRC09 said:**
> If you press and hold the shift key during the boot process it should bring up the Grub menu and allow you to select which kernel you wish to boot.....Or perhaps the Esc key.

---

### Post by PRC09 on 2010-06-13
The esc key is for 9.04 and older Grub,press and hold shift is for Grub 2.....

---

### Post by chili555 on 2010-06-13
> **PRC09 said:**
> The esc key is for 9.04 and older Grub,press and hold shift is for Grub 2.....Indeed. The OP does not say which version he's using and, moreover, if he upgraded instead of fresh installed, he may still have old Grub, as I do. That's why I say 'perhaps.'

---

### Post by cespinal on 2010-06-14
thanks for coming back to me guys....the kernel im running is 2.6.32-22. I also have the -21 kernel available on grub but says it fails to lo load from the hard disk, finally leading me to a CLI.

to chilli: I have 10.4, upgraded from karmic when it came out and have nt had any problems at all until yesterday. I believe I have the old grub since I dont see any fancy backgrounds or icons :P

---

### Post by cespinal on 2010-06-14
update....got ethernet working by puttin this in  /etc/network/interfaces

```
auto eth0
iface eth0 inet dhcp
```

then I managed to reinstall the broadcom driver, made a reboot and Im back online. 

thanks for the answers and I hope this would be useful for someone else

---

