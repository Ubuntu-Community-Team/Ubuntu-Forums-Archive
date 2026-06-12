---
title: "Atheros AR5005G Wireless problems"
date: 2006-02-23
forum: Networking &amp; Wireless
---

### Post by k5knt on 2006-02-23
This card is integrated on a Toshiba Satellite A105-S1014 laptop.
Ubuntu 5.10 installed, dual booting with Windows XP.

The card appears to be recognized, but I can't get it to work. 

Here is the output from the command *sudo lshw-C network*
```
*-network:0
       description: Wireless interface
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 4
       bus info: pci@02:04.0
       logical name: ath0
       version: 01
       serial: 00:11:f5:eb:77:98
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) multicast=yes wireless=IEEE 802.11g
       resources: iomemory:c0200000-c020ffff irq:20
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@02:07.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:30:20:0e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:a000-a0ff iomemory:c0211000-c02110ff irq:20

```

Here is the output from *dmesg*
```
[4294706.289000] ath_hal: module license 'Proprietary' taints kernel.
[4294706.293000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[4294706.299000] wlan: 0.8.6.0 (EXPERIMENTAL)
[4294706.303000] ath_rate_sample: 1.2
[4294706.311000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[4294706.314000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294706.902000] Build date: Oct 11 2005
[4294706.902000] Debugging version (IEEE80211)
[4294706.902000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[4294706.902000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294706.902000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[4294706.902000] ath0: mac 7.8 phy 4.5 radio 5.6
[4294706.902000] ath0: Use hw queue 1 for WME_AC_BE traffic
[4294706.902000] ath0: Use hw queue 0 for WME_AC_BK traffic
[4294706.902000] ath0: Use hw queue 2 for WME_AC_VI traffic
[4294706.902000] ath0: Use hw queue 3 for WME_AC_VO traffic
[4294706.902000] ath0: Use hw queue 8 for CAB traffic
[4294706.902000] ath0: Use hw queue 9 for beacons
[4294706.902000] Debugging version (ATH)
[4294706.902000] ath0: Atheros 5212: mem=0xc0200000, irq=20
[4294706.968000] Linux Kernel Card Services
[4294706.968000]   options:  [pci] [cardbus] [pm]
[4294706.980000] PCI: Enabling device 0000:02:06.0 (0004 -> 0006)
[4294706.980000] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 23 (level, low) -> IRQ 23
[4294706.980000] Yenta: CardBus bridge found at 0000:02:06.0 [1179:ff10]
[4294706.980000] yenta 0000:02:06.0: Preassigned resource 0 busy, reconfiguring...
[4294706.980000] Yenta: Enabling burst memory read transactions
[4294706.980000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294706.980000] Yenta: Routing CardBus interrupts to PCI
[4294706.980000] Yenta TI: socket 0000:02:06.0, mfunc 0x01111122, devctl 0x44
[4294707.202000] Yenta: ISA IRQ mask 0x0050, PCI irq 23
[4294707.202000] Socket status: 30000006
[4294708.492000] Real Time Clock Driver v1.12
[4294708.514000] input: PC Speaker
[4294709.348000] eth0: link down
[4294709.366000] NET: Registered protocol family 17
[4294774.402000] ACPI: AC Adapter [ADP0] (on-line)
[4294774.470000] ACPI: Power Button (FF) [PWRF]
[4294774.470000] ACPI: Power Button (CM) [PWRB]
[4294774.470000] ACPI: Lid Switch [LID]
[4294774.534000] ibm_acpi: ec object not found
[4294774.645000] ACPI: Battery Slot [BAT0] (battery present)
[4294782.924000] apm: BIOS not found.
[4294783.466000] cs: IO port probe 0x100-0x4ff: excluding 0x1f0-0x1f7 0x3f0-0x3f7 0x4d0-0x4d7
[4294783.469000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[4294783.470000] cs: IO port probe 0xa00-0xaff: clean.
[4294783.837000] Bluetooth: Core ver 2.7
[4294783.837000] NET: Registered protocol family 31
[4294783.837000] Bluetooth: HCI device and connection manager initialized
[4294783.837000] Bluetooth: HCI socket layer initialized
[4294783.859000] Bluetooth: L2CAP ver 2.7
[4294783.859000] Bluetooth: L2CAP socket layer initialized
[4294783.889000] Bluetooth: RFCOMM ver 1.5
[4294783.889000] Bluetooth: RFCOMM socket layer initialized
[4294783.889000] Bluetooth: RFCOMM TTY layer initialized
[4294823.631000] NET: Registered protocol family 10
[4294823.631000] Disabled Privacy Extensions on device c02eb280(lo)
[4294823.631000] IPv6 over IPv4 tunneling driver
[4294834.098000] eth0: no IPv6 routers present
[4295117.311000]     ACPI-0299: *** Error: No installed handler for fixed event [00000000]

```

