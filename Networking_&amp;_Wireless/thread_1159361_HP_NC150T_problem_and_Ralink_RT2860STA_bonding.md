---
title: "HP NC150T problem and Ralink RT2860STA bonding"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by Faw on 2009-05-14
I have 2 problems:

1) I have an [HP NC150T PCI 4-port gigabit combo switch adapter]("http://h18013.www1.hp.com/products/servers/networking/nc150t/documentation.html"), from what I understand it's supposed to use the tg3 driver but is not recognized. I get the following when I do 'lshw -C network'

```

*-network UNCLAIMED
       description: Ethernet controller
       product: NetXtreme BCM5705_2 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:07:04.0
       version: 03
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi cap_list
       configuration: latency=32 mingnt=64
       resources: iomemory:f7ffffff0-f7fffffef

```

and the following shows on /var/log/dmesg
```

[    5.021661] tg3.c:v3.94 (August 14, 2008)
[    5.021678] tg3 0000:07:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.021697] ioremap: invalid physical address f7fffffff0400000
[    5.021704] ------------[ cut here ]------------
[    5.021705] WARNING: at /build/buildd/linux-2.6.28/arch/x86/mm/ioremap.c:212 __ioremap_caller+0x322/0x390()
[    5.021707] Modules linked in: tg3(+) e1000e(+) vesafb fbcon tileblit font bitblit softcursor
[    5.021713] Pid: 321, comm: modprobe Not tainted 2.6.28-11-generic #42-Ubuntu
[    5.021715] Call Trace:
[    5.021720]  [<ffffffff802509bf>] warn_on_slowpath+0x5f/0x90
[    5.021725]  [<ffffffff8069bf36>] ? printk+0x67/0x69
[    5.021728]  [<ffffffff802b6cae>] ? __get_free_pages+0x1e/0x60
[    5.021731]  [<ffffffff80236c02>] __ioremap_caller+0x322/0x390
[    5.021736]  [<ffffffffa006b87d>] ? tg3_init_one+0x180/0xc93 [tg3]
[    5.021739]  [<ffffffff805b74bf>] ? alloc_netdev_mq+0x11f/0x180
[    5.021742]  [<ffffffff805c8a00>] ? ether_setup+0x0/0x80
[    5.021745]  [<ffffffff80236d82>] ioremap_nocache+0x12/0x20
[    5.021749]  [<ffffffffa006b87d>] tg3_init_one+0x180/0xc93 [tg3]
[    5.021752]  [<ffffffff80349518>] ? sysfs_do_create_link+0xc8/0x160
[    5.021756]  [<ffffffff80418a2a>] ? kobject_get+0x1a/0x30
[    5.021758]  [<ffffffff8069e569>] ? _spin_lock+0x9/0x10
[    5.021762]  [<ffffffff80430c3c>] pci_device_probe+0x7c/0xa0
[    5.021766]  [<ffffffff804b98fd>] really_probe+0x6d/0x1a0
[    5.021768]  [<ffffffff804b9a7b>] driver_probe_device+0x4b/0x60
[    5.021770]  [<ffffffff804b9b2b>] __driver_attach+0x9b/0xa0
[    5.021772]  [<ffffffff804b9a90>] ? __driver_attach+0x0/0xa0
[    5.021774]  [<ffffffff804b90eb>] bus_for_each_dev+0x6b/0xa0
[    5.021776]  [<ffffffff804b977c>] driver_attach+0x1c/0x20
[    5.021778]  [<ffffffff804b88dd>] bus_add_driver+0x14d/0x250
[    5.021781]  [<ffffffffa002f000>] ? tg3_init+0x0/0x20 [tg3]
[    5.021783]  [<ffffffff804b9d1c>] driver_register+0x6c/0x150
[    5.021787]  [<ffffffffa002f000>] ? tg3_init+0x0/0x20 [tg3]
[    5.021789]  [<ffffffff80430f1d>] __pci_register_driver+0x6d/0xc0
[    5.021793]  [<ffffffffa002f000>] ? tg3_init+0x0/0x20 [tg3]
[    5.021796]  [<ffffffffa002f01e>] tg3_init+0x1e/0x20 [tg3]
[    5.021799]  [<ffffffff8020a03b>] do_one_initcall+0x3b/0x170
[    5.021802]  [<ffffffff802d0225>] ? __vunmap+0xc5/0x110
[    5.021804]  [<ffffffff802d02c5>] ? vfree+0x25/0x30
[    5.021807]  [<ffffffff8027eee8>] ? load_module+0x11c8/0x11d0
[    5.021810]  [<ffffffff8027ef9d>] sys_init_module+0xad/0x1e0
[    5.021812]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
[    5.021814] ---[ end trace 37a1aa17e88c2415 ]---
[    5.021816] tg3: Cannot map device registers, aborting.
[    5.021823] tg3 0000:07:04.0: PCI INT A disabled
[    5.021828] tg3: probe of 0000:07:04.0 failed with error -12

```

I want this computer to be a router that's why i got this card, I want everything connected to this card (4 ports) to be sent to the actual NIC going out (eth0).

2) I have 2 nic ports + a wireless card (Ralink RT2860) on the computer. I want to bond them so that if I connect a cable to either eth0,eth1 the computer uses that connection but if I disconnect the cable it goes over wireless. Right now I have bonding working with the wired ports (eth0+eth1) and it works. I'm unable to add the ra0 to the bond as soon as I add it the network stops working. My interfaces file:

```

# The loopback network interface
auto lo
iface lo inet loopback

auto bond0
iface bond0 inet manual
pre-up ifconfig bond0 up
# i thought adding this line would associate the card with the 
# access point, without getting an IP adress, am I wrong?
#post-up wpa_supplicant -BW -Dwext -ira0 -c/etc/wpa_supplicant/wpa_supplicant.conf
post-up ifenslave bond0 eth0 eth1 ra0
post-up dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.bond0.pid -lf /var/lib/dhcp3/dhclient.bond0.leases bond0
pre-down dhclient3 -r bond0
#pre-down killall -q wpa_supplicant
pre-down ifenslave -d bond0 eth0 eth1 ra0

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

# The secondary network interface
#auto eth1
#iface eth1 inet dhcp

#auto ra0
#iface ra0 inet dhcp
#wpa-driver wext
#wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

```

Any help with any of my 2 problems will be greatly appreciated.

---

