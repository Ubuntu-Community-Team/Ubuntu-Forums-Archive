---
title: "Please help: wifi problem"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by prajakta on 2009-01-14
I posted in one of the threads for my wifi problem. Tried googling and several troubleshooting guides, no success. Tried installing ndisgtk and windows drivers from the drivers CD, but nothing worked. Posting the problem here with some more details here:

I have Broadcom 4312 (14e4:4315) wireless in a lenovo 3000 G430 laptop.
It worked fine when I installed Intrepid. Once I closed the wireless network switch of my laptop when it was connected to wireless. After that it never worked. I do not know whether it has created a hardware problem.

I get the following outputs for various commands:

$sudo iwlist scan
eth1 Failed to read scan data : Invalid argument

$sudo iwconfig
eth1 IEEE 802.11bg ESSID:"" Nickname:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Bit Rate:54 Mb/s Tx-Power:off
Retry min limit:7 RTS thr:off Fragment thrff
Power Managementmode:All packets received
Link Quality=5/5 Signal level=0 dBm Noise level=0 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

$sudo ifconfig

eth1      Link encap:Ethernet  HWaddr 00:21:00:56:a2:ba  
          inet6 addr: fe80::221:ff:fe56:a2ba/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

$sudo lshw -C Network
 *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:56:a2:ba
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

$sudo lsmod|grep ndis
ndiswrapper           196380  0 
usbcore               148848  5 uvcvideo,ndiswrapper,ehci_hcd,uhci_hcd


Thanks in advance for any help.

---