And here is the output from *ifconfig*
[CODE]ath0      Link encap:Ethernet  HWaddr 00:11:F5:EB:77:98  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Memory:dcc60000-dcc70000 

eth0      Link encap:Ethernet  HWaddr 00:A0:D1:30:20:0E  
          inet6 addr: fe80::2a0:d1ff:fe30:200e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3631 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3631 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:330176 (322.4 KiB)  TX bytes:330176 (322.4 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
/CODE]

This is my first laptop and my first attempt at wireless. I can connect fine using my ethernet cable. 

I'm using the GNOME desktop and in the Connection Properties only eth0 and lo show up in the Connection Name list.

The Network Settings show both the Wireless connection and Ethernet connection. I have tried having both active and deactivating the ethernet.  In the Default gateway device list there is no listing for ath0, just eth0.


Kent

---

### Post by phanboy_iv on 2006-02-23
Open a terminal and try this:
> sudo iwconfig ath0 essid "your essid here"
entering your wifi essid where indicated.

Is WEP encryption required here?

---

### Post by Lambert on 2006-02-23
See if you can find any help here.

[http://madwifi.org/wiki/UserDocs/MiniPCI](http://madwifi.org/wiki/UserDocs/MiniPCI)

---

### Post by k5knt on 2006-02-23
[QUOTE=phanboy_iv]Open a terminal and try this:

entering your wifi essid where indicated.[/quote]
Done. This is the result I get if I type iwconfig:
```

lo        no wireless extensions.

eth0    no wireless extensions.

ath0    IEEE 802.11g  ESSID:"frazier.lan"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:13:10:06:FF:F5   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:283  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0     no wireless extensions.


```

> Is WEP encryption required here?

Yes. WPA

Still not connecting.

---

### Post by k5knt on 2006-02-23
[QUOTE=Lambert]See if you can find any help here.

[http://madwifi.org/wiki/UserDocs/MiniPCI](http://madwifi.org/wiki/UserDocs/MiniPCI)[/QUOTE]

I tried the ```
modprobe ath_pci rfkill=0
```
but nothing seems to be any different.

---

### Post by k5knt on 2006-02-24
**[SIZE="7"]PROBLEM SOLVED[/SIZE]**

After thinking over the problem, I remembered that my initial install was done without any network connection (it was done while my daughter was playing in a park) ;) I decided to do a reinstall with my laptop connected to my router (a Linksys WRT54G Broadband). I left the wireless switch on the laptop in the "off" position during the install. My NIC was autodetected and autoconfigured.

Upon first boot, I was prompted to install updates. I didn't remember this prompt on my first install even after geting my NIC working.

Follwing the update I made the following changes to my router's configuration:

Wireless Mode from "G" to "Mixed"
Security Mode from "WPA Personal" to "Disabled"

I then configured my wireless card in Ubuntu, agian it was autodetected and autoconfigured. **My wireless now works!!!:-D **

Next I changed the security mode on the router from "Disabled" to WEP, made the change to my wireless configuration in Ubuntu and I still have wireless!!

Thanks to everyone for the help. 

Kent

---

