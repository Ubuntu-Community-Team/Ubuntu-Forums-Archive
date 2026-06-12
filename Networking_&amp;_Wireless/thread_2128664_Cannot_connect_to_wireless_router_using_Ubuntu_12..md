---
title: "Cannot connect to wireless router using Ubuntu 12.04 LTS"
date: 2013-03-23
forum: Networking &amp; Wireless
---

### Post by Tim13 on 2013-03-23
After spending a couple of days using ndiswrapper to install a Windows drive I have got the network to install (Marvell W8300 chipset on a DLINK DWL-G510) but cannot connect to my router using WPA/WPA2 encryption. I'm not sure which output would be useful to get help, but here I go:

 lshw -C network
  *-network:0             
       description: Wireless interface
       product: Marvell W8300 802.11 Adapter
       vendor: Marvell Technology Group Ltd.
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: wlan0
       version: 07
       serial: 00:11:95:18:08:52
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+mrv8k51 driverversion=1.58rc1+PLANET Technology Corp., latency=64 link=no multicast=yes wireless=IEEE 802.11b
       resources: irq:16 memory:fa000000-fa00ffff memory:fa010000-fa01ffff
. . . . some about the wired card is next . . .

nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             **unmanaged**
  Default:           no
  HW Address:        00:11:95:18:08:52

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes

  Wireless Access Points 

As you can see it says unmanged, which perplexes me? Please let me know if I can provide more information. Thank you. Tim.

---

