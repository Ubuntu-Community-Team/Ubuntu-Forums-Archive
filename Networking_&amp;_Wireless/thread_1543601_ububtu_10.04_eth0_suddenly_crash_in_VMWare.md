---
title: "ububtu 10.04 eth0 suddenly crash in VMWare"
date: 2010-08-01
forum: Networking &amp; Wireless
---

### Post by fisher0510 on 2010-08-01
Hi All,

My ubuntu running in VMWare worked fine, but I did nothing and suddenly crashed and never camp back again.

I found [COLOR=Red]eth0 link is down[/COLOR] and eth0 [COLOR=Red]isn't ruunning[/COLOR].


[COLOR=DarkGreen]#ifconfig eth0 up   --->not useful

#modprobe pcnet32  ----->not useful[/COLOR]


I post some useful (maybe) msg here . please help me chech where is the problem. 

That already annoyed me for two days.....!@#$%:(



root@fisher-desktop:~# [COLOR=DarkGreen]dmesg | grep eth0[/COLOR]
[    2.704732] eth0: registered as PCnet/PCI II 79C970A
[    5.812400] [COLOR=Red]eth0: link down[/COLOR]
[    6.468491] ADDRCONF(NETDEV_UP):[COLOR=Red] eth0: link is not ready[/COLOR]
[  963.357986] eth0: link down
[  964.173665] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1310.168384] eth0: link down
[ 1310.984466] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5949.208135] eth0: registered as PCnet/PCI II 79C970A
[ 5949.283592] eth0: link down
[ 5950.093037] ADDRCONF(NETDEV_UP): eth0: link is not ready


root@fisher-desktop:~# [COLOR=DarkGreen]ifconfig eth0 up[/COLOR]
root@fisher-desktop:~# [COLOR=DarkGreen]ifconfig eth0 [/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:0c:29:c7:db:eb  
          inet addr:140.133.88.28  Bcast:140.133.88.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0x2000 


root@fisher-desktop:~# [COLOR=DarkGreen]lsmod[/COLOR]
Module                  Size  Used by
[COLOR=Red]pcnet32                28890  0 
mii                     4381  1 pcnet32[/COLOR]
nls_utf8                1069  1 
isofs                  29250  1 
binfmt_misc             6587  1 
snd_ens1371            18814  2 
......
....


#[COLOR=DarkGreen]lspic[/COLOR]
00:18.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.7 PCI bridge: VMware PCI Express Root Port (rev 01)
02:00.0 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB
[COLOR=Red]02:01.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)[/COLOR]
02:02.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
02:03.0 USB Controller: VMware USB2 EHCI Controller

---

