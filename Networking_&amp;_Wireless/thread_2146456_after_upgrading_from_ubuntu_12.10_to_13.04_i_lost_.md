---
title: "after upgrading from ubuntu 12.10 to 13.04 i lost all my network adapters"
date: 2013-05-18
forum: Networking &amp; Wireless
---

### Post by amiralex32 on 2013-05-18
after upgrading from ubuntu 12.10 to 13.04 i faced 2 problems
1- i lost all my network adapters LAN or wireless
[FONT=arial] i run[/FONT]
[FONT=arial]> lshw -C network[/FONT]
[FONT=arial]> WARNING: you should run this program as super-user.[/FONT]
[FONT=arial]>   *-network[/FONT]
[FONT=arial]>        description: Network controller[/FONT]
[FONT=arial]>        product: BCM4311 802.11b/g WLAN[/FONT]
[FONT=arial]>        vendor: Broadcom Corporation[/FONT]
[FONT=arial]>        physical id: 0[/FONT]
[FONT=arial]>        bus info: pci@0000:0b:00.0[/FONT]
[FONT=arial]>        version: 01[/FONT]
[FONT=arial]>        width: 32 bits[/FONT]
[FONT=arial]>        clock: 33MHz[/FONT]
[FONT=arial]>        capabilities: bus_master cap_list[/FONT]
[FONT=arial]>        configuration: driver=wl latency=0[/FONT]
[FONT=arial]>        resources: irq:16 memory:efdfc000-efdfffff[/FONT]
[FONT=arial]>   *-network UNCLAIMED[/FONT]
[FONT=arial]>        description: Ethernet controller[/FONT]
[FONT=arial]>        product: BCM4401-B0 100Base-TX[/FONT]
[FONT=arial]>        vendor: Broadcom Corporation[/FONT]
[FONT=arial]>        physical id: 0[/FONT]
[FONT=arial]>        bus info: pci@0000:03:00.0[/FONT]
[FONT=arial]>        version: 02[/FONT]
[FONT=arial]>        width: 32 bits[/FONT]
[FONT=arial]>        clock: 33MHz[/FONT]
[FONT=arial]>        capabilities: bus_master cap_list[/FONT]
[FONT=arial]>        configuration: latency=64[/FONT]
[FONT=arial]>        resources: memory:ef9fe000-ef9fffff[/FONT]
[FONT=arial]> WARNING: output may be incomplete or inaccurate, you should run this[/FONT]
[FONT=arial]> program as super-user.[/FONT]
[FONT=arial]> but i don't know how to make it work
[/FONT]
[FONT=arial]2- when i shutdown ubuntu 13.04 it never shutdown it stop on ubuntu [/FONT][FONT=arial]screen without turn off

please i need help[/FONT]

---

### Post by praseodym on 2013-05-18
Download the firmware package from this link

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

save it in "Downloads" and uninstall the Broadcom-STA driver:
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo dpkg -i ~/Downloads/linux-*.deb
```
Reboot.

---

### Post by amiralex32 on 2013-05-19
thanks so much sir this solve my problem

---

