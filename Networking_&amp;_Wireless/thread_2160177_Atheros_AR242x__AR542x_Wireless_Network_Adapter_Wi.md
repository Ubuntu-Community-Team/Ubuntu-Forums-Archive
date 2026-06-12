---
title: "Atheros AR242x / AR542x Wireless Network Adapter Will NOT Connect"
date: 2013-07-05
forum: Networking &amp; Wireless
---

### Post by croblast2000 on 2013-07-05
Hi-- I am seeking the help of the linux experts here.
I've been installing linux as a newbie on 4 computers.
Sometimes Linux doesn't automatically get the wireless cards going right away.
I seek answers on the forums and then they work -- even though I don't usually fully comprehend what commands I am putting in.
Well that streak of luck has ended.  I simply cannot get this wireless card working.  It maybe a hardware issue.
I have even reinstalled the kernel  = 3.2.0-49-generic
I am running Xubuntu Precise = Ubuntu 12.04.2 LTS \n \l
I am working with a Toshiba Satellite P205D-S7802 laptop.

Here's some info to use in helping diagnose.  Thanks for any insights you can provide.

---

```
momza@supermom:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:11:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:af:05:16
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.196 latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:a000(size=256) memory:f8300000-f8300fff memory:80000000-8001ffff
  *-network
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:17:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:66:37:24
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.2.0-49-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f8200000-f820ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
momza@supermom:~$ 
```

---

```
momza@supermom:~$ lsmod | grep -e ath -e 80211
ath5k                 134863  0 
ath                    19187  1 ath5k
mac80211              474589  1 ath5k
cfg80211              188000  3 ath5k,ath,mac80211
compat                 19507  6 bnep,rfcomm,bluetooth,ath5k,mac80211,cfg80211
momza@supermom:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
```

---

