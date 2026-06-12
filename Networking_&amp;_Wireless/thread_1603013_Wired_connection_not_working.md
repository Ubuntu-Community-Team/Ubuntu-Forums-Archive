---
title: "Wired connection not working"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by Chikitulfo on 2010-10-22
Hi all,

I recently moved to a student dorm in my university (RWTH Aachen) and I have an ethernet connection from my room. The thing is that I can't connect to the internet, I don't get any IP through DHCP.

I tried using wicd instead of network-manager, and doing it manually with dhclient. None of those worked (actually I don't know much about how networking works so maybe i didn't do it well with dhclient).

The weird thing is that Windows 7 gets the IP instantly and I can connect to the internet from windows. But i don't know why Ubuntu refuses to get an IP.

I don't know exactly which info should I post here, so I'll edit this post soon with the info from lshw, lspci and everything that comes to my mind.

EDIT:

lspci```
sudo lspci -vv
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)
    Subsystem: Sony Corporation Device 905e
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 30
    Region 0: Memory at d7920000 (64-bit, non-prefetchable) [size=16K]
    Region 2: I/O ports at c000 [size=256]
    Expansion ROM at d7900000 [disabled] [size=128K]
    Capabilities: [48] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=1 PME-
    Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Address: 00000000fee0200c  Data: 41a9
    Capabilities: [c0] Express (v2) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <1us, L1 <32us
            ClockPM+ Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM L0s L1 Enabled; RCB 128 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [130] Device Serial Number ff-40-3a-85-00-24-be-ff
    Kernel driver in use: sky2
    Kernel modules: sky2
```

lshw```
sudo lshw
          *-network
                description: Ethernet interface
                product: Marvell Technology Group Ltd.
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 10
                serial: 00:24:be:40:3a:85
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: irq:30 memory:d7920000-d7923fff ioport:c000(size=256) memory:d7900000-d791ffff(prefetchable)

```

ifconfig```
ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:24:be:40:3a:85  
          Dirección inet6: fe80::224:beff:fe40:3a85/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:238 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:11 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:20066 (20.0 KB)  TX bytes:1878 (1.8 KB)
          Interrupción:16 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:12 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:12 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  direcciónHW 00:22:fb:c8:cb:70  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
```

dmesg```
dmesg | grep eth
[    0.703276] sky2 eth0: addr 00:24:be:40:3a:85
[   20.860950] sky2 eth0: enabling interface
[   20.861615] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.587401] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   22.587883] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   33.371266] eth0: no IPv6 routers present

```

BTW using Ubuntu 10.04 x64 up to date

Thanks in advance

---

### Post by chili555 on 2010-10-22
The driver module sky2 has always been a bit flaky. Search Google for "sky2 ubuntu bug" and you will see. The solution is to install sk98lin. Posts #13 and following explain this. [http://ubuntuforums.org/showthread.php?t=1319116&page=2](http://ubuntuforums.org/showthread.php?t=1319116&page=2)

Make sure your model number exactly matches if it isn't 88E8040 as in the posts.

I downloaded it and got it to run after I changed the line in the install.sh file form #!/bin/sh to #!/bin/**ba**sh.

If you need further guidance or get stuck, please post back.

---

### Post by Chikitulfo on 2010-10-22
It seems that is not the problem, the sk98lin driver doesn't solve anything. I have the exact same problem whichever driver I'm using, I can't get an IP. Strange thing is that at home i can connect through ethernet.

