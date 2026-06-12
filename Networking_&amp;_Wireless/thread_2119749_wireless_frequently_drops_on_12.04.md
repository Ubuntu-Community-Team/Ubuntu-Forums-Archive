---
title: "wireless frequently drops on 12.04"
date: 2013-02-24
forum: Networking &amp; Wireless
---

### Post by kavmac on 2013-02-24
so i've finally decided to go feet first and run Ubuntu 12.04 LTS on my Dell XPS l501x (i3 m380). thought i'd try and get steam installed, but i've got some tweaking to do to my system first, before it'll even open. (something about my graphics, of course). so i went to start playing with that today, and my wifi connection kept randomly dropping. full signal it seems, but the connection would drop frequently. took a few refreshes to get anything on the forums to load, and even more for them to load 'properly'. a few hours later (not of full-blown troubleshooting, but some, and i've grabbed all of the stuff from the how-to thread for a new support thread) it appears to be somewhat stable, although rather slow.

i would greatly appreciate some assistance figuring out if it's stuff that's missing from my install, etc or if it was perhaps just my router being silly earlier today!

(if anyone would like me to go ahead and share all the info in the how-to guide, i will.. otherwise i thought it'd be easier to just start with the basics as it's asked - everything is done & saved though).


thanks!

---

### Post by ahallubuntu on 2013-02-24
~

---

### Post by kavmac on 2013-02-24
sorry i didn't see this sooner!


$ sudo lshw -C network

```
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:49:d8:82
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-24-generic firmware=39.31.5.1 build 35138 ip=192.168.1.144 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:50 memory:f0400000-f0401fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 06
       serial: f0:4d:a2:6c:30:31
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.112 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:47 ioport:5000(size=256) memory:f0a04000-f0a04fff memory:f0a00000-f0a03fff

```

---

### Post by ahallubuntu on 2013-02-24
~

---

### Post by kavmac on 2013-02-25
i've tried out the second option for now. i'll give it a bit to test it out. thanks :)

---

### Post by Hodevah on 2013-02-25
What about manually adjusting the *rc.local* file if you are getting temperamental connections if nothing else helps? 

```

sudo gedit /etc/rc.local
```

Mind you I am only mentioning this as either an option or if nothing else works.

---

### Post by alcyst on 2013-03-02
Looks iike 

sudo modprobe -r iwlwifi
sudo modprobe iwlwifi swcrypto=1

got wifi working on my Dell XPS 13 with 12.04 Sputnik. Speed is very modest though 1Mb where I would get 8-10Mb on other machines. Turned out the speed issue was a problem with the router, speed & connectivity both ok now.

---

