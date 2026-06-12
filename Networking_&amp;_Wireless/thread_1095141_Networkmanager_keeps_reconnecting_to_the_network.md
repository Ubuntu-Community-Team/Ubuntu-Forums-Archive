---
title: "Networkmanager keeps reconnecting to the network"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by Igotaproblem on 2009-03-13
On 8.04. And every time it reconnects I get shut off from the internet for like 20 seconds. Sometimes it does this just a couple of times an evening whilst sometimes it will enter an annoying state of unusableness where it repeatedly connects, stays connected for a second and then tries to reconnect again.

If I point at it when it's reconnecting it says "Waiting for Network key". The network has WPA-PSK with AES encryption.

How do I find what the problem is and solve it? Wireless works flawlessly on Windows, which I got installed on a different harddrive.

---

### Post by pytheas22 on 2009-03-13
The next time it disconnects, please immediately open a terminal, run the following commands and post the output:
```

dmesg | tail -50
lshw -C Network
uname -rm
```

---

### Post by Igotaproblem on 2009-03-18
Late reply - been busy.

```
admin@m:~$ dmesg | tail -50
[14390.826990] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[14405.954367] ath0: no IPv6 routers present
[14466.321421] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[14482.764561] ath0: no IPv6 routers present
[14891.988243] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[14904.324957] ath0: no IPv6 routers present
[15328.735159] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[15333.549666] ath0: no IPv6 routers present
[15359.101330] ath0: no IPv6 routers present
[15391.074985] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[15399.424988] ath0: no IPv6 routers present
[15594.022575] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[15606.575167] ath0: no IPv6 routers present
[15879.470842] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[15893.721136] ath0: no IPv6 routers present
[15950.718603] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[15965.956150] ath0: no IPv6 routers present
[16318.809773] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[16328.646595] ath0: no IPv6 routers present
[16781.710194] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[16791.819376] ath0: no IPv6 routers present
[18187.383266] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[18203.347705] ath0: no IPv6 routers present
[22331.774959] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[22341.458335] ath0: no IPv6 routers present
[23556.336939] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[23566.634670] ath0: no IPv6 routers present
[23644.546753] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[23649.263999] ath0: no IPv6 routers present
[23663.991555] ath0: no IPv6 routers present
[23678.336915] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[23683.035915] ath0: no IPv6 routers present
[23699.336964] ath0: no IPv6 routers present
[23730.717724] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[23747.402640] ath0: no IPv6 routers present
[23779.067016] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[23789.133883] ath0: no IPv6 routers present
[23816.742586] ath0: no IPv6 routers present
[23901.696677] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[23917.542201] ath0: no IPv6 routers present
[24078.728548] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[24086.294984] ath0: no IPv6 routers present
[24145.326994] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[24154.610872] ath0: no IPv6 routers present
[24200.866004] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[24210.477033] ath0: no IPv6 routers present
[24300.628299] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[24307.723514] ath0: no IPv6 routers present
[24331.499246] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[24343.706979] ath0: no IPv6 routers present
admin@m:~$ lshw -C Network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:d5:ee:08
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
       product: AR5413 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: wifi0
       version: 01
       serial: 00:02:e3:47:ea:92
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
admin@m:~$ 
admin@m:~$ uname -rm
2.6.24-23-generic i686
```

Additionally the notorious "key ring" pop up is bugging me, but I guess it has nothing to do with my connection issues.

---

### Post by pytheas22 on 2009-03-18
Thanks for the output.  Unfortunately, it doesn't contain a concrete explanation of why the connection crashes, but it may have to do with Network Manager.  In that case, you would likely have better luck using wicd, an alternative connection manager.  You can install wicd by typing:
```

echo 'deb http://apt.wicd.net hardy extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

Then launch it from the Applications>Internet menu.

The other possibility is that this is a driver problem, in which case we could try updating your driver or using an alternative one.  But please give wicd a try first and let me know if it helps.

---

