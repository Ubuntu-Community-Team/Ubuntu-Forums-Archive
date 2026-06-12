---
title: "wifi problems and computer crash"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by tal32123 on 2010-07-29
My sister has an Acer aspire laptop with Ubuntu and for some reason the wifi turns on and off constantly and then crashes after about an hour of use. Please help as I have no idea what is causing this.

---

### Post by marc.verwerft on 2010-07-30
Logs for extra info would be good.

Try posting the output of dmesg, /sys/var/log/messages and syslog, next to the exact version of the distribution etc.

Regards,

Marc

---

### Post by marc.verwerft on 2010-07-30
Should be /var/log/messages and /var/log/syslog instead of /sys/var/log/messages

My thoughts go faster then my fingers ...

---

### Post by tal32123 on 2010-07-30
> **marc.verwerft said:**
> Should be /var/log/messages and /var/log/syslog instead of /sys/var/log/messages

My thoughts go faster then my fingers ...

thats the dmesg

[ 15.879241] iwl3945 0000:05:00.0: loaded firmware version 15.32.2.9 
[ 15.947666] yenta_cardbus 0000:06:04.0: ISA IRQ mask 0x0cf8, PCI irq 16 
[ 15.947674] yenta_cardbus 0000:06:04.0: Socket status: 30000006 
[ 15.947679] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #07 to #0a 
[ 15.947692] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge I/O window: 0x7000 - 0x7fff 
[ 15.947697] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x7000-0x7fff: clean. 
[ 15.947980] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd00fffff 
[ 15.947984] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff 
[ 15.983665] Registered led device: iwl-phy0::radio 
[ 15.983696] Registered led device: iwl-phy0::assoc 
[ 15.983717] Registered led device: iwl-phy0::RX 
[ 15.983739] Registered led device: iwl-phy0::TX 
[ 16.110444] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 16.228741] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000 
[ 16.258976] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8 
[ 16.313886] ppdev: user-space parallel port driver 
[ 16.411384] fb0: inteldrmfb frame buffer device 
[ 16.411388] registered panic notifier 
[ 16.411398] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0 
[ 16.411451] alloc irq_desc for 22 on node -1 
[ 16.411455] alloc kstat_irqs on node -1 
[ 16.411464] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22 
[ 16.411502] HDA Intel 0000:00:1b.0: setting latency timer to 64 
[ 16.415404] vga16fb: initializing 
[ 16.415409] vga16fb: mapped to 0xc00a0000 
[ 16.415414] vga16fb: not registering due to another framebuffer present 
[ 16.419061] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean. 
[ 16.421283] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7 
[ 16.422202] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean. 
[ 16.422932] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean. 
[ 16.423862] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean. 
[ 16.522520] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9 
[ 16.534264] Console: switching to colour frame buffer device 160x50 
[ 26.676613] wlan0: deauthenticating from 02:1e:8c:37:8b:65 by local choice (reason=3) 
[ 26.678903] wlan0: direct probe to AP 02:1e:8c:37:8b:65 (try 1) 
[ 26.877097] wlan0: direct probe to AP 02:1e:8c:37:8b:65 (try 2) 
[ 27.076064] wlan0: direct probe to AP 02:1e:8c:37:8b:65 (try 3) 
[ 27.276065] wlan0: direct probe to AP 02:1e:8c:37:8b:65 timed out 
[ 33.354669] wlan0: direct probe to AP 02:1e:8c:37:92:2a (try 1) 
[ 33.552064] wlan0: direct probe to AP 02:1e:8c:37:92:2a (try 2) 
[ 33.752069] wlan0: direct probe to AP 02:1e:8c:37:92:2a (try 3) 
[ 33.952068] wlan0: direct probe to AP 02:1e:8c:37:92:2a timed out 
[ 34.177105] __ratelimit: 9 callbacks suppressed 
[ 34.177118] operapluginwrap[1395]: segfault at 0 ip (null) sp bfcd6c6c error 4 in libuuid.so.1.3.0[110000+3000] 
[ 34.284274] operapluginwrap[1417]: segfault at 0 ip (null) sp bfd8f5ec error 4 in libXt.so.6.0.0[110000+4f000] 
[ 34.312220] operapluginwrap[1428]: segfault at 0 ip (null) sp bfdda75c error 4 in libX11.so.6.3.0[110000+119000] 
[ 34.385213] operapluginwrap[1450]: segfault at 0 ip (null) sp bf8e998c error 4 in libm-2.11.1.so[110000+24000] 
[ 40.050240] wlan0: direct probe to AP 02:1e:8c:37:92:2a (try 1) 
[ 40.248136] wlan0: direct probe to AP 02:1e:8c:37:92:2a (try 2) 
[ 40.448036] wlan0: direct probe to AP 02:1e:8c:37:92:2a (try 3) 
[ 40.648040] wlan0: direct probe to AP 02:1e:8c:37:92:2a timed out 
[ 46.753932] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 46.756413] wlan0: direct probe responded 
[ 46.756421] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 46.758554] wlan0: authenticated 
[ 46.758594] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 46.761146] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 46.761153] wlan0: associated 
[ 46.766450] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 56.836104] wlan0: no IPv6 routers present 
[ 141.858588] iwl3945 0000:05:00.0: Microcode SW error detected. Restarting 0x82000008. 
[ 141.943615] Registered led device: iwl-phy0::radio 
[ 141.948057] Registered led device: iwl-phy0::assoc 
[ 141.948185] Registered led device: iwl-phy0::RX 
[ 141.952496] Registered led device: iwl-phy0::TX 
[ 142.721141] CE: hpet increasing min_delta_ns to 15000 nsec 
[ 162.172182] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away. 
[ 185.369144] CE: hpet increasing min_delta_ns to 22500 nsec 
[ 226.056692] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away. 
[ 764.209125] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424) 
[ 764.209158] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.WMID.Z000] (Node f70128b8), AE_TIME 
[ 764.209236] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.WMID.WMBA] (Node f7012ae0), AE_TIME 
[ 776.317231] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 777.256772] Registered led device: iwl-phy0::radio 
[ 777.256798] Registered led device: iwl-phy0::assoc 
[ 777.256820] Registered led device: iwl-phy0::RX 
[ 777.256842] Registered led device: iwl-phy0::TX 
[ 777.269780] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 790.585590] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 790.612820] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 790.615254] wlan0: direct probe responded 
[ 790.615261] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 790.617105] wlan0: authenticated 
[ 790.617129] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 790.620477] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 790.620482] wlan0: associated 
[ 790.622188] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 800.852166] wlan0: no IPv6 routers present 
[ 806.349195] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 807.185477] Registered led device: iwl-phy0::radio 
[ 807.185911] Registered led device: iwl-phy0::assoc 
[ 807.186146] Registered led device: iwl-phy0::RX 
[ 807.186367] Registered led device: iwl-phy0::TX 
[ 807.196910] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 814.665701] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 814.702918] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 814.900147] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 2) 
[ 814.902713] wlan0: direct probe responded 
[ 814.902721] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 814.904600] wlan0: authenticated 
[ 814.904645] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 814.907099] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 814.907108] wlan0: associated 
[ 814.911609] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 825.652066] wlan0: no IPv6 routers present 
[ 836.305184] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 837.192891] Registered led device: iwl-phy0::radio 
[ 837.193012] Registered led device: iwl-phy0::assoc 
[ 837.193057] Registered led device: iwl-phy0::RX 
[ 837.193100] Registered led device: iwl-phy0::TX 
[ 837.205661] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 843.874902] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 843.889114] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 843.892405] wlan0: direct probe responded 
[ 843.892415] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 843.895753] wlan0: authenticated 
[ 843.895794] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 843.898271] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 843.898279] wlan0: associated 
[ 843.900470] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 854.100116] wlan0: no IPv6 routers present 
[ 866.293240] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 867.165194] Registered led device: iwl-phy0::radio 
[ 867.165314] Registered led device: iwl-phy0::assoc 
[ 867.165359] Registered led device: iwl-phy0::RX 
[ 867.165404] Registered led device: iwl-phy0::TX 
[ 867.185655] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 873.881091] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 873.917754] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 874.116197] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 2) 
[ 874.120267] wlan0: direct probe responded 
[ 874.120279] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 874.122911] wlan0: authenticated 
[ 874.122958] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 874.125923] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 874.125932] wlan0: associated 
[ 874.129606] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 884.472081] wlan0: no IPv6 routers present 
[ 896.324287] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 897.193603] Registered led device: iwl-phy0::radio 
[ 897.193656] Registered led device: iwl-phy0::assoc 
[ 897.193701] Registered led device: iwl-phy0::RX 
[ 897.193747] Registered led device: iwl-phy0::TX 
[ 897.213077] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 898.854505] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 898.890430] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 898.893177] wlan0: direct probe responded 
[ 898.893188] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 898.895699] wlan0: authenticated 
[ 898.895753] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 898.901514] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 898.901524] wlan0: associated 
[ 898.905118] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 909.828106] wlan0: no IPv6 routers present 
[ 926.336337] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 927.173661] Registered led device: iwl-phy0::radio 
[ 927.173688] Registered led device: iwl-phy0::assoc 
[ 927.173710] Registered led device: iwl-phy0::RX 
[ 927.173734] Registered led device: iwl-phy0::TX 
[ 927.194034] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 928.835574] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 928.870841] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 928.873307] wlan0: direct probe responded 
[ 928.873319] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 928.875192] wlan0: authenticated 
[ 928.875240] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 928.877707] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 928.877714] wlan0: associated 
[ 928.881792] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 941.556178] wlan0: no IPv6 routers present 
[ 956.313191] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 957.706486] Registered led device: iwl-phy0::radio 
[ 957.706607] Registered led device: iwl-phy0::assoc 
[ 957.706652] Registered led device: iwl-phy0::RX 
[ 957.706695] Registered led device: iwl-phy0::TX 
[ 957.725911] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 964.429367] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 964.461755] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 964.464270] wlan0: direct probe responded 
[ 964.464280] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 964.468274] wlan0: authenticated 
[ 964.468368] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 964.474924] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 964.474932] wlan0: associated 
[ 964.481202] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 974.672122] wlan0: no IPv6 routers present 
[ 986.321224] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 987.192752] Registered led device: iwl-phy0::radio 
[ 987.192804] Registered led device: iwl-phy0::assoc 
[ 987.192848] Registered led device: iwl-phy0::RX 
[ 987.192893] Registered led device: iwl-phy0::TX 
[ 987.214107] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 988.852907] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 988.888713] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 989.088070] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 2) 
[ 989.288304] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 3) 
[ 989.488085] wlan0: direct probe to AP 00:21:63:4c:c3:9d timed out 
[ 1030.217551] Registered led device: iwl-phy0::radio 
[ 1030.221348] Registered led device: iwl-phy0::assoc 
[ 1030.222310] Registered led device: iwl-phy0::RX 
[ 1030.222811] Registered led device: iwl-phy0::TX 
[ 1030.232795] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 1030.270081] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 1030.468193] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 2) 
[ 1030.669145] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 3) 
[ 1030.672580] wlan0: direct probe responded 
[ 1030.672592] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1030.674511] wlan0: authenticated 
[ 1030.674557] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1030.677044] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 1030.677053] wlan0: associated 
[ 1030.683771] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 1040.928102] wlan0: no IPv6 routers present 
[ 1054.549226] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1060.166641] Registered led device: iwl-phy0::radio 
[ 1060.166761] Registered led device: iwl-phy0::assoc 
[ 1060.166807] Registered led device: iwl-phy0::RX 
[ 1060.171840] Registered led device: iwl-phy0::TX 
[ 1060.179936] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 1061.847169] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1061.847233] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 1062.045075] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 2) 
[ 1062.245204] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 3) 
[ 1062.445201] wlan0: direct probe to AP 00:21:63:4c:c3:9d timed out 
[ 1104.210322] Registered led device: iwl-phy0::radio 
[ 1104.211227] Registered led device: iwl-phy0::assoc 
[ 1104.211852] Registered led device: iwl-phy0::RX 
[ 1104.212487] Registered led device: iwl-phy0::TX 
[ 1104.225107] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 1104.225149] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 1104.425044] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 2) 
[ 1104.625162] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 3) 
[ 1104.628183] wlan0: direct probe responded 
[ 1104.628195] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1104.630034] wlan0: authenticated 
[ 1104.630079] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1104.632520] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 1104.632528] wlan0: associated 
[ 1104.637068] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 1105.017209] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1111.632417] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 1111.832043] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 2) 
[ 1112.032059] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 3) 
[ 1112.232081] wlan0: direct probe to AP 00:21:63:4c:c3:9d timed out 
[ 1114.710732] wlan0: no IPv6 routers present 
[ 1118.288354] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 1118.292905] wlan0: direct probe responded 
[ 1118.292915] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1118.297466] wlan0: authenticated 
[ 1118.297515] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1118.299969] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 1118.299978] wlan0: associated 
[ 1133.320087] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1134.221543] Registered led device: iwl-phy0::radio 
[ 1134.221597] Registered led device: iwl-phy0::assoc 
[ 1134.221643] Registered led device: iwl-phy0::RX 
[ 1134.221689] Registered led device: iwl-phy0::TX 
[ 1134.237573] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 1184.192814] Registered led device: iwl-phy0::radio 
[ 1184.192866] Registered led device: iwl-phy0::assoc 
[ 1184.192910] Registered led device: iwl-phy0::RX 
[ 1184.192955] Registered led device: iwl-phy0::TX 
[ 1184.209401] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 1190.897245] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1190.911105] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 1190.914368] wlan0: direct probe responded 
[ 1190.914379] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1190.916379] wlan0: authenticated 
[ 1190.916427] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1190.918879] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 1190.918884] wlan0: associated 
[ 1190.920294] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 1201.820127] wlan0: no IPv6 routers present 
[ 1213.297125] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1214.182426] Registered led device: iwl-phy0::radio 
[ 1214.182492] Registered led device: iwl-phy0::assoc 
[ 1214.182515] Registered led device: iwl-phy0::RX 
[ 1214.182541] Registered led device: iwl-phy0::TX 
[ 1214.193108] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 1220.879441] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1220.915308] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 1221.112089] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 2) 
[ 1221.116532] wlan0: direct probe responded 
[ 1221.116542] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1221.118408] wlan0: authenticated 
[ 1221.118457] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1221.121204] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 1221.121213] wlan0: associated 
[ 1221.124148] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 1231.604067] wlan0: no IPv6 routers present 
[ 1243.317081] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1244.201632] Registered led device: iwl-phy0::radio 
[ 1244.201725] Registered led device: iwl-phy0::assoc 
[ 1244.201748] Registered led device: iwl-phy0::RX 
[ 1244.203276] Registered led device: iwl-phy0::TX 
[ 1244.218354] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 1250.917535] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1250.957104] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 1250.960216] wlan0: direct probe responded 
[ 1250.960226] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1250.966901] wlan0: authenticated 
[ 1250.966953] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1250.976217] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 1250.976226] wlan0: associated 
[ 1250.978964] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 1261.140057] wlan0: no IPv6 routers present 
[ 1273.305061] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1274.197536] Registered led device: iwl-phy0::radio 
[ 1274.197563] Registered led device: iwl-phy0::assoc 
[ 1274.197586] Registered led device: iwl-phy0::RX 
[ 1274.197609] Registered led device: iwl-phy0::TX 
[ 1274.213052] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 1280.900189] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1280.934773] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 1281.133085] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 2) 
[ 1281.333131] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 3) 
[ 1281.335924] wlan0: direct probe responded 
[ 1281.335932] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1281.337760] wlan0: authenticated 
[ 1281.337801] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1281.340278] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 1281.340287] wlan0: associated 
[ 1281.344350] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 1291.608112] wlan0: no IPv6 routers present 
[ 1303.336216] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1304.202955] Registered led device: iwl-phy0::radio 
[ 1304.203075] Registered led device: iwl-phy0::assoc 
[ 1304.203124] Registered led device: iwl-phy0::RX 
[ 1304.203167] Registered led device: iwl-phy0::TX 
[ 1304.223005] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 1316.133561] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1316.167584] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 1316.173884] wlan0: direct probe responded 
[ 1316.173897] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1316.176132] wlan0: authenticated 
[ 1316.176180] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1316.180193] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 1316.180202] wlan0: associated 
[ 1316.183898] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 1326.232030] wlan0: no IPv6 routers present 
[ 1333.329221] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1334.193611] Registered led device: iwl-phy0::radio 
[ 1334.193708] Registered led device: iwl-phy0::assoc 
[ 1334.193754] Registered led device: iwl-phy0::RX 
[ 1334.193798] Registered led device: iwl-phy0::TX 
[ 1334.213831] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 1340.927833] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1340.963952] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 1340.967187] wlan0: direct probe responded 
[ 1340.967197] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1340.969108] wlan0: authenticated 
[ 1340.969147] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1340.971599] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 1340.971608] wlan0: associated 
[ 1340.974383] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 1351.788112] wlan0: no IPv6 routers present 
[ 1363.309179] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1364.185723] Registered led device: iwl-phy0::radio 
[ 1364.185778] Registered led device: iwl-phy0::assoc 
[ 1364.185823] Registered led device: iwl-phy0::RX 
[ 1364.185865] Registered led device: iwl-phy0::TX 
[ 1364.194052] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 1370.886412] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1370.924550] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 1371.124194] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 2) 
[ 1371.128240] wlan0: direct probe responded 
[ 1371.128252] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1371.132202] wlan0: authenticated 
[ 1371.132251] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1371.134801] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 1371.134811] wlan0: associated 
[ 1371.136777] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 1382.060114] wlan0: no IPv6 routers present 
[ 1393.316189] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1394.189497] Registered led device: iwl-phy0::radio 
[ 1394.189525] Registered led device: iwl-phy0::assoc 
[ 1394.189547] Registered led device: iwl-phy0::RX 
[ 1394.189569] Registered led device: iwl-phy0::TX 
[ 1394.210277] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 1400.897145] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1400.932198] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 1401.133167] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 2) 
[ 1401.332111] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 3) 
[ 1401.532064] wlan0: direct probe to AP 00:21:63:4c:c3:9d timed out 
[ 1407.535815] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 1407.732206] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 2) 
[ 1407.932027] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 3) 
[ 1407.934437] wlan0: direct probe responded 
[ 1407.934442] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1407.936270] wlan0: authenticated 
[ 1407.936295] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1407.938722] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 1407.938727] wlan0: associated 
[ 1407.940241] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 1418.532083] wlan0: no IPv6 routers present 
[ 1423.341197] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1424.196353] Registered led device: iwl-phy0::radio 
[ 1424.196472] Registered led device: iwl-phy0::assoc 
[ 1424.196517] Registered led device: iwl-phy0::RX 
[ 1424.196560] Registered led device: iwl-phy0::TX 
[ 1424.209865] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 1430.898299] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1430.934275] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 1430.936745] wlan0: direct probe responded 
[ 1430.936753] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1430.938585] wlan0: authenticated 
[ 1430.938613] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1430.941055] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 1430.941062] wlan0: associated 
[ 1430.942555] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[ 1441.644065] wlan0: no IPv6 routers present 
[ 1453.317082] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1454.193888] Registered led device: iwl-phy0::radio 
[ 1454.196147] Registered led device: iwl-phy0::assoc 
[ 1454.197762] Registered led device: iwl-phy0::RX 
[ 1454.199172] Registered led device: iwl-phy0::TX 
[ 1454.211326] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 1460.913248] wlan0: deauthenticating from 00:21:63:4c:c3:9d by local choice (reason=3) 
[ 1460.943347] wlan0: direct probe to AP 00:21:63:4c:c3:9d (try 1) 
[ 1460.948194] wlan0: direct probe responded 
[ 1460.948206] wlan0: authenticate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1460.950487] wlan0: authenticated 
[ 1460.950539] wlan0: associate with AP 00:21:63:4c:c3:9d (try 1) 
[ 1460.953108] wlan0: RX AssocResp from 00:21:63:4c:c3:9d (capab=0x401 status=0 aid=2) 
[ 1460.953117] wlan0: associated 
[ 1460.966745] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

---

