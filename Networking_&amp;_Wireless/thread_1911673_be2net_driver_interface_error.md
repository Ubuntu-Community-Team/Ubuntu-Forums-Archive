---
title: "be2net driver interface error"
date: 2012-01-19
forum: Networking &amp; Wireless
---

### Post by hasan.ovuc on 2012-01-19
I installed ubuntu 10.04 lts on hp blade 460 G7. I  get lots of interface errors. I can't get updated version of be2net  drive. I need emulex driver repository address because I tested same  hardware with rhel latest edition server. There is no problem on the  interface. I put details of module in below. I don't want to change my  os due to this problem.
 Rhel Server
p65:~# modinfo be2net
filename:       /lib/modules/2.6.32-33-server/kernel/drivers/net/benet/be2net.ko
license:        GPL
author:         ServerEngines Corporation
description:    ServerEngines BladeEngine2 10Gbps NICDriver 2.101.205
version:        2.101.205
srcversion:     3CA06454C512DB32ED03AC4
alias:          pci:v000019A2d00000710sv*sd*bc*sc*i*
alias:          pci:v000019A2d00000701sv*sd*bc*sc*i*
alias:          pci:v000019A2d00000700sv*sd*bc*sc*i*
alias:          pci:v000019A2d00000221sv*sd*bc*sc*i*
alias:          pci:v000019A2d00000211sv*sd*bc*sc*i*
depends:
vermagic:       2.6.32-33-server SMP mod_unload modversions
parm:           rx_frag_size:Size of a fragment that holds rcvd data. (uint)
65:~#
65:~# uname -a
Linux p65 2.6.32-33-server #70-Ubuntu SMP Thu Jul 7 22:28:30 UTC 2011 x86_64 GNU/Linux
p65:~#
bond0     Link encap:Ethernet  HWaddr 9c:8e:99:27:07:48
          inet addr:192.168.40.65  Bcast:192.168.40.255  Mask:255.255.255.0
          inet6 addr: fe80::9e8e:99ff:fe27:748/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:161810096 errors:3001138465 dropped:0 overruns:0 frame:2944229021
          TX packets:239462984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:82049476598 (82.0 GB)  TX bytes:277454648737 (277.4 GB)
 bond0:0   Link encap:Ethernet  HWaddr 9c:8e:99:27:07:48
          inet addr:192.168.40.65  Bcast:192.168.40.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
 eth0      Link encap:Ethernet  HWaddr 9c:8e:99:27:07:48
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:159067028 errors:2812344562 dropped:0 overruns:0 frame:2760917654
          TX packets:239462984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:81878371517 (81.8 GB)  TX bytes:277454648737 (277.4 GB)
 eth1      Link encap:Ethernet  HWaddr 9c:8e:99:27:07:48
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:2743068 errors:188793903 dropped:0 overruns:0 frame:183311367
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:171105081 (171.1 MB)  TX bytes:0 (0.0 B)
 ----------------------------------------------------------------------------------------
 Ubuntu Server
p75:~# modinfo be2net
filename:       /lib/modules/2.6.32-220.el6.x86_64/kernel/drivers/net/benet/be2net.ko
license:        GPL
author:         ServerEngines Corporation
description:    ServerEngines BladeEngine 10Gbps NIC Driver 4.0.160r
version:        4.0.160r
srcversion:     47B631EFAC17FB12A7B8859
alias:          pci:v000010DFd0000E228sv*sd*bc*sc*i*
alias:          pci:v000010DFd0000E220sv*sd*bc*sc*i*
alias:          pci:v000019A2d00000710sv*sd*bc*sc*i*
alias:          pci:v000019A2d00000700sv*sd*bc*sc*i*
alias:          pci:v000019A2d00000221sv*sd*bc*sc*i*
alias:          pci:v000019A2d00000211sv*sd*bc*sc*i*
depends:
vermagic:       2.6.32-220.el6.x86_64 SMP mod_unload modversions
parm:           rx_frag_size:Size of a fragment that holds rcvd data. (ushort)
parm:           num_vfs:Number of PCI VFs to initialize (uint)
parm:           multi_rxq:Obsolete and used only for compatibility (bool)
p75:~#
 eth0      Link encap:Ethernet  HWaddr 44:1E:A1:54:AC:40
          inet addr:192.168.1.75  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::461e:a1ff:fe54:ac40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3439546 errors:0 dropped:0 overruns:847 frame:0
          TX packets:11505 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:214787883 (204.8 MiB)  TX bytes:3743444 (3.5 MiB)

---