```
momza@supermom:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

---

```
momza@supermom:~$ dmesg | grep -i -e warn -e error
[    0.174430] ACPI Error: No handler for Region [ERAM] (f4421f90) [EmbeddedControl] (20110623/evregion-373)
[    0.174437] ACPI Error: Region EmbeddedControl (ID=3) has no handler (20110623/exfldio-292)
[    0.174444] ACPI Error: Method parse/execution failed [\_SB_.HTEV] (Node f4420e10), AE_NOT_EXIST (20110623/psparse-536)
[    0.174455] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPC0.EC0_._REG] (Node f4429d08), AE_NOT_EXIST (20110623/psparse-536)
[   13.812345] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   50.925799] accounts-daemon[1312]: segfault at 7489008c ip 009f1644 sp bfa0335c error 4 in libdbus-1.so.3.5.8[9e9000+47000]
```

---

```
momza@supermom:~$  dmesg | grep -e ath5 -e wlan
[   20.267185] ath5k 0000:17:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   20.267200] ath5k 0000:17:00.0: setting latency timer to 64
[   20.267268] ath5k 0000:17:00.0: registered as 'phy0'
[   21.063286] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   30.286569] ath5k: phy0: gain calibration timeout (2412MHz)
[   30.618727] ath5k: phy0: gain calibration timeout (2412MHz)
[   30.619339] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.619925] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.744120] ath5k: phy0: gain calibration timeout (2412MHz)
[   32.200722] ath5k: phy0: gain calibration timeout (2417MHz)
[   32.655004] ath5k: phy0: gain calibration timeout (2422MHz)
[   33.107313] ath5k: phy0: gain calibration timeout (2427MHz)
[   33.558961] ath5k: phy0: gain calibration timeout (2432MHz)
[   34.010938] ath5k: phy0: gain calibration timeout (2437MHz)
[   34.462904] ath5k: phy0: gain calibration timeout (2442MHz)
[   35.367022] ath5k: phy0: gain calibration timeout (2452MHz)
[   35.818969] ath5k: phy0: gain calibration timeout (2457MHz)
[   36.270861] ath5k: phy0: gain calibration timeout (2462MHz)
[   36.723054] ath5k: phy0: gain calibration timeout (2412MHz)
[   39.392703] ath5k: phy0: gain calibration timeout (2412MHz)
[   39.879401] ath5k: phy0: gain calibration timeout (2417MHz)
[   40.363381] ath5k: phy0: gain calibration timeout (2422MHz)
[   40.847184] ath5k: phy0: gain calibration timeout (2427MHz)
[   41.331562] ath5k: phy0: gain calibration timeout (2432MHz)
[   41.815524] ath5k: phy0: gain calibration timeout (2437MHz)
[   42.299150] ath5k: phy0: gain calibration timeout (2442MHz)
[   42.783461] ath5k: phy0: gain calibration timeout (2447MHz)
[   43.267462] ath5k: phy0: gain calibration timeout (2452MHz)
[   43.759385] ath5k: phy0: gain calibration timeout (2457MHz)
[   44.243365] ath5k: phy0: gain calibration timeout (2462MHz)
[   44.727410] ath5k: phy0: gain calibration timeout (2412MHz)
[   52.332510] ath5k: phy0: gain calibration timeout (2412MHz)
[   52.787086] ath5k: phy0: gain calibration timeout (2417MHz)
[   53.239414] ath5k: phy0: gain calibration timeout (2422MHz)
[   53.690989] ath5k: phy0: gain calibration timeout (2427MHz)
[   54.142727] ath5k: phy0: gain calibration timeout (2432MHz)
[   54.595151] ath5k: phy0: gain calibration timeout (2437MHz)
[   55.046549] ath5k: phy0: gain calibration timeout (2442MHz)
[   55.499596] ath5k: phy0: gain calibration timeout (2447MHz)
[   55.951447] ath5k: phy0: gain calibration timeout (2452MHz)
[   56.403612] ath5k: phy0: gain calibration timeout (2457MHz)
[   82.333558] ath5k: phy0: gain calibration timeout (2412MHz)
[   82.786793] ath5k: phy0: gain calibration timeout (2417MHz)
[   83.238663] ath5k: phy0: gain calibration timeout (2422MHz)
[   83.691763] ath5k: phy0: gain calibration timeout (2427MHz)
[   84.147643] ath5k: phy0: gain calibration timeout (2432MHz)
[   84.598501] ath5k: phy0: gain calibration timeout (2437MHz)
[   85.050532] ath5k: phy0: gain calibration timeout (2442MHz)
[   85.502483] ath5k: phy0: gain calibration timeout (2447MHz)
[   85.954809] ath5k: phy0: gain calibration timeout (2452MHz)
[   86.406321] ath5k: phy0: gain calibration timeout (2457MHz)
[  122.337411] ath5k: phy0: gain calibration timeout (2412MHz)
[  122.791776] ath5k: phy0: gain calibration timeout (2417MHz)
[  123.249577] ath5k: phy0: gain calibration timeout (2422MHz)
[  123.704148] ath5k: phy0: gain calibration timeout (2427MHz)
[  124.160037] ath5k: phy0: gain calibration timeout (2432MHz)
[  124.620757] ath5k: phy0: gain calibration timeout (2437MHz)
[  125.080608] ath5k: phy0: gain calibration timeout (2442MHz)
[  125.537588] ath5k: phy0: gain calibration timeout (2447MHz)
[  125.993827] ath5k: phy0: gain calibration timeout (2452MHz)
[  126.447070] ath5k: phy0: gain calibration timeout (2457MHz)
[  172.339015] ath5k: phy0: gain calibration timeout (2412MHz)
[  172.795729] ath5k: phy0: gain calibration timeout (2417MHz)
[  173.251463] ath5k: phy0: gain calibration timeout (2422MHz)
[  173.704918] ath5k: phy0: gain calibration timeout (2427MHz)
[  174.159362] ath5k: phy0: gain calibration timeout (2432MHz)
[  174.614873] ath5k: phy0: gain calibration timeout (2437MHz)
[  175.071922] ath5k: phy0: gain calibration timeout (2442MHz)
[  175.531831] ath5k: phy0: gain calibration timeout (2447MHz)
[  175.991458] ath5k: phy0: gain calibration timeout (2452MHz)
[  176.446737] ath5k: phy0: gain calibration timeout (2457MHz)
[  232.338319] ath5k: phy0: gain calibration timeout (2412MHz)
[  232.794327] ath5k: phy0: gain calibration timeout (2417MHz)
[  233.250363] ath5k: phy0: gain calibration timeout (2422MHz)
[  233.706314] ath5k: phy0: gain calibration timeout (2427MHz)
[  234.162583] ath5k: phy0: gain calibration timeout (2432MHz)
[  234.618337] ath5k: phy0: gain calibration timeout (2437MHz)
[  235.074278] ath5k: phy0: gain calibration timeout (2442MHz)
[  235.530245] ath5k: phy0: gain calibration timeout (2447MHz)
[  235.986248] ath5k: phy0: gain calibration timeout (2452MHz)
[  236.442262] ath5k: phy0: gain calibration timeout (2457MHz)
[  292.340732] ath5k: phy0: gain calibration timeout (2412MHz)
[  292.794748] ath5k: phy0: gain calibration timeout (2417MHz)
[  293.246639] ath5k: phy0: gain calibration timeout (2422MHz)
[  293.698610] ath5k: phy0: gain calibration timeout (2427MHz)
[  294.150961] ath5k: phy0: gain calibration timeout (2432MHz)
[  294.606478] ath5k: phy0: gain calibration timeout (2437MHz)
[  295.062246] ath5k: phy0: gain calibration timeout (2442MHz)
[  295.518279] ath5k: phy0: gain calibration timeout (2447MHz)
[  295.974298] ath5k: phy0: gain calibration timeout (2452MHz)
[  296.427863] ath5k: phy0: gain calibration timeout (2457MHz)
[  352.339011] ath5k: phy0: gain calibration timeout (2412MHz)
[  352.794923] ath5k: phy0: gain calibration timeout (2417MHz)
[  353.246895] ath5k: phy0: gain calibration timeout (2422MHz)
[  353.703000] ath5k: phy0: gain calibration timeout (2427MHz)
[  354.155371] ath5k: phy0: gain calibration timeout (2432MHz)
[  354.610141] ath5k: phy0: gain calibration timeout (2437MHz)
[  355.063251] ath5k: phy0: gain calibration timeout (2442MHz)
[  355.514581] ath5k: phy0: gain calibration timeout (2447MHz)
[  355.966203] ath5k: phy0: gain calibration timeout (2452MHz)
[  356.420618] ath5k: phy0: gain calibration timeout (2457MHz)
[  412.338001] ath5k: phy0: gain calibration timeout (2412MHz)
[  412.791659] ath5k: phy0: gain calibration timeout (2417MHz)
[  413.242037] ath5k: phy0: gain calibration timeout (2422MHz)
[  413.694018] ath5k: phy0: gain calibration timeout (2427MHz)
[  414.147004] ath5k: phy0: gain calibration timeout (2432MHz)
[  414.601374] ath5k: phy0: gain calibration timeout (2437MHz)
[  415.059088] ath5k: phy0: gain calibration timeout (2442MHz)
[  415.514112] ath5k: phy0: gain calibration timeout (2447MHz)
[  415.967318] ath5k: phy0: gain calibration timeout (2452MHz)
[  416.419168] ath5k: phy0: gain calibration timeout (2457MHz)
[  472.338041] ath5k: phy0: gain calibration timeout (2412MHz)
[  472.794588] ath5k: phy0: gain calibration timeout (2417MHz)
[  473.250468] ath5k: phy0: gain calibration timeout (2422MHz)
[  473.706248] ath5k: phy0: gain calibration timeout (2427MHz)
[  474.162790] ath5k: phy0: gain calibration timeout (2432MHz)
[  474.614578] ath5k: phy0: gain calibration timeout (2437MHz)
[  475.066628] ath5k: phy0: gain calibration timeout (2442MHz)
[  475.518593] ath5k: phy0: gain calibration timeout (2447MHz)
[  475.970593] ath5k: phy0: gain calibration timeout (2452MHz)
[  476.422576] ath5k: phy0: gain calibration timeout (2457MHz)
[  532.339736] ath5k: phy0: gain calibration timeout (2412MHz)
[  532.796690] ath5k: phy0: gain calibration timeout (2417MHz)
[  533.252853] ath5k: phy0: gain calibration timeout (2422MHz)
[  533.706860] ath5k: phy0: gain calibration timeout (2427MHz)
[  534.158826] ath5k: phy0: gain calibration timeout (2432MHz)
[  534.614204] ath5k: phy0: gain calibration timeout (2437MHz)
[  535.069748] ath5k: phy0: gain calibration timeout (2442MHz)
[  535.522943] ath5k: phy0: gain calibration timeout (2447MHz)
[  535.977373] ath5k: phy0: gain calibration timeout (2452MHz)
[  536.433047] ath5k: phy0: gain calibration timeout (2457MHz)
[  592.334571] ath5k: phy0: gain calibration timeout (2412MHz)
[  592.787387] ath5k: phy0: gain calibration timeout (2417MHz)
[  593.242330] ath5k: phy0: gain calibration timeout (2422MHz)
[  593.699396] ath5k: phy0: gain calibration timeout (2427MHz)
[  594.154175] ath5k: phy0: gain calibration timeout (2432MHz)
[  594.607566] ath5k: phy0: gain calibration timeout (2437MHz)
[  595.060133] ath5k: phy0: gain calibration timeout (2442MHz)
[  595.515122] ath5k: phy0: gain calibration timeout (2447MHz)
[  595.967747] ath5k: phy0: gain calibration timeout (2452MHz)
[  596.424753] ath5k: phy0: gain calibration timeout (2457MHz)
[  652.342963] ath5k: phy0: gain calibration timeout (2412MHz)
[  652.795438] ath5k: phy0: gain calibration timeout (2417MHz)
[  653.247399] ath5k: phy0: gain calibration timeout (2422MHz)
[  653.699267] ath5k: phy0: gain calibration timeout (2427MHz)
[  654.151121] ath5k: phy0: gain calibration timeout (2432MHz)
[  654.604544] ath5k: phy0: gain calibration timeout (2437MHz)
[  655.064057] ath5k: phy0: gain calibration timeout (2442MHz)
[  655.522061] ath5k: phy0: gain calibration timeout (2447MHz)
[  655.975484] ath5k: phy0: gain calibration timeout (2452MHz)
[  656.428692] ath5k: phy0: gain calibration timeout (2457MHz)
[  712.339064] ath5k: phy0: gain calibration timeout (2412MHz)
[  712.794522] ath5k: phy0: gain calibration timeout (2417MHz)
[  713.250465] ath5k: phy0: gain calibration timeout (2422MHz)
[  713.706318] ath5k: phy0: gain calibration timeout (2427MHz)
[  714.162465] ath5k: phy0: gain calibration timeout (2432MHz)
[  714.614596] ath5k: phy0: gain calibration timeout (2437MHz)
[  715.066695] ath5k: phy0: gain calibration timeout (2442MHz)
[  715.518594] ath5k: phy0: gain calibration timeout (2447MHz)
[  715.970591] ath5k: phy0: gain calibration timeout (2452MHz)
[  716.424447] ath5k: phy0: gain calibration timeout (2457MHz)
[  772.338521] ath5k: phy0: gain calibration timeout (2412MHz)
[  772.791687] ath5k: phy0: gain calibration timeout (2417MHz)
[  773.246142] ath5k: phy0: gain calibration timeout (2422MHz)
[  773.701521] ath5k: phy0: gain calibration timeout (2427MHz)
[  774.158609] ath5k: phy0: gain calibration timeout (2432MHz)
[  774.614358] ath5k: phy0: gain calibration timeout (2437MHz)
[  775.069537] ath5k: phy0: gain calibration timeout (2442MHz)
[  775.525622] ath5k: phy0: gain calibration timeout (2447MHz)
[  775.984740] ath5k: phy0: gain calibration timeout (2452MHz)
[  776.442339] ath5k: phy0: gain calibration timeout (2457MHz)
[  832.339645] ath5k: phy0: gain calibration timeout (2412MHz)
[  832.794062] ath5k: phy0: gain calibration timeout (2417MHz)
[  833.250558] ath5k: phy0: gain calibration timeout (2422MHz)
[  833.703315] ath5k: phy0: gain calibration timeout (2427MHz)
[  834.155664] ath5k: phy0: gain calibration timeout (2432MHz)
[  834.607481] ath5k: phy0: gain calibration timeout (2437MHz)
[  835.062947] ath5k: phy0: gain calibration timeout (2442MHz)
[  835.515283] ath5k: phy0: gain calibration timeout (2447MHz)
[  835.967486] ath5k: phy0: gain calibration timeout (2452MHz)
[  836.419020] ath5k: phy0: gain calibration timeout (2457MHz)
[  892.335061] ath5k: phy0: gain calibration timeout (2412MHz)
[  892.787302] ath5k: phy0: gain calibration timeout (2417MHz)
[  893.239137] ath5k: phy0: gain calibration timeout (2422MHz)
[  893.691224] ath5k: phy0: gain calibration timeout (2427MHz)
[  894.143223] ath5k: phy0: gain calibration timeout (2432MHz)
[  894.595203] ath5k: phy0: gain calibration timeout (2437MHz)
[  895.047086] ath5k: phy0: gain calibration timeout (2442MHz)
[  895.499183] ath5k: phy0: gain calibration timeout (2447MHz)
[  895.951249] ath5k: phy0: gain calibration timeout (2452MHz)
[  896.403167] ath5k: phy0: gain calibration timeout (2457MHz)
[  952.340178] ath5k: phy0: gain calibration timeout (2412MHz)
[  952.801032] ath5k: phy0: gain calibration timeout (2417MHz)
[  953.255125] ath5k: phy0: gain calibration timeout (2422MHz)
[  953.711769] ath5k: phy0: gain calibration timeout (2427MHz)
[  954.170086] ath5k: phy0: gain calibration timeout (2432MHz)
[  954.636846] ath5k: phy0: gain calibration timeout (2437MHz)
[  955.091385] ath5k: phy0: gain calibration timeout (2442MHz)
[  955.546015] ath5k: phy0: gain calibration timeout (2447MHz)
[  956.004271] ath5k: phy0: gain calibration timeout (2452MHz)
[  956.460703] ath5k: phy0: gain calibration timeout (2457MHz)
[ 1012.337888] ath5k: phy0: gain calibration timeout (2412MHz)
[ 1012.793344] ath5k: phy0: gain calibration timeout (2417MHz)
[ 1013.249280] ath5k: phy0: gain calibration timeout (2422MHz)
[ 1013.703468] ath5k: phy0: gain calibration timeout (2427MHz)
[ 1014.157947] ath5k: phy0: gain calibration timeout (2432MHz)
[ 1014.611182] ath5k: phy0: gain calibration timeout (2437MHz)
[ 1015.065244] ath5k: phy0: gain calibration timeout (2442MHz)
[ 1015.522505] ath5k: phy0: gain calibration timeout (2447MHz)
[ 1015.978308] ath5k: phy0: gain calibration timeout (2452MHz)
[ 1016.434192] ath5k: phy0: gain calibration timeout (2457MHz)
[ 1072.339016] ath5k: phy0: gain calibration timeout (2412MHz)
[ 1072.794690] ath5k: phy0: gain calibration timeout (2417MHz)
[ 1073.250510] ath5k: phy0: gain calibration timeout (2422MHz)
[ 1073.705766] ath5k: phy0: gain calibration timeout (2427MHz)
[ 1074.158845] ath5k: phy0: gain calibration timeout (2432MHz)
[ 1074.614762] ath5k: phy0: gain calibration timeout (2437MHz)
[ 1075.070559] ath5k: phy0: gain calibration timeout (2442MHz)
[ 1075.526337] ath5k: phy0: gain calibration timeout (2447MHz)
[ 1075.982306] ath5k: phy0: gain calibration timeout (2452MHz)
[ 1076.435183] ath5k: phy0: gain calibration timeout (2457MHz)
[ 1132.339565] ath5k: phy0: gain calibration timeout (2412MHz)
[ 1132.791515] ath5k: phy0: gain calibration timeout (2417MHz)
[ 1133.243671] ath5k: phy0: gain calibration timeout (2422MHz)
[ 1133.696984] ath5k: phy0: gain calibration timeout (2427MHz)
[ 1134.153134] ath5k: phy0: gain calibration timeout (2432MHz)
[ 1134.609460] ath5k: phy0: gain calibration timeout (2437MHz)
[ 1135.063466] ath5k: phy0: gain calibration timeout (2442MHz)
[ 1135.517130] ath5k: phy0: gain calibration timeout (2447MHz)
[ 1135.972736] ath5k: phy0: gain calibration timeout (2452MHz)
[ 1136.427235] ath5k: phy0: gain calibration timeout (2457MHz)
[ 1192.338973] ath5k: phy0: gain calibration timeout (2412MHz)
[ 1192.794638] ath5k: phy0: gain calibration timeout (2417MHz)
[ 1193.251078] ath5k: phy0: gain calibration timeout (2422MHz)
[ 1193.706334] ath5k: phy0: gain calibration timeout (2427MHz)
[ 1194.160537] ath5k: phy0: gain calibration timeout (2432MHz)
[ 1194.614314] ath5k: phy0: gain calibration timeout (2437MHz)
[ 1195.067335] ath5k: phy0: gain calibration timeout (2442MHz)
[ 1195.518352] ath5k: phy0: gain calibration timeout (2447MHz)
[ 1195.970923] ath5k: phy0: gain calibration timeout (2452MHz)
[ 1196.422759] ath5k: phy0: gain calibration timeout (2457MHz)
[ 1252.339600] ath5k: phy0: gain calibration timeout (2412MHz)
[ 1252.793424] ath5k: phy0: gain calibration timeout (2417MHz)
[ 1253.247256] ath5k: phy0: gain calibration timeout (2422MHz)
[ 1253.699117] ath5k: phy0: gain calibration timeout (2427MHz)
[ 1254.151254] ath5k: phy0: gain calibration timeout (2432MHz)
[ 1254.602945] ath5k: phy0: gain calibration timeout (2437MHz)
[ 1255.057211] ath5k: phy0: gain calibration timeout (2442MHz)
[ 1255.512936] ath5k: phy0: gain calibration timeout (2447MHz)
[ 1255.971387] ath5k: phy0: gain calibration timeout (2452MHz)
[ 1256.426554] ath5k: phy0: gain calibration timeout (2457MHz)
[ 1312.338884] ath5k: phy0: gain calibration timeout (2412MHz)
[ 1312.793979] ath5k: phy0: gain calibration timeout (2417MHz)
[ 1313.247464] ath5k: phy0: gain calibration timeout (2422MHz)
[ 1313.699428] ath5k: phy0: gain calibration timeout (2427MHz)
[ 1314.155660] ath5k: phy0: gain calibration timeout (2432MHz)
[ 1314.608871] ath5k: phy0: gain calibration timeout (2437MHz)
[ 1315.063367] ath5k: phy0: gain calibration timeout (2442MHz)
[ 1315.514958] ath5k: phy0: gain calibration timeout (2447MHz)
[ 1315.967289] ath5k: phy0: gain calibration timeout (2452MHz)
[ 1316.423435] ath5k: phy0: gain calibration timeout (2457MHz)
[ 1372.335773] ath5k: phy0: gain calibration timeout (2412MHz)
[ 1372.800939] ath5k: phy0: gain calibration timeout (2417MHz)
[ 1373.256805] ath5k: phy0: gain calibration timeout (2422MHz)
[ 1373.712904] ath5k: phy0: gain calibration timeout (2427MHz)
[ 1374.176251] ath5k: phy0: gain calibration timeout (2432MHz)
[ 1374.635986] ath5k: phy0: gain calibration timeout (2437MHz)
[ 1375.098453] ath5k: phy0: gain calibration timeout (2442MHz)
[ 1375.568903] ath5k: phy0: gain calibration timeout (2447MHz)
[ 1376.024911] ath5k: phy0: gain calibration timeout (2452MHz)
[ 1376.479911] ath5k: phy0: gain calibration timeout (2457MHz)
[ 1432.339123] ath5k: phy0: gain calibration timeout (2412MHz)
[ 1432.794685] ath5k: phy0: gain calibration timeout (2417MHz)
[ 1433.250664] ath5k: phy0: gain calibration timeout (2422MHz)
[ 1433.705230] ath5k: phy0: gain calibration timeout (2427MHz)
[ 1434.158979] ath5k: phy0: gain calibration timeout (2432MHz)
[ 1434.614322] ath5k: phy0: gain calibration timeout (2437MHz)
[ 1435.066627] ath5k: phy0: gain calibration timeout (2442MHz)
[ 1435.519363] ath5k: phy0: gain calibration timeout (2447MHz)
[ 1435.971280] ath5k: phy0: gain calibration timeout (2452MHz)
[ 1436.423346] ath5k: phy0: gain calibration timeout (2457MHz)
```

---

---

### Post by praseodym on 2013-07-06
Try to deactivate the hardware encryption of the driver:
```

echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```

---

### Post by croblast2000 on 2013-07-06
Yes, it worked!
Count this as another reason why linux destroys Macs and MS!  Proprietary = Fascism!
Heal yea! I like eclamation points.
But I do have question, dear [**[COLOR=#000000]praseodym[/COLOR]**]("http://ubuntuforums.org/member.php?u=1411497")...
What part of the results in the Code sections of my post did you see that the hardware was encrypted?
And one more, on the off chance, could the device have been disabled by a virus when the laptop was still running windoze?
Thank you for your help and amazing insights.

---

### Post by praseodym on 2013-07-06
The encryption is enabled by default in Atheros devices. Maybe some BIOS settings in Windows caused the problem?!

---

### Post by croblast2000 on 2013-07-06
amazing... i didn't see this with another toshiba satellite?  this is invaluable info for all those loading linux ans say no to the nsa!

---

### Post by praseodym on 2013-07-06
I remember a visitor wanting to use Win7 and an Atheros card in my home network. My router was running in **b+g+n** mode and he wasnt able to connect. After I changed the router to **b+g** mode only he did. Maybe the Win drivers dont work properly.

---

### Post by Naturally-Simple on 2013-08-24
Hi there, I have exactly the same wireless card, and pretty much the same outputs from the commands that croblast2000 posted, so I figured it was worth a shot to see if those commands posted by praseodym would work. Nope. But I have hope that something will work, now that I've upgraded to 13.04 since my last attempt at fixing the wireless issue (thread found here: [http://ubuntuforums.org/showthread.php?t=1916598](http://ubuntuforums.org/showthread.php?t=1916598)). Here are some outputs for you:

```
kevin@deep-thought:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:d6:21:06
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.133 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:3000(size=256) memory:90410000-90410fff memory:90400000-9040ffff memory:90420000-9043ffff
  *-network
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:2c:52:f9:5e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.8.0-29-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:92600000-9260ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

