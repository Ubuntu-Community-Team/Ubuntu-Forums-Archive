---
title: "NC10 lost wireless"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by themorningflight on 2009-01-31
I've lost wireless since the last Ubuntu upgrade. Have searched forums and tried various things but nothing gets it working again. Have been using my NC10 since beginning of Dec 08 and have had no problems with wireless until now. As I have dual-boot I went into the XP side and wireless works there fine. But not in 8.10! Help?

In the terminal I ran 'lshw' and got a lot of output including the following:

  *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0

If some wizz out there needs more info, I ran 'lspci -v | less' in the terminal I got lots of info including the following:

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Askey Computer Corp. Device 7131
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at f0100000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

But when I run 'iwconfig' I get:

[INDENT]lo        no wireless extensions.

eth0      no wireless extensions.[/INDENT]

Looking in my blacklist (/etc/modprobe.d/blacklist) I see:

[INDENT]# replaced by p54pci
blacklist prism54

# possible conflict with orinoco drivers
blacklist hostap_cs
blacklist hostap

and:
blacklist ath_pci
blacklist ath_hal[/INDENT]

I don't know if any of the blacklisted things are wrong.

So, any ideas?

---

### Post by themorningflight on 2009-01-31
I did it!

I kept looking and found someone who had the answer. 

Thanks to the following site:
[http://nc10linux.wordpress.com/2008/12/10/install-wireless-driver/](http://nc10linux.wordpress.com/2008/12/10/install-wireless-driver/)

:D

---

