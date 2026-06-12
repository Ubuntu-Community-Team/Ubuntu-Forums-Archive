---
title: "eth0 Networking Problem"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by Linuturk on 2010-10-04
I'm having quite the strange problem.

Ubuntu 10.04
x86_64 - 2.6.32-25-generic

```

00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
```

Network Manager is configured to pull DHCP from eth0, and does so after a somewhat long wait.

After it connects, I'm able to access any local resources on the 192.168.1.X network, as well as ping the router and gateway. DNS resolution is also working correctly.

Any connections attempting to route past my gateway at 192.168.1.1 fail to return packets.

I also have a wireless network in the same building, that uses the same gateway as the wired network. When I connect to our wireless network, the network is fully functional and routes traffic past the gateway at 10.3.1.1

gateway (192.168.1.1) < Layer3 Switch (192.168.1.2) < Wireless Router (192.168.1.3 & 10.3.1.1)

**Note:** Yesterday, this laptop was running Fedora 13, and was not having any problems connecting to external resources on this wired network.

---

### Post by Linuturk on 2010-10-04
More information:

```
$ dmesg | grep -i eth0
[    1.003829] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1c:25:9b:e6:04
[    1.003831] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.003858] 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: 1008ff-0ff
[   13.570778] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.812073] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   16.812482] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   27.470094] eth0: no IPv6 routers present
[ 1017.960219] e1000e: eth0 NIC Link is Down
[ 1069.441001] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[ 1189.081480] e1000e: eth0 NIC Link is Down
[ 1200.542143] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[ 1311.220639] e1000e: eth0 NIC Link is Down
[ 1342.152161] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[ 1970.195007] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1c:25:9b:e6:04
[ 1970.195011] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[ 1970.195039] 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: 1008ff-0ff
[ 1970.281588] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1972.770917] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[ 1972.772092] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1983.051320] eth0: no IPv6 routers present

```

```
$ lsmod | grep -i e1000e
e1000e                136269  0
```

```
$ cat /var/log/messages | grep -i e1000e
Oct  3 22:01:41 naabal kernel: [    0.850431] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
Oct  3 22:01:41 naabal kernel: [    0.850434] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Oct  3 22:01:41 naabal kernel: [    0.850479] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Oct  3 22:18:13 naabal kernel: [    0.815302] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
Oct  3 22:18:13 naabal kernel: [    0.815305] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Oct  3 22:18:13 naabal kernel: [    0.829794] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Oct  4 01:02:31 naabal kernel: [    0.825584] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
Oct  4 01:02:31 naabal kernel: [    0.825586] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Oct  4 01:02:31 naabal kernel: [    0.868742] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Oct  4 01:45:23 naabal kernel: [ 2572.130336] e1000e 0000:00:19.0: PCI INT A disabled
Oct  4 01:45:23 naabal kernel: [ 2572.130341] e1000e 0000:00:19.0: PME# enabled
Oct  4 01:45:23 naabal kernel: [ 2572.130347] e1000e 0000:00:19.0: wake-up capability enabled by ACPI
Oct  4 01:45:23 naabal kernel: [ 2575.310279] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Oct  4 01:45:23 naabal kernel: [ 2575.310291] e1000e 0000:00:19.0: wake-up capability disabled by ACPI
Oct  4 01:45:23 naabal kernel: [ 2575.310296] e1000e 0000:00:19.0: PME# disabled
Oct  4 01:47:46 naabal kernel: [    0.871666] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
Oct  4 01:47:46 naabal kernel: [    0.871668] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Oct  4 01:47:46 naabal kernel: [    0.872751] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Oct  4 09:36:50 naabal kernel: [    0.799530] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
Oct  4 09:36:50 naabal kernel: [    0.799533] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Oct  4 09:36:50 naabal kernel: [    0.852061] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Oct  4 09:36:53 naabal kernel: [   16.742047] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
Oct  4 10:36:33 naabal kernel: [    0.842437] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
Oct  4 10:36:33 naabal kernel: [    0.842439] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Oct  4 10:36:33 naabal kernel: [    0.842485] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Oct  4 10:36:37 naabal kernel: [   16.361336] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
Oct  4 10:40:54 naabal kernel: [    0.840755] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
Oct  4 10:40:54 naabal kernel: [    0.840757] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Oct  4 10:40:54 naabal kernel: [    0.851575] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Oct  4 10:40:58 naabal kernel: [   16.820795] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
Oct  4 10:51:53 naabal kernel: [    0.862748] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
Oct  4 10:51:53 naabal kernel: [    0.862751] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Oct  4 10:51:53 naabal kernel: [    0.863845] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Oct  4 10:51:56 naabal kernel: [   16.641708] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
Oct  4 11:08:34 naabal kernel: [    0.842581] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
Oct  4 11:08:34 naabal kernel: [    0.842584] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Oct  4 11:08:34 naabal kernel: [    0.858523] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Oct  4 11:08:37 naabal kernel: [   16.812073] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
Oct  4 11:25:18 naabal kernel: [ 1017.960219] e1000e: eth0 NIC Link is Down
Oct  4 11:26:10 naabal kernel: [ 1069.441001] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
Oct  4 11:28:09 naabal kernel: [ 1189.081480] e1000e: eth0 NIC Link is Down
Oct  4 11:28:21 naabal kernel: [ 1200.542143] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
Oct  4 11:30:12 naabal kernel: [ 1311.220639] e1000e: eth0 NIC Link is Down
Oct  4 11:30:43 naabal kernel: [ 1342.152161] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
Oct  4 11:37:09 naabal kernel: [ 1728.690436] e1000e 0000:00:19.0: PCI INT A disabled
Oct  4 11:41:10 naabal kernel: [ 1970.052763] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
Oct  4 11:41:10 naabal kernel: [ 1970.052771] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Oct  4 11:41:10 naabal kernel: [ 1970.052872] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Oct  4 11:41:13 naabal kernel: [ 1972.770917] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None

```