This is the output of dhclient:
```
dhclient eth0 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:24:be:40:3a:85
Sending on   LPF/eth0/00:24:be:40:3a:85
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by chili555 on 2010-10-22
It will very difficult, maybe impossible to get manual methods to work if Network Manager is installed and running. When you let NM try to connect, what does this report?```
sudo cat /var/log/syslog | grep eth0
```

---

### Post by Chikitulfo on 2010-10-22
This is the output of cat /var/log/syslog | grep eth  right after network-manager saying that it couldn't connect.
```
Oct 22 22:01:27 tetto kernel: [    0.714358] sky2 eth0: addr 00:24:be:40:3a:85
Oct 22 22:01:27 tetto NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0, iface: eth0)
Oct 22 22:01:27 tetto NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Oct 22 22:01:27 tetto NetworkManager: <info>  (eth0): carrier is OFF
Oct 22 22:01:27 tetto NetworkManager: <info>  (eth0): new Ethernet device (driver: 'sky2')
Oct 22 22:01:27 tetto NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct 22 22:01:27 tetto NetworkManager: <info>  (eth0): now managed
Oct 22 22:01:27 tetto NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Oct 22 22:01:27 tetto NetworkManager: <info>  (eth0): bringing up device.
Oct 22 22:01:27 tetto kernel: [   21.841016] sky2 eth0: enabling interface
Oct 22 22:01:27 tetto NetworkManager: <info>  (eth0): preparing device.
Oct 22 22:01:27 tetto NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Oct 22 22:01:27 tetto NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0
Oct 22 22:01:27 tetto kernel: [   21.844699] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 22 22:01:29 tetto NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Oct 22 22:01:29 tetto NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Oct 22 22:01:29 tetto NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Oct 22 22:01:29 tetto NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Oct 22 22:01:29 tetto NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 22 22:01:29 tetto NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Oct 22 22:01:29 tetto NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Oct 22 22:01:29 tetto NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Oct 22 22:01:29 tetto NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Oct 22 22:01:29 tetto NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Oct 22 22:01:29 tetto NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Oct 22 22:01:29 tetto NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 22 22:01:29 tetto NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Oct 22 22:01:29 tetto NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Oct 22 22:01:29 tetto NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Oct 22 22:01:29 tetto NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Oct 22 22:01:29 tetto NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Oct 22 22:01:29 tetto NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Oct 22 22:01:29 tetto NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Oct 22 22:01:29 tetto NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Oct 22 22:01:29 tetto kernel: [   23.554361] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
Oct 22 22:01:29 tetto kernel: [   23.563862] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 22 22:01:29 tetto NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Oct 22 22:01:29 tetto dhclient: Listening on LPF/eth0/00:24:be:40:3a:85
Oct 22 22:01:29 tetto dhclient: Sending on   LPF/eth0/00:24:be:40:3a:85
Oct 22 22:01:30 tetto dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Oct 22 22:01:31 tetto avahi-daemon[986]: Registering new address record for fe80::224:beff:fe40:3a85 on eth0.*.
Oct 22 22:01:34 tetto dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Oct 22 22:01:40 tetto kernel: [   34.211260] eth0: no IPv6 routers present
Oct 22 22:01:42 tetto dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Oct 22 22:01:52 tetto dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Oct 22 22:02:02 tetto dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Oct 22 22:02:12 tetto dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Oct 22 22:02:15 tetto NetworkManager: <info>  (eth0): DHCP transaction took too long, stopping it.
Oct 22 22:02:15 tetto NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1290
Oct 22 22:02:15 tetto NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Oct 22 22:02:15 tetto NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Oct 22 22:02:15 tetto NetworkManager: <info>  (eth0): device state change: 7 -> 9 (reason 5)
Oct 22 22:02:15 tetto NetworkManager: <info>  Marking connection 'Auto eth0' invalid.
Oct 22 22:02:15 tetto NetworkManager: <info>  Activation (eth0) failed.
Oct 22 22:02:15 tetto NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Oct 22 22:02:15 tetto NetworkManager: <info>  (eth0): device state change: 9 -> 3 (reason 0)
Oct 22 22:02:15 tetto NetworkManager: <info>  (eth0): deactivating device (reason: 0).
```


> It will very difficult, maybe impossible to get manual methods to work if Network Manager is installed and running.
Then I should deactivate network-manager and try manually again?
I also tried it, but the result was something like "eth0 is not configured" when I did ifconfig eth0 down/up

---

### Post by chili555 on 2010-10-22
> [   23.554361] [COLOR="Red"]sky2[/COLOR] eth0: Link is up at 100 Mbps, full duplex, flow control rxWhy is this not sk98lin? Is sk98lin properly installed?```
modinfo sk98lin
```What does this do for us?```
sudo rmmod -f sky2
sudo modprobe sk98lin
```Now check syslog:```
sudo tail -n 25 /var/log/syslog
```We may need to blacklist sky2 and explicitly load sk98lin.

---

### Post by Chikitulfo on 2010-10-22
Both are installed right now as far as i know, and if I want to use sk98lin I need to load it manually.

modinfo sk98lin```
filename:       /lib/modules/2.6.32-25-generic/kernel/drivers/net/sk98lin/sk98lin.ko
version:        10.85.9.3
license:        GPL
description:    Marvell/SysKonnect Yukon Ethernet Network Driver
author:         Mirko Lindner <support@marvell.com>
srcversion:     94C0EF5E858A98A3566AC20
alias:          pci:v00001737d00001064sv*sd*bc*sc*i*
alias:          pci:v00001737d00001032sv*sd*bc*sc*i*
alias:          pci:v00001371d0000434Esv*sd*bc*sc*i*
alias:          pci:v000011ABd00005005sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004381sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004380sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004370sv*sd*bc*sc*i*
alias:          pci:v000011ABd0000436Dsv*sd*bc*sc*i*
alias:          pci:v000011ABd0000436Csv*sd*bc*sc*i*
alias:          pci:v000011ABd0000436Bsv*sd*bc*sc*i*
alias:          pci:v000011ABd0000436Asv*sd*bc*sc*i*
alias:          pci:v000011ABd00004369sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004368sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004367sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004366sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004365sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004364sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004363sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004362sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004361sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004360sv*sd*bc*sc*i*
alias:          pci:v000011ABd0000435Asv*sd*bc*sc*i*
alias:          pci:v000011ABd00004357sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004356sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004355sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004354sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004353sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004352sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004351sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004350sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004347sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004346sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004345sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004344sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004343sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004342sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004341sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004340sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004320sv*sd*bc*sc*i*
alias:          pci:v00001186d00004C00sv*sd*bc*sc*i*
alias:          pci:v00001186d00004B03sv*sd*bc*sc*i*
alias:          pci:v00001186d00004B02sv*sd*bc*sc*i*
alias:          pci:v00001186d00004B01sv*sd*bc*sc*i*
alias:          pci:v00001186d00004B00sv*sd*bc*sc*i*
alias:          pci:v00001186d00004001sv*sd*bc*sc*i*
alias:          pci:v00001148d00009E01sv*sd*bc*sc*i*
alias:          pci:v00001148d00009E00sv*sd*bc*sc*i*
alias:          pci:v00001148d00009000sv*sd*bc*sc*i*
alias:          pci:v00001148d00004320sv*sd*bc*sc*i*
alias:          pci:v000010B7d000080EBsv*sd*bc*sc*i*
alias:          pci:v000010B7d00001700sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.32-25-generic SMP mod_unload modversions 
parm:           Speed_A:array of charp
parm:           Speed_B:array of charp
parm:           AutoNeg_A:array of charp
parm:           AutoNeg_B:array of charp
parm:           DupCap_A:array of charp
parm:           DupCap_B:array of charp
parm:           FlowCtrl_A:array of charp
parm:           FlowCtrl_B:array of charp
parm:           Role_A:array of charp
parm:           Role_B:array of charp
parm:           ConType:array of charp
parm:           WolType:array of charp
parm:           IntsPerSec:array of int
parm:           Moderation:array of charp
parm:           ModerationMask:array of charp
parm:           LowLatency:array of charp
parm:           TxModeration:array of int
parm:           MsiIrq:array of charp
```


When i run ```
sudo rmmod -f sky2
sudo modprobe sk98lin
```network-manager tries to connect again. 
Should I be doing this with nm deactivated?

Last 25 lines of /var/log/syslog are these after the last commands```
Oct 22 22:39:32 tetto dhclient: All rights reserved.
Oct 22 22:39:32 tetto dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct 22 22:39:32 tetto dhclient: 
Oct 22 22:39:32 tetto NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Oct 22 22:39:32 tetto NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Oct 22 22:39:32 tetto dhclient: Listening on LPF/eth0/00:24:be:40:3a:85
Oct 22 22:39:32 tetto dhclient: Sending on   LPF/eth0/00:24:be:40:3a:85
Oct 22 22:39:32 tetto dhclient: Sending on   Socket/fallback
Oct 22 22:39:32 tetto dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Oct 22 22:39:33 tetto avahi-daemon[967]: Registering new address record for fe80::224:beff:fe40:3a85 on eth0.*.
Oct 22 22:39:38 tetto dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Oct 22 22:39:42 tetto kernel: [  240.830213] eth0: no IPv6 routers present
Oct 22 22:39:49 tetto dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Oct 22 22:39:59 tetto dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Oct 22 22:40:15 tetto dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Oct 22 22:40:18 tetto NetworkManager: <info>  (eth0): DHCP transaction took too long, stopping it.
Oct 22 22:40:18 tetto NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1956
Oct 22 22:40:18 tetto NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Oct 22 22:40:18 tetto NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Oct 22 22:40:18 tetto NetworkManager: <info>  (eth0): device state change: 7 -> 9 (reason 5)
Oct 22 22:40:18 tetto NetworkManager: <info>  Marking connection 'Auto eth0' invalid.
Oct 22 22:40:18 tetto NetworkManager: <info>  Activation (eth0) failed.
Oct 22 22:40:18 tetto NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Oct 22 22:40:18 tetto NetworkManager: <info>  (eth0): device state change: 9 -> 3 (reason 0)
Oct 22 22:40:18 tetto NetworkManager: <info>  (eth0): deactivating device (reason: 0).

