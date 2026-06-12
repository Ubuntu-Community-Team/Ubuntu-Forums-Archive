---
title: "Pre-Up not working on boot"
date: 2012-07-17
forum: Networking &amp; Wireless
---

### Post by jomom on 2012-07-17
So i've been having some issues with my Realtek 8111/8168B

realtek finally has some drivers on their site that state support for 3.x, this seems to work a lot better (don't have to load the module everytime I reboot)

but I am still having issues getting the HW address to stick

I can fix it by running ifconfig eth0 hw address XX:XX:XX:XX:XX

but it doesn't stay

I tried a few things from the documentation, but they don't seem to work

I added the above in the interfaces with pre-up in front

i've created a script in the if-pre-up.d folder that runs the above command

everything works when I run them manually (ie /etc/network/if-pre-up.d/changehwaddress), but nothing seems to work during the reboot

i'm stumped as I cannot figure out why this is not working the way its supposed to

has anyone gotten this to work?

3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:80:25:8c
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.031.00-NAPI duplex=full ip=10.90.70.2 latency=0 multicast=yes port=twisted pair promiscuous=yes speed=100Mbit/s
       resources: irq:46 ioport:de00(size=256) memory:fdeff000-fdefffff memory:fdee0000-fdeeffff memory:fde00000-fde0ffff

---

### Post by jomom on 2012-07-21
after digging around in the syslog I now notice that when the daily cron jobs run that the dhclient attempts to renew the lease, but because its attempting to renew the lease with FF:FF:FF:FF:FF it gets a random ip from my router

sh ip dhcp binding
...
10.90.70.59         ffff.ffff.ffff          Jul 22 2012 12:19 PM    Automatic
...

this happens everynight, but in the morning if i simply run dhclient -r;dhclient eth0 everything renews like normal

I'm really not understanding where else to look at this point for clues. is this a bug or am I still missing something

just did a fresh install of ubuntu 12.04 x64 less then a month ago

---

