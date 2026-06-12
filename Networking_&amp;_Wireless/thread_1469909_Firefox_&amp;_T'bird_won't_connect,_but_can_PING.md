---
title: "Firefox &amp; T'bird won't connect, but can PING"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by flopwich on 2010-05-02
I have an Acer Aspire One that worked fine with version 9.* of Ubuntu, then I upgraded to v10.1.  Now Thunderbird, Evolution, and Firefox (Namoroku?) can't connect, either wirelessly or by Ethernet cable, to my ISP.  I get error messages like "connection timed out" or "cannot find {link}".  I can PING my ISP from Terminal, though, and I have the machine set up for dual boot with Windows 7 and  Firefox works fine under Windows.

I have no idea what to look for or where to start.  Any help would be greatly appreciated.

Here's the output from sudo lshw -c net

	 	 [FONT=DejaVu Sans, sans-serif][SIZE=2]*-network               [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]description: Ethernet interface [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]product: Atheros AR8132 / L1c Gigabit Ethernet Adapter [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]vendor: Atheros Communications [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]physical id: 0 [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]bus info: pci@0000:01:00.0 [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]logical name: eth0 [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]version: c0 [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]serial: 70:5a:b6:21:f3:fd [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]capacity: 100MB/s [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]width: 64 bits [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]clock: 33MHz [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]resources: irq:27 memory:57000000-5703ffff ioport:5000(size=128) [/SIZE][/FONT] 
   [FONT=DejaVu Sans, sans-serif][SIZE=2]*-network [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]description: Wireless interface [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]product: AR9285 Wireless Network Adapter (PCI-Express) [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]vendor: Atheros Communications Inc. [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]physical id: 0 [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]bus info: pci@0000:02:00.0 [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]logical name: wlan0 [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]version: 01 [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]serial: c4:17:fe:62:77:06 [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]width: 64 bits [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]clock: 33MHz [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]configuration: broadcast=yes driver=ath9k ip=192.168.2.100 latency=0 multicast=yes wireless=IEEE 802.11bgn [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]resources: irq:17 memory:56000000-5600ffff [/SIZE][/FONT]

---

### Post by ajpearson on 2010-06-08
I have the same problem - just posted a separate thread. I have a mobile dongle that is active ok but Firefox & Thunderbird do not seem to recognise or find it.

If I find an answer I will get back to you - but will keep an eye on your thread with interest.

Good Luck

Andrew

---

### Post by Iowan on 2010-06-08
The wireless adapter is showing an IP address - good start...
Are you pinging ISP by name or IP address (can you ping internet by IP address)?
Check (from a terminal) **less /etc/resolv.conf**

---