```

---

### Post by chili555 on 2010-10-22
> Should I be doing this with nm deactivated?Not really; if it won't connect with NM, it probably won't connect without. Let's see:```
lsmod | grep sk
sudo ethtool eth0
```Thanks.

---

### Post by Chikitulfo on 2010-10-22
```
~$ lsmod | grep sk
sky2                   48835  0 
~$ sudo ethtool eth0
sudo: ethtool: command not found
~$ sudo aptitude search ethtool
p   ethtool                              - display or change Ethernet device settings
```

I'm already downloading the deb package of ethtool just in case is really needed.

Also as I thought the module loaded at boot is sky2, but I'm not really sure the issue I'm having here has to do with sky2...

[COLOR="DarkOrange"][B]
EDIT:[/B][/COLOR]

Installed ethtool and tried it with both sky2 and sk98lin:
```
~$ lsmod | grep sk
sky2                   48835  0 
~$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  Not reported
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: No
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pg
    Wake-on: d
    Current message level: 0x000000ff (255)
    Link detected: yes
~$ sudo rmmod -f sky2
~$ sudo modprobe sk98lin
~$ lsmod | grep sk
sk98lin               174786  1 
~$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  Not reported
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: No
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: g
    Wake-on: g
    Link detected: yes


```

---

### Post by Chikitulfo on 2010-10-22
I finally solved it!

It was a really stupid thing (I knew that all we were trying to do here was in a wrong direction).

So the thing was that the dhcp server needs the mac address of the device.
Only thing I had to do was edit /etc/dhcp3/dhclient.conf and uncomment the following line (putting my mac address instead of the one there)
```
#send dhcp-client-identifier 1:aa:bb:cc:dd:ee:ff;
```

Now I get the IP instantly and can use internet without any problems.

Also I didn't have any problem with sky2 up to the moment, but now I know I may have it in the future.

Thanks a lot for the help!

---

### Post by chili555 on 2010-10-22
Good job. Glad it's working!

---