---

### Post by Linuturk on 2010-10-04
New information.

The wired connection works fine at my house.

The primary difference is the docking station at the office. I did plug straight into the laptop at the office today, but the device wouldn't come up. It seems Ubuntu is choking on something to do with the docking station.

---

### Post by Sergius14 on 2010-10-04
In my networking experience this issues are very related with routes.

If can ping ok your GW but nothing behind them, could be missing routes at the other side of the network or a missing default gateways.

You can see your DG with "route".

You may expect something like this:

user@computername:~$ route

default         192.168.1.1   0.0.0.0         UG    0      0        0 wlan0

If you don't have this route add it manually and try again.

Regards,

---

### Post by Linuturk on 2010-10-05
Well, I came in this morning, and played with ping and traceroute and such, and it suddenly started working. Not sure why or how. I'm going to reboot and make sure it sticks.

---

### Post by Linuturk on 2010-10-05
Works after reboot. Weird.

---

### Post by Linuturk on 2010-10-05
Well, I was quite mistaken in my last diagnosis. It seems the issue was a little deeper than I thought.

I have removed several packages:

```
sudo aptitude purge libnss-mdns avahi-autoipd avahi-daemon avahi-utils telepathy-salut
```

and that has sped up my boot time and networking changes significantly. This has allowed me to properly diagnose the problem.

It seems that if I don't periodically ping my firewall (192.168.1.1) I can't get any information past that device. My default gateway (192.168.1.2) is a switching router with this ip route defined:

```
ip route 0.0.0.0 0.0.0.0 192.168.1.1
```

Please note:
There are about a hundred other workstations on this same network that work fine using 192.168.1.2 as the default route.
This was a non-issue using Fedora 13 last week.

Why is my connectivity dropping unless I ping my firewall at 192.168.1.1?

I have a temporary solution in place of running:

```
ping -i 30 192.168.1.1
```

but this is not ideal.

---

### Post by Linuturk on 2010-10-05
```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
10.3.1.0        *               255.255.255.0   U     2      0        0 wlan0
default         192.168.1.2     0.0.0.0         UG    0      0        0 eth0

```

---

### Post by Sergius14 on 2010-10-05
You should run further or deeper diagnosis.

Run a Wireshark to see what is happening when you lost conectivity.

I'll speceally check ARP requests/responses.

Can be the OS with something wrong, but first you need to figure out the exact cause.


Install Wireshark, wait to "loose" conectivity and check what's happening. Then update your post.

---

### Post by Linuturk on 2010-10-05
I'm not noticing anything obvious, except for the expected TCP retransmission requests.

---

### Post by Linuturk on 2010-10-05
I am ashamed to say that there was a duplicate IP on the network. I should have checked for it.

---

### Post by Sergius14 on 2010-10-05
Glad to know that you can find and solved your issue.

---

