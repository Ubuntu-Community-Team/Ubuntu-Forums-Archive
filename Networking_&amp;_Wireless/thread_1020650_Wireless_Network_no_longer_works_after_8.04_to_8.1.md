---
title: "Wireless Network no longer works after 8.04 to 8.10 upgrade"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by prezvdi on 2008-12-24
I have seen the same issue from other posters, tried all their suggestion.

Wireless worked perfectly in 8.04, even on WPA networks. Upgraded today to 8.10, and now wireless interface does not appear in NetworkManager.

Panasonic CF-29 Toughbook laptop.

Output from lshw -C network :
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 19
       serial: 00:0b:97:33:65:9a
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32 maxlatency=24 mingnt=3

Any other suggestions? Due to complex configuration, a 'fresh install' of 8.04 or 8.10 would be VERY difficult (multiple versions of Windows in GRUB).

Thank you.

---

### Post by frankelr on 2008-12-24
Are you using a static ip?  new update for 8.10 broke my networking on my static ip machine, other dhcp machines are still working.  If you are a static ip there are other thread which can get you working

good luck Bob

---

### Post by prezvdi on 2008-12-25
Bob,

Thanks for the thought, but no. Home router (also running Linux), DHCP only. No static IP.

I'd really hate to have to wait all the way until the first release in 2009 to get wireless working. I have enough trouble with all my Window$ friends as it is . . .

---

