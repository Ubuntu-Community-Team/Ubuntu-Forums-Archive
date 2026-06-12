---
title: "Fujitsu Siemens + Atheros card unable to find router"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by nocturnuk on 2009-09-28
Hello all. I apologise in advance if the solution is obvious here i have recently installed Ubuntu off of one of my University modules last year and its going fine excluding i can't get my wireless card to find my network. I'll try to post as much information as possible.

Laptop: Fujitsu Siemens M52228
OS: Ubuntu Linux 9.04 Jaunty Jackalope, installed within Windows Vista SP2
Wireless card:
```
08:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 04)
        Subsystem: Atheros Communications Inc. Device 3067
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at fa000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath_pci
        Kernel modules: ath_pci, ath5k

```Result from sudo lshw -C network

```

  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1f:16:03:96:72
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=192.168.0.2 latency=0 link=yes module=r8169 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wifi0
       version: 04
       serial: 00:16:44:f1:94:ca
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 7e:c9:58:88:1a:99
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```iwlist scan under ath0 gives "No Scan Results".

Other information:

Currently using Sky Broadband with WPA-PSK security on router Netgear DG834GT. Can connect fine in Vista, have tried several other guides and putting the connection in manually many times to no avail. Am currently using a hard-wired connection but that can only be used as a short-term solution (my desktop will need its connection back soon ;) ). 

I have installed Madwifi 0.9.4 i believe, but i cannot be sure if its worked (For obvious reasons, i'd assume not).

Feel free to ask for anything else i hope i can get this sorted (would also hope that it isn't a really simple fix too haha).

---

### Post by trundlenut on 2009-09-28
looking at the output from lshw there it would appear that the wireless card is listed as wifi0 not ath0

---

### Post by t0mppa on 2009-09-28
Wifi0 is the master device. The master device is an internal master device used only by ieee80211 in your case or by mac80211 for all the newer generation drivers (wmaster0 for ath5k, b43, iwlagn, rtl8180, etc.). It should be ignored by users. Ath0 is a front end for the above that users should manipulate and leave the drivers to handle wifi0.

As to your problem, lspci still shows ath5k as a module for your wireless, so are you sure you have blacklisted it after swapping to ath_pci? Having two drivers active for the same interface usually means neither one works.

Another thing is, do you have any other networks around? One possibility is, if you're outside US is that the network you're trying to find has a channel 12, 13 or 14, which are forbidden in the US and Ubuntu could is set to use only the US channels by default. But in that case, it should pick up all networks using channels 1-11.

Oh and didn't ath5k work for you? I have the same chip and it works perfectly well with it.

---

### Post by nocturnuk on 2009-09-28
> **t0mppa said:**
> Wifi0 is the master device. The master device is an internal master device used only by ieee80211 in your case or by mac80211 for all the newer generation drivers (wmaster0 for ath5k, b43, iwlagn, rtl8180, etc.). It should be ignored by users. Ath0 is a front end for the above that users should manipulate and leave the drivers to handle wifi0.

As to your problem, lspci still shows ath5k as a module for your wireless, so are you sure you have blacklisted it after swapping to ath_pci? Having two drivers active for the same interface usually means neither one works.

Another thing is, do you have any other networks around? One possibility is, if you're outside US is that the network you're trying to find has a channel 12, 13 or 14, which are forbidden in the US and Ubuntu could is set to use only the US channels by default. But in that case, it should pick up all networks using channels 1-11.

Oh and didn't ath5k work for you? I have the same chip and it works perfectly well with it.

There  are several networks around i cannot see any. According to the routers settings its broadcasting on channel 1 anyway, so i think i can rule that out. You mention blacklisting, how do i do that? ath5k indicates its not in use anyway, i attempted to blacklist but what i was doing wouldn't take.

I've followed so many guides i feel i've lost myself. 

Ath5k refused to work for me in the begining, but if it works for you i may well try getting it to work again, but i recall not being able to see wireless networks then either.

---

### Post by t0mppa on 2009-09-28
> **nocturnuk said:**
> There  are several networks around i cannot see any. According to the routers settings its broadcasting on channel 1 anyway, so i think i can rule that out.

Ok, something else is clearly wrong then. Does **dmesg | grep ath** or **less /var/logs/syslog | grep ath** (terminal commands) give any clues towards what could be going wrong?

> **nocturnuk said:**
> You mention blacklisting, how do i do that? ath5k indicates its not in use anyway, i attempted to blacklist but what i was doing wouldn't take.

By adding a line consisting of **blacklist <module_name>** to one of the .conf files at */etc/modprobe.d/*, blacklist.conf is the main file, but you can create others too, if you want to separate the rules you added yourself.

> **nocturnuk said:**
> I've followed so many guides i feel i've lost myself.

You came to the right place then. Guides can sometimes be a little overwhelming, when they don't explain what's happening, just give a dozen commands to run.

> **nocturnuk said:**
> Ath5k refused to work for me in the begining, but if it works for you i may well try getting it to work again, but i recall not being able to see wireless networks then either.

Ath_pci works for me too, so that's poor criteria for picking one over the other. ;)

---

### Post by nocturnuk on 2009-09-29
> **t0mppa said:**
> Ok, something else is clearly wrong then. Does **dmesg | grep ath** or **less /var/logs/syslog | grep ath** (terminal commands) give any clues towards what could be going wrong?

By adding a line consisting of **blacklist <module_name>** to one of the .conf files at */etc/modprobe.d/*, blacklist.conf is the main file, but you can create others too, if you want to separate the rules you added yourself.

Okay i've blacklisted what i needed and gave it a quick re-boot.
Output from dmesg | grep ath:

```

[    3.537468] device-mapper: multipath: version 1.0.5 loaded
[    3.537471] device-mapper: multipath round-robin: version 1.0.0 loaded
[   12.162276] ath_pci 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.162292] ath_pci 0000:08:00.0: setting latency timer to 64
[   12.655313] MadWifi: ath_attach: Switching rfkill capability off.
[   12.694197] ath_pci: wifi0: Atheros 5424/2424: mem=0xfa000000, irq=18
[   37.669020] ath0: no IPv6 routers present

```From **less /var/logs/syslog | grep ath **i just get a no file or directory message.

Still seeing no networks unfortunately.

---

### Post by t0mppa on 2009-09-29
Sorry, a typo. It's */var/log/syslog*, and it contains all the same things as dmesg, plus quite a bit of extra, so skimming through is a quite a bit of work.

Anyhow, it looks like the interface isn't even trying to do much, just fails to pick up IPv6 routers and that's it. I know some users have reported that disabling IPv6 on their machines has cured exactly the behavior you're facing, but I'm not 100% certain it is the cause of your troubles. Can't really think of any other issue either though. [Here]("http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html")'s a how-to about it, if you want to give it a shot.

---

### Post by nocturnuk on 2009-09-29
> **t0mppa said:**
> Sorry, a typo. It's */var/log/syslog*, and it contains all the same things as dmesg, plus quite a bit of extra, so skimming through is a quite a bit of work.

Anyhow, it looks like the interface isn't even trying to do much, just fails to pick up IPv6 routers and that's it. I know some users have reported that disabling IPv6 on their machines has cured exactly the behavior you're facing, but I'm not 100% certain it is the cause of your troubles. Can't really think of any other issue either though. [Here]("http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html")'s a how-to about it, if you want to give it a shot.

Followed the guide. For a while my wireless disappeared all together, re-installed madwifi and disabled IPv6 but i'm still at the same problem. Thanks for the follow up though, i'll keep searching for an answer.

---