***

```

kevin@deep-thought:~$ lsmod | grep -e ath -e 80211
ath5k                 134997  0 
ath                    19187  1 ath5k
mac80211              526519  1 ath5k
cfg80211              436177  3 ath,ath5k,mac80211

```

***

```

kevin@deep-thought:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

```

***

```

kevin@deep-thought:~$ cat /etc/network/interfacesauto lo
iface lo inet loopback

```

***

```

kevin@deep-thought:~$ dmesg | grep -i -e warn -e error[    0.148218] ACPI Warning: For \_SB_.PCI0.P32_._PRT: Return Package has no elements (empty) (20121018/nspredef-463)
[   17.362757] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMBA 1 (20121018/utaddress-251)
[   17.362766] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \_SB_.PCI0.LPC_.PMA1 2 (20121018/utaddress-251)
[   17.362776] ACPI Warning: 0x00000530-0x0000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   17.664730] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro

```

***

```

kevin@deep-thought:~$ dmesg | grep -e ath5 -e wlan[   17.511765] ath5k 0000:02:00.0: registered as 'phy0'
[   18.094643] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   21.394089] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.394558] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.788635] wlan0: authenticate with 98:fc:11:3e:bc:e2
[   22.796541] wlan0: send auth to 98:fc:11:3e:bc:e2 (try 1/3)
[   22.801445] wlan0: authenticated
[   22.804042] wlan0: associate with 98:fc:11:3e:bc:e2 (try 1/3)
[   22.806483] wlan0: RX AssocResp from 98:fc:11:3e:bc:e2 (capab=0x411 status=0 aid=2)
[   22.806762] wlan0: associated
[   22.806773] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   25.576482] wlan0: authenticate with 98:fc:11:3e:bc:e2
[   25.580351] wlan0: send auth to 98:fc:11:3e:bc:e2 (try 1/3)
[   25.784031] wlan0: send auth to 98:fc:11:3e:bc:e2 (try 2/3)
[   25.988034] wlan0: send auth to 98:fc:11:3e:bc:e2 (try 3/3)
[   26.192045] wlan0: authentication with 98:fc:11:3e:bc:e2 timed out
[   68.204052] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

***

```

