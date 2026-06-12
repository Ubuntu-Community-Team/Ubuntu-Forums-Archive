---
title: "unstable internet connection"
date: 2011-07-23
forum: Networking &amp; Wireless
---

### Post by ubfoac on 2011-07-23
i have an unstable internet connection,when browsing suddenly i'm unable to load anything which keeps going for a min or so then the internet comes back to repeat that again after a while,same for any other internet app.
i have another os (windows 7) on the same computer and the internet works perfectly so i guess it's a system related thing,even when connecting to the same router by another computer at the same time (by wireless on the same router) everything works fine even in the moment ubuntu is not.


description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
       serial: 50:e5:49:3a:3e:9d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz

built in ethernet
speedtouch router
wired connection
ubuntu 11.04
dual booting with windows 7
the system is up to date
afaik the setting for the connection and dhcp (set to automatic) is the same as the ones i have on my mac and windows

i can bare most issues but not the ones concerning the internet!!

i'm new to ubuntu so i hope to stay away from the geeky stuff

and do i have to buy a wireless card instead of the wired one?

---

### Post by jmoorse on 2011-07-24
Hi, there appears to be an issue with the wrong module being loaded for r8168.  Can you please run these commands:

```

sudo rmmod r8169 
sudo modprobe r8168
sudo dhclient

```

and then post the output of:

```

ifconfig -a

```

Please see if that helps!  Thanks

---

