---
title: "Multiple wireless interfaces keep disconnecting/reconnecting"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by daveola on 2011-10-29
I have two wireless devices, the builtin Intel 4965 as well as an Alfi USB device, both which have worked fine.

I have a Clear hotspot which gives me a wireless network to connect to.

Whenever I connect my Ubuntu box to the Clear network, eventually it just disconnects.

Other computers seem to connect to the hotspot with no problems.

I've tried NetworkManager and wicd (both after stopping the other service) and both disconnect.

I've tried both devices, and both disconnect.

So it somewhat seems that it's not a device problem, and it's not a problem with the Clear hotspot, it seems that something on my Ubuntu box is causing the disconnect.

I grabbed the dmesg output over a disconnect, here it is:

```

[667159.504074] No probe response from AP 00:0b:6c:c7:30:47 after 500ms, disconnecting.
[667160.939859] Registered led device: iwl-phy1::radio
[667160.939908] Registered led device: iwl-phy1::assoc
[667160.939950] Registered led device: iwl-phy1::RX
[667160.939992] Registered led device: iwl-phy1::TX
[667160.972186] ADDRCONF(NETDEV_UP): eth0: link is not ready
[667161.369045] sky2 eth6: disabling interface
[667161.386594] sky2 eth6: enabling interface
[667161.386841] ADDRCONF(NETDEV_UP): eth6: link is not ready
[669916.405435] Registered led device: iwl-phy1::radio
[669916.406764] Registered led device: iwl-phy1::assoc
[669916.407390] Registered led device: iwl-phy1::RX
[669916.407541] Registered led device: iwl-phy1::TX
[669916.451188] ADDRCONF(NETDEV_UP): eth0: link is not ready
[669916.882746] Registered led device: iwl-phy1::radio
[669916.882793] Registered led device: iwl-phy1::assoc
[669916.882836] Registered led device: iwl-phy1::RX
[669916.882878] Registered led device: iwl-phy1::TX
[669916.918739] ADDRCONF(NETDEV_UP): eth0: link is not ready
[669917.080050] sky2 eth6: disabling interface
[669917.091167] sky2 eth6: enabling interface
[669917.091513] ADDRCONF(NETDEV_UP): eth6: link is not ready
[669917.487647] Registered led device: iwl-phy1::radio
[669917.487695] Registered led device: iwl-phy1::assoc
[669917.487736] Registered led device: iwl-phy1::RX
[669917.487778] Registered led device: iwl-phy1::TX
[669917.526966] ADDRCONF(NETDEV_UP): eth0: link is not ready
[669920.119669] eth0: direct probe to AP 00:0b:6c:c7:30:47 (try 1)
[669920.120521] eth0: deauthenticating from 00:0b:6c:c7:30:47 by local choice (reason=3)
[669920.121351] eth0: direct probe to AP 00:0b:6c:c7:30:47 (try 1)
[669920.321024] eth0: direct probe to AP 00:0b:6c:c7:30:47 (try 2)
[669920.323397] eth0: direct probe responded
[669920.323402] eth0: authenticate with AP 00:0b:6c:c7:30:47 (try 1)
[669920.325886] eth0: authenticated
[669920.325912] eth0: associate with AP 00:0b:6c:c7:30:47 (try 1)
[669920.331159] eth0: RX AssocResp from 00:0b:6c:c7:30:47 (capab=0x411 status=0 aid=1)
[669920.331163] eth0: associated
[669920.350987] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[669930.372025] eth0: no IPv6 routers present
[669956.492040] No probe response from AP 00:0b:6c:c7:30:47 after 500ms, disconnecting.
[669958.310076] eth0: direct probe to AP 00:0b:6c:c7:30:47 (try 1)
[669958.453825] eth0: deauthenticating from 00:0b:6c:c7:30:47 by local choice (reason=3)
[669958.739393] Registered led device: iwl-phy1::radio
[669958.741847] Registered led device: iwl-phy1::assoc
[669958.743264] Registered led device: iwl-phy1::RX
[669958.744586] Registered led device: iwl-phy1::TX
[669958.787136] ADDRCONF(NETDEV_UP): eth0: link is not ready
[669958.787187] eth0: direct probe to AP 00:0b:6c:c7:30:47 (try 1)
[669958.789483] eth0: direct probe responded
[669958.789491] eth0: authenticate with AP 00:0b:6c:c7:30:47 (try 1)
[669958.792003] eth0: authenticated
[669958.792073] eth0: associate with AP 00:0b:6c:c7:30:47 (try 1)
[669958.795296] eth0: RX AssocResp from 00:0b:6c:c7:30:47 (capab=0x411 status=13 aid=0)
[669958.795305] eth0: AP denied association (code=13)
[669958.795333] eth0: deauthenticating from 00:0b:6c:c7:30:47 by local choice (reason=3)
[669958.804934] eth0: deauthenticating from 00:0b:6c:c7:30:47 by local choice (reason=3)
[669958.904060] sky2 eth6: disabling interface
[669958.917912] sky2 eth6: enabling interface
[669958.918288] ADDRCONF(NETDEV_UP): eth6: link is not ready
[670098.590323] Registered led device: iwl-phy1::radio
[670098.590372] Registered led device: iwl-phy1::assoc
[670098.590417] Registered led device: iwl-phy1::RX
[670098.590460] Registered led device: iwl-phy1::TX
[670098.647943] ADDRCONF(NETDEV_UP): eth0: link is not ready
[670098.942507] Registered led device: iwl-phy1::radio
[670098.942555] Registered led device: iwl-phy1::assoc
[670098.942598] Registered led device: iwl-phy1::RX
[670098.942639] Registered led device: iwl-phy1::TX
[670098.988103] ADDRCONF(NETDEV_UP): eth0: link is not ready
[670098.988153] eth0: direct probe to AP 00:0b:6c:c7:30:47 (try 1)
[670098.990482] eth0: direct probe responded
[670098.990491] eth0: authenticate with AP 00:0b:6c:c7:30:47 (try 1)
[670098.994744] eth0: authenticated
[670098.994788] eth0: associate with AP 00:0b:6c:c7:30:47 (try 1)
[670098.997986] eth0: RX AssocResp from 00:0b:6c:c7:30:47 (capab=0x411 status=13 aid=0)
[670098.997995] eth0: AP denied association (code=13)
[670098.998025] eth0: deauthenticating from 00:0b:6c:c7:30:47 by local choice (reason=3)
[670099.049056] sky2 eth6: disabling interface
[670099.063548] sky2 eth6: enabling interface
[670099.064091] ADDRCONF(NETDEV_UP): eth6: link is not ready
[670099.374286] Registered led device: iwl-phy1::radio
[670099.374333] Registered led device: iwl-phy1::assoc
[670099.374376] Registered led device: iwl-phy1::RX
[670099.374416] Registered led device: iwl-phy1::TX
[670099.439192] ADDRCONF(NETDEV_UP): eth0: link is not ready
[670099.439323] eth0: direct probe to AP 00:0b:6c:c7:30:47 (try 1)
[670099.441614] eth0: direct probe responded
[670099.441622] eth0: authenticate with AP 00:0b:6c:c7:30:47 (try 1)
[670099.444119] eth0: authenticated
[670099.444165] eth0: associate with AP 00:0b:6c:c7:30:47 (try 1)
[670099.447693] eth0: RX AssocResp from 00:0b:6c:c7:30:47 (capab=0x411 status=13 aid=0)
[670099.447703] eth0: AP denied association (code=13)
[670099.447733] eth0: deauthenticating from 00:0b:6c:c7:30:47 by local choice (reason=3)
[670101.523345] eth0: direct probe to AP 00:0b:6c:c7:30:47 (try 1)
[670101.525670] eth0: direct probe responded
[670101.525678] eth0: authenticate with AP 00:0b:6c:c7:30:47 (try 1)
[670101.528394] eth0: authenticated
[670101.528447] eth0: associate with AP 00:0b:6c:c7:30:47 (try 1)
[670101.532035] eth0: RX AssocResp from 00:0b:6c:c7:30:47 (capab=0x411 status=13 aid=0)
[670101.532044] eth0: AP denied association (code=13)
[670101.532074] eth0: deauthenticating from 00:0b:6c:c7:30:47 by local choice (reason=3)
[670101.538861] eth0: direct probe to AP 00:0b:6c:c7:30:47 (try 1)
[670101.541226] eth0: direct probe responded
[670101.541234] eth0: authenticate with AP 00:0b:6c:c7:30:47 (try 1)
[670101.544063] eth0: authenticated
[670101.544110] eth0: associate with AP 00:0b:6c:c7:30:47 (try 1)
[670101.547314] eth0: RX AssocResp from 00:0b:6c:c7:30:47 (capab=0x411 status=13 aid=0)
[670101.547323] eth0: AP denied association (code=13)
[670101.547350] eth0: deauthenticating from 00:0b:6c:c7:30:47 by local choice (reason=3)
[670101.613739] eth0: direct probe to AP 00:0b:6c:c7:30:47 (try 1)
[670101.616066] eth0: direct probe responded
[670101.616075] eth0: authenticate with AP 00:0b:6c:c7:30:47 (try 1)
[670101.618589] eth0: authenticated
[670101.618642] eth0: associate with AP 00:0b:6c:c7:30:47 (try 1)
[670101.623122] eth0: RX AssocResp from 00:0b:6c:c7:30:47 (capab=0x411 status=0 aid=1)
[670101.623129] eth0: associated
[670101.641292] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[670111.901029] eth0: no IPv6 routers present
[671139.489048] No probe response from AP 00:0b:6c:c7:30:47 after 500ms, disconnecting.
[671140.898621] Registered led device: iwl-phy1::radio
[671140.898649] Registered led device: iwl-phy1::assoc
[671140.898672] Registered led device: iwl-phy1::RX
[671140.898699] Registered led device: iwl-phy1::TX
[671140.940154] ADDRCONF(NETDEV_UP): eth0: link is not ready
[671141.040043] sky2 eth6: disabling interface
[671141.053800] sky2 eth6: enabling interface
[671141.054178] ADDRCONF(NETDEV_UP): eth6: link is not ready

```

---

