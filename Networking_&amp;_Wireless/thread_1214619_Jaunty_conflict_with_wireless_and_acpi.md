---
title: "Jaunty conflict with wireless and acpi ?"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by caitriana on 2009-07-16
As a novice Ubuntu user, I installed Jaunty last week and everything was working nicely. Yesterday the update manager downloaded a few packages including an acpi update; today, my wireless suddenly stopped working.

After trying various things with the wireless, I found a hint on another forum that turning acpi off might help. Eventually, booting the kernel with acpi=ht allows the wireless to work. (acpi=off also worked but it took a long time to boot and graphics were messed up). 

But now I can't get battery / power information... is there any way to fix this? i.e. get acpi and wireless both working? or else to get power info some other way?

thanks :-)

laptop is Dell vostro 1000

wireless card:
```
$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:3a:0e:ec:1d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 \
ip=192.168.1.101 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
```/boot/grub/menu.lst:
```
title           Ubuntu 9.04, kernel 2.6.28-13-generic
uuid            61b9f2c3-b00c-4544-900e-12ecb2558ff7
kernel          /boot/vmlinuz-2.6.28-13-generic \
root=UUID=61b9f2c3-b00c-4544-900e-12ecb2558ff7 \
ro quiet splash acpi=ht
initrd          /boot/initrd.img-2.6.28-13-generic
quiet
```

---

### Post by nixscripter on 2009-07-29
What do you mean by "can't get battery information"? What happens when you run this in a terminal:

```
acpitool -b
```

---

### Post by Dawei87 on 2009-07-30
i think what he means is his computer does not detect the battery at all. without acpi, it just reads the AC and it will not put any power-manager applet on the panel and wont have a battery tab under the power manager. but in the end, im not sure how you can correct this without enabling acpi.

---

### Post by nixscripter on 2009-07-30
Oh. So  the real question is, what the did the update do?

I don't know for sure, but perhaps the card is just powered off or in a funny wakeup. If you reboot with ACPI turned on, it might be possible to wake it up. You can use: ```
acpitool -w
``` to get a list of PCI devices. Then you can match it to your card's location on the bus in the output from ```
lspci
```

---