kevin@deep-thought:~$ rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```

***

Should I undo the commands I followed from praseodym? I see my wireless connection and I see others, but it just doesn't connect.
Thanks for any help!

---

### Post by casrenooij on 2013-12-19
This is what eventuelly worked for me:

>   apt-get remove firmware-atheros apt-get install firmware-atheros
 reboot
 apt-get update
 apt-get upgrade
 apt-get install firmware-atheros
shutdown




I did uninstall Wicd before this, i do not know if that had anything to do with it

root@klapdoos:/home/crenooij# lspci | grep Atheros
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)

root@klapdoos:/home/crenooij# uname -a
Linux klapdoos 3.2.0-4-amd64 #1 SMP Debian 3.2.51-1 x86_64 GNU/Linux

---

### Post by micyek on 2014-04-19
> **casrenooij said:**
> This is what eventuelly worked for me:



I did uninstall Wicd before this, i do not know if that had anything to do with it

root@klapdoos:/home/crenooij# lspci | grep Atheros
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)

root@klapdoos:/home/crenooij# uname -a
Linux klapdoos 3.2.0-4-amd64 #1 SMP Debian 3.2.51-1 x86_64 GNU/Linux

Just removing the firmware and re-installing it worked for me after upgrading to 14.04.  Hopefully this helps others.

---

### Post by richardlc on 2015-01-10
As a complete beginner, trying to connect a Toshiba Satellite L300 to WIFI, I have been greatly helped by all these suggestions.
Please could you help with how to enter the last code removing the atheros firmware and then re-installing the atheros firmware.  What should the wording be precisely on the command line?  When copying the code, apt said it could not find the "atheros firmware"
Finally I solved the problem by finding a manual for the old Toshiba, which revealed a hardware switch!  WIFI is now active with Ubuntu 14.04.1 LTS.
I did also run the small code section from Praseodym early in the thread.

---

