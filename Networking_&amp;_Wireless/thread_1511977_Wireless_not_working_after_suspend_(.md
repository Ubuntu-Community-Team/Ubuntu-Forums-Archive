---
title: "Wireless not working after suspend ("
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by pino_s on 2010-06-17
hello,

After upgrade from Hardy to Lucid, wireless card (Atheros Communications Inc. AR5212 ) was extremely slow and not really functional. I installed the madwifi driver following the instructions from Ubuntu Wiki and wireless works now. But, after suspend Network Manager nor Wicd could scan for any wirelss networks.

 I found a workaround: in console, run "dhclient" and, magically, while the scan for Ip address is going on, suddenly also Network Manager starts connecting to my default access point!

I guess this could be some acpi issue but i don't have a clue really :)

Any help to solve this problem is appreciated!

Cheers.

---

### Post by Sealbhach on 2010-06-18
I have the same problem with wicd. After suspend wicd will not connect to the network, either wired or wireless. Rebooting gets the connection up.

I switched to wicd because network manager kept dropping the connection after 20 minutes or so.

Prior to this I had been using Lucid from the Beta and networking worked fine. But I did a fresh reinstall with the Ubuntu minimal CD two days ago and have had networking issues since then.

uname -a
```
Linux vaio 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

```lshw -C network
```
  *-network               
       description: Wireless interface
       product: **PRO/Wireless 4965 AG or AGN** [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 61
       serial: 00:1d:e0:14:32:35
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.66 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:fa000000-fa001fff
  *-network
       description: Ethernet interface
     [B]  product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.[/B]
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 16
       serial: 00:24:be:43:e1:ee
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:30 memory:fc000000-fc003fff ioport:6000(size=256)
  
*-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```iwconfig
```
wlan0     IEEE 802.11abgn  ESSID:"BTHomeHub-045E"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:68:E3:7D:EB   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          **Power Management:off**
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```Maybe it's the Power Management setting?

.

---

### Post by pino_s on 2010-06-21
allright, the issue is solved for me by following the solution from [here ]("https://wiki.ubuntu.com/IntrepidReleaseNotes#Wireless%20doesn%27t%20work%20after%20suspend%20with%20ath_pci%20driver"):

> 
Wireless devices that use the ath_pci kernel  driver, such as the Atheros AR5212 wireless card, will be unable to  connect to the network after using suspend and resume.  To work around  this issue, users can create a file /etc/pm/config.d/madwifi  containing the single line: 
   SUSPEND_MODULES=ath_pciThis will cause the module to be unloaded before  suspend and reloaded on resume. cheers! :)

---

