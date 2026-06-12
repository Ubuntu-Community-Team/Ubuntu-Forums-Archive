---
title: "Network Bonding on Server (RTFM done too many times)"
date: 2011-11-21
forum: Networking &amp; Wireless
---

### Post by mganapa on 2011-11-21
Hello All,
I have two servers running 11.10 server edition. One is 32 bit and the other is 64 bit. Both the servers have a dual port gigabit ethernet card. The issue I face is with configuring bonding (with static IP) on the 64bit server.
Let me start by giving you a bit of history. 
In 11.04, the bonding never worked on the 32 bit server. The same configuration worked great on the 64 bit server. I tried hard, read every manual and forum post but I could never get bonding to work on the 32 bit machine. Fast forward a few months and I install 11.10 (server) on both machines and all of a sudden, the 32 bit machine bonding starts working. I still use the configuration from the 9.04 release (see below). 
However, I can never get bonding to work now on the 64bit machine. The configuration that worked, does not work anymore. I tried the new configuration scheme for 11 and that doesn't work either. 

Old Network configuration (worked on 11.04 x64 not on 11.10 x64):
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto bond0
iface bond0 inet static
    address 192.168.0.21
    gateway 192.168.0.1
    netmask 255.255.255.0
    network 192.168.0.0
    bond-slaves eth1 eth2
    # LACP Configuration
    bond_mode balance-rr
    bond_miimon 100

auto eth1
iface eth1 inet manual

auto eth2
iface eth2 inet manual 

```Can anyone please assist me with this issue?

---

