---
title: "Netgear WG311v2, drops connection, ndiswrapper and acx111"
date: 2005-12-11
forum: Networking &amp; Wireless
---

### Post by hamil on 2005-12-11
Hmmm... Having big trouble with my internetconnection. I am connecting to an router out of my reach, from my student dorm room. The connection is protected with an WEP-passphrase, 10 digits.
I am running Breezy Badger i386 on an AMD64 machine, having bought the NetGear 311v2, i thought my connction would be good and stable, but it isn't...

When installing Ubuntu, it is recogniced, and i am able to download my languagepacks in the install, after inserting my essid and wep-key.

The trouble starts when i do something with heavy use of the computer, or network. Like transfering big files from my HD to my USB hd, or transfering files over the local network, or similar heavy use of the network/machine.

After checking alot of other threads, and trying both ndiswrapper, and the acx_100 from houseofcraig.net, I have found nothing of it to work... 

When I did try the acx_100 from houseofcraig, I found it to work, but after some use, it also dropped the connection. Sometimes, Ican be lucky, and the connection stays alive for days, but other times, it drops after 10 min.
When i returned to houseofcraig.net, there was a statement on the frontpage that the packages downloaded from this site would not work with my kernel, so i did as i was told, and went to acx100.erley.org, and downloaded the latest from that page. When I followed the instructions from that page, I ended up with an unusable system. After a reboot, I got to the login page, but I could never log in. I had to do a complete reinnstallation again..

Looking to another solution, I was told to use ndiswrapper, it was supposed to manage this problem.. But I could not even get it to work properly..
I installed ndiswrapper via synaptic, and have tried to install the drivers both in the terminal and the gui-way. Both installs the driver perfectly, and the hardware is found present and everything. I have tried to remove the old acx_pci.ko, and putting ndiswrapper in the /etc/modules
But after an reboot, i am not able to connect. In network tools, my wlan-card is still showing up as active, but it does not work..

So i reverted back to the original acx_pci.ko now, and have to live with an reboot every time my connection drops... annoying...

My /etc/networking gives this output:
```
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map wlan0

# The primary network interface
iface wlan0 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid Etasje 3
        wireless-key1 3443445545
        wireless-key s:3443445545

auto wlan0

```

And my ifonfig wlan0 gives this output:
```
wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:80:B6:D9
          inet addr:192.168.0.248  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fe80:b6d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7120 errors:287 dropped:0 overruns:0 frame:0
          TX packets:6726 errors:316 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6072859 (5.7 MiB)  TX bytes:1033877 (1009.6 KiB)
          Interrupt:18 Base address:0xe000


```

My lshw -C gives this output:
```
*-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 8
       bus info: pci@02:08.0
       logical name: wlan0
       version: 00
       serial: 00:0f:b5:80:b6:d9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci ip=192.168.0.248 multicast=yes wireless=IEEE 802.11b+/g+
       resources: iomemory:fdffe000-fdffffff iomemory:fdfc0000-fdfdffff irq:18

```

And lspci -v this output:
```
0000:02:08.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
        Subsystem: Netgear: Unknown device 4c00
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at fdffe000 (32-bit, non-prefetchable) [size=8K]
        Memory at fdfc0000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: <available only to root>

```

All outputs are taken when i am online.

Is there someone out there who can be able to help me with this issue??
Would be nice to have a stable connection without al these dropouts..

Brgds Lasse

---

