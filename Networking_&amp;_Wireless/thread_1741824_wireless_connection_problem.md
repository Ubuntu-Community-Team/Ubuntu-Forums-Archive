---
title: "wireless connection problem"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by mighty_wolf on 2011-04-28
Hey guys, I have the following problem concerning my wireless 802.11g connection

well i performed perfectly all the steps of ndiswrapper and nothing   seems wrong i also did the checks (It's the first time i installed   ndiswrapper) and all seems ok!

Now I am trying to connect to my router which is using WPA2 personal   security. If i connect directly to the D- Link router then it prompts me   to WEP 128. So to get internet in a proper way i try to connect  through  a hidden wireless network which prompts me to WPA2 personal  (exactly  the security of the router). I type my key and after some  minutes it  prompts me again to the same prompt without having finished  the  connection ( I am still offline)! I changed security so that i can   connect directly with WEP128 but it always happens the same! 

What should i do?

Here there are the checks:

spiros@spiros-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 15
       serial: 00:13:d4:21:62:af
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes
       resources: irq:28 memory:d2efc000-d2efffff ioport:c800(size=256) memory:d2ec0000-d2edffff(prefetchable)
  *-network
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 15
       serial: 00:13:d4:21:7a:0a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes
       resources: irq:29 memory:d2dfc000-d2dfffff ioport:b800(size=256) memory:d2dc0000-d2ddffff(prefetchable)
  *-network
       description: Wireless interface
       product: 88W8310 and 88W8000G [Libertas] 802.11g client chipset
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 07
       serial: 00:13:d4:21:63:db
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+mrv8ka51   driverversion=1.56+Marvell,05/20/2004,2.3.0.19 latency=64 multicast=yes   wireless=IEEE 802.11b
       resources: irq:20 memory:d2ce0000-d2ceffff memory:d2cb0000-d2cbffff
spiros@spiros-desktop:~$ dmesg | grep -e ndis -e wlan
[  293.562348] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[  293.610857] ndiswrapper: driver mrv8ka51 (Marvell,05/20/2004,2.3.0.19) loaded
[  293.611090] ndiswrapper 0000:01:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[  293.611375] ndiswrapper: using IRQ 20
[  293.873768] wlan0: ethernet device 00:13:d4:21:63:db using NDIS   driver: mrv8ka51, version: 0x2030006, NDIS version: 0x501, vendor:   'Marvell 802.11 Driver', 11AB:1FA7.5.conf
[  293.873794] ndiswrapper (set_iw_encr_mode:70:cool:: setting encryption mode to 6 failed (C00000BB)
[  293.873805] wlan0: encryption modes supported: WEP; TKIP with WPA
[  293.874917] usbcore: registered new interface driver ndiswrapper
[  295.181471] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  536.301785] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  536.306563] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  546.364014] wlan0: no IPv6 routers present

---

