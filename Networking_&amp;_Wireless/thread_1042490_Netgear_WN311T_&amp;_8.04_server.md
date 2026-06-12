---
title: "Netgear WN311T &amp; 8.04 server"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by dwsdad on 2009-01-17
Let me start off by saying that Ive read the troubleshooting guide and the installation guide, but Im still having issues with my card.

Im using WICD as my Network tool.  At times it will show my wireless network.  At times it wont.  But even if it does see the wireless, it wont connect.

Here&#347; the output of dmesg:
[47352.176789] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[47352.192385] ndiswrapper: driver netmw14x (NETGEAR,11/09/2007, 3.0.4.9) loaded
[47352.197666] ndiswrapper: using IRQ 21
[47356.487571] ndiswrapper (NdisMAllocateSharedMemory:1087): couldn't allocate 4199424 bytes of un-cached DMA memory
[47356.520260]  [<f8f82fb0>] NdisMAllocateSharedMemory+0x30/0x90 [ndiswrapper]
[47356.520499]  [<f8f90f54>] mp_init+0xa4/0x1f0 [ndiswrapper]
[47356.520551]  [<f8f91179>] NdisDispatchPnp+0xd9/0xfb0 [ndiswrapper]
[47356.520692]  [<f8f8a44b>] IoAllocateIrp+0x4b/0x80 [ndiswrapper]
[47356.520730]  [<f8f8a461>] IoAllocateIrp+0x61/0x80 [ndiswrapper]
[47356.520776]  [<f8f86564>] get_current_nt_thread+0x44/0x50 [ndiswrapper]
[47356.520815]  [<f8f8a755>] IofCallDriver+0x55/0xc0 [ndiswrapper]
[47356.520858]  [<f8f8f7eb>] IoSendIrpTopDev+0xbb/0x120 [ndiswrapper]
[47356.520918]  [<f8f8fb40>] pnp_start_device+0x50/0xb0 [ndiswrapper]
[47356.520982]  [<f8f8fddf>] wrap_pnp_start_device+0x23f/0x290 [ndiswrapper]
[47356.521045]  [<f8f8fe75>] wrap_pnp_start_pci_device+0x45/0x50 [ndiswrapper]
[47356.521261]  [<f8f7f702>] loader_init+0x82/0x140 [ndiswrapper]
[47356.521283]  [<f8f8c19f>] wrap_procfs_init+0x3f/0xb0 [ndiswrapper]
[47356.521303]  [<f8f90285>] wrapndis_init+0x45/0x50 [ndiswrapper]
[47356.521328]  [<f8d730b7>] wrapper_init+0xb7/0xc2 [ndiswrapper]
[47356.526661] ndiswrapper (NdisMAllocateSharedMemory:1087): couldn't allocate 2099712 bytes of un-cached DMA memory
[47357.109520] wlan0: ethernet device 00:18:4d:20:0a:0b using NDIS driver: netmw14x, version: 0x2010419, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:2A02.5.conf
[47357.109552] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[47360.047035] usbcore: registered new interface driver ndiswrapper
[47364.500843] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[47364.650746] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[47791.960233] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[47792.468238] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[47904.557788] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[47958.786941] ndiswrapper (set_essid:53): setting essid failed (C0000001)
[47959.275764] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[48016.976543] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[48023.460897] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[48049.508048] ndiswrapper (set_essid:53): setting essid failed (C0000001)
[48049.518498] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[48066.536962] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[52900.862652] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[52911.874852] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[52912.414777] ndiswrapper (set_essid:53): setting essid failed (C0000001)
[52940.653327] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[52941.185357] ndiswrapper (set_essid:53): setting essid failed (C0000001)
[53013.929841] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[53093.747262] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[54989.862290] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[55016.388289] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[57861.952483] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[57988.995951] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[58048.372686] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[58122.603582] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[58129.493713] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[58130.025670] ndiswrapper (set_essid:53): setting essid failed (C0000001)
[58206.391417] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[58321.581478] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[58326.102582] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[58573.515616] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[58610.098151] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[58617.399731] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[58696.229532] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[58765.991208] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[58774.916547] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[58775.458366] ndiswrapper (set_essid:53): setting essid failed (C0000001)
[58852.821703] ndiswrapper (set_scan:1205): scanning failed (C0000001)
[58984.503979] ndiswrapper (set_scan:1205): scanning failed (C0000001)

Any suggestions are welcomed with open arms!

---

