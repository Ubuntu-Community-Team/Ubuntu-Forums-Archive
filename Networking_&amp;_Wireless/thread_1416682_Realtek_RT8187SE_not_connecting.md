---
title: "Realtek RT8187SE not connecting"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by schurtek on 2010-02-26
I have a white label netbook with the Realtek RT8187SE Wireless card on PCIe. 

It is not detecting wireless networks consistently. When I am even 1 meter from the wireless router, I get no networks in range, but sometimes I pick up networks that are more than 20 meters from me. I can not connect, even if it is unsecure.

WiFi Radar does not detect the card.


**If I run a system check on the PCI bus I get the following:**
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at ec00 [size=256]
        Memory at febfc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: r8180
        Kernel modules: rtl8187se



**ifconfig:**
wlan0     Link encap:Ethernet  HWaddr 00:1e:e3:da:69:ba  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:9534 (9.5 KB)
          Interrupt:17 Memory:f80a8000-f80a8100 



**iwconfig:**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Channel=15  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

bnep0     no wireless extensions.

lsmod: 
rtl8187se             200472  0 


**sudo lshw -C network:**
  *-network
       description: Wireless interface
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 22
       serial: 00:1e:e3:da:69:ba
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=r8180 latency=0 multicast=yes wireless=802.11b/g
       resources: irq:17 ioport:ec00(size=256) memory:febfc000-febfffff



**dmesg:**
[    7.045650] rtl8187se: module is from the staging directory, the quality is unknown, you have been warned.

[    7.053328] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
[    7.053334] Copyright (c) 2004-2005, Andrea Merello
[    7.053339] r8180: Initializing module
[    7.053344] r8180: Wireless extensions version 22
[    7.053349] r8180: Initializing proc filesystem
[    7.053434] r8180: Configuring chip resources
[    7.053470] r8180 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.053486] r8180 0000:02:00.0: setting latency timer to 64
[    7.060468] r8180: Channel plan is 5
[    7.060471] 
[    7.060477] Dot11d_Init()
[    7.060485] r8180: MAC controller is a RTL8187SE b/g
[    7.060489] r8180: This is a PCI NIC
[    7.062912] r8180: usValue is 0x100
[    7.062914] 
[    7.119094] r8180: EEPROM version 104
[    7.123936] r8180: WW:**PLEASE** REPORT SUCCESSFUL/UNSUCCESSFUL TO Realtek!
[    7.124743] r8180: IRQ 17
[    7.126517] r8180: Driver probe completed

[ 1313.710435] In rtl8180_set_chan: Invalid chnanel 16
[ 1318.848337] In rtl8180_set_chan: Invalid chnanel 18
[ 1323.948220] In rtl8180_set_chan: Invalid chnanel 20
[ 1329.075051] In rtl8180_set_chan: Invalid chnanel 22
[ 1334.179116] In rtl8180_set_chan: Invalid chnanel 24
[ 1339.280386] In rtl8180_set_chan: Invalid chnanel 26
[ 1344.362785] In rtl8180_set_chan: Invalid chnanel 28
[ 1349.444080] In rtl8180_set_chan: Invalid chnanel 30
[ 1354.561631] In rtl8180_set_chan: Invalid chnanel 32
[ 1359.640783] In rtl8180_set_chan: Invalid chnanel 34
[ 1364.742045] In rtl8180_set_chan: Invalid chnanel 36
[ 1369.864539] In rtl8180_set_chan: Invalid chnanel 38
[ 1374.967288] In rtl8180_set_chan: Invalid chnanel 40
[ 1380.047791] In rtl8180_set_chan: Invalid chnanel 42
[ 1385.148058] In rtl8180_set_chan: Invalid chnanel 44
[ 1390.268584] In rtl8180_set_chan: Invalid chnanel 46
[ 1391.951017] In rtl8180_set_chan: Invalid chnanel 48
[ 1397.059293] In rtl8180_set_chan: Invalid chnanel 50
[ 1402.159027] In rtl8180_set_chan: Invalid chnanel 52
[ 1407.258935] In rtl8180_set_chan: Invalid chnanel 54
[ 1412.360747] In rtl8180_set_chan: Invalid chnanel 56
[ 1417.486716] In rtl8180_set_chan: Invalid chnanel 58
[ 1422.586556] In rtl8180_set_chan: Invalid chnanel 60
[ 1427.667303] In rtl8180_set_chan: Invalid chnanel 62
[ 1432.766659] In rtl8180_set_chan: Invalid chnanel 64
[ 1437.878846] In rtl8180_set_chan: Invalid chnanel 66
[ 1443.004064] In rtl8180_set_chan: Invalid chnanel 68
[ 1448.083032] In rtl8180_set_chan: Invalid chnanel 70
[ 1453.183283] In rtl8180_set_chan: Invalid chnanel 72
[ 1458.283088] In rtl8180_set_chan: Invalid chnanel 74
[ 1463.383030] In rtl8180_set_chan: Invalid chnanel 76
[ 1468.504711] In rtl8180_set_chan: Invalid chnanel 78
[ 1473.586279] In rtl8180_set_chan: Invalid chnanel 80
[ 1478.704498] In rtl8180_set_chan: Invalid chnanel 82
[ 1483.789863] In rtl8180_set_chan: Invalid chnanel 84
[ 1488.915496] In rtl8180_set_chan: Invalid chnanel 86
[ 1494.014242] In rtl8180_set_chan: Invalid chnanel 88
[ 1499.111575] In rtl8180_set_chan: Invalid chnanel 90
[ 1504.192759] In rtl8180_set_chan: Invalid chnanel 92
[ 1509.294109] In rtl8180_set_chan: Invalid chnanel 94
[ 1514.394917] In rtl8180_set_chan: Invalid chnanel 96
[ 1519.499392] In rtl8180_set_chan: Invalid chnanel 98
[ 1524.602344] In rtl8180_set_chan: Invalid chnanel 100
[ 1529.739629] In rtl8180_set_chan: Invalid chnanel 102
[ 1534.841353] In rtl8180_set_chan: Invalid chnanel 104
[ 1539.943241] In rtl8180_set_chan: Invalid chnanel 106
[ 1545.043098] In rtl8180_set_chan: Invalid chnanel 108
[ 1550.144804] In rtl8180_set_chan: Invalid chnanel 110
[ 1555.264159] In rtl8180_set_chan: Invalid chnanel 112
[ 1560.343103] In rtl8180_set_chan: Invalid chnanel 114
[ 1565.444959] In rtl8180_set_chan: Invalid chnanel 116
[ 1570.566890] In rtl8180_set_chan: Invalid chnanel 118
[ 1575.646566] In rtl8180_set_chan: Invalid chnanel 120
[ 1580.715171] In rtl8180_set_chan: Invalid chnanel 122
[ 1585.816829] In rtl8180_set_chan: Invalid chnanel 124
[ 1590.940880] In rtl8180_set_chan: Invalid chnanel 126
[ 1596.040628] In rtl8180_set_chan: Invalid chnanel 128
[ 1601.122775] In rtl8180_set_chan: Invalid chnanel 130
[ 1606.223247] In rtl8180_set_chan: Invalid chnanel 132
[ 1611.328568] In rtl8180_set_chan: Invalid chnanel 134
[ 1616.430564] In rtl8180_set_chan: Invalid chnanel 136
[ 1621.529495] In rtl8180_set_chan: Invalid chnanel 138
[ 1626.630691] In rtl8180_set_chan: Invalid chnanel 140
[ 1631.752841] In rtl8180_set_chan: Invalid chnanel 142
[ 1636.834254] In rtl8180_set_chan: Invalid chnanel 144
[ 1641.958260] In rtl8180_set_chan: Invalid chnanel 146
[ 1647.039822] In rtl8180_set_chan: Invalid chnanel 148
[ 1652.126313] In rtl8180_set_chan: Invalid chnanel 150
[ 1657.208177] In rtl8180_set_chan: Invalid chnanel 152
[ 1662.308079] In rtl8180_set_chan: Invalid chnanel 154
[ 1667.372244] In rtl8180_set_chan: Invalid chnanel 156
[ 1672.471552] In rtl8180_set_chan: Invalid chnanel 158
[ 1677.571540] In rtl8180_set_chan: Invalid chnanel 160
[ 1682.698279] In rtl8180_set_chan: Invalid chnanel 162
[ 1687.780058] In rtl8180_set_chan: Invalid chnanel 164
[ 1749.716887] r8180: Bringing up iface
[ 1750.213285] r8180: Card successfully reset
[ 1752.051957] r8180: WIRELESS_MODE_G
[ 1752.051965] 
[ 1752.087836] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by schurtek on 2010-03-13
It came right after an update via ethernet cable.

---

### Post by WooWah on 2010-04-20
Did you find a solution to this?

---

### Post by schurtek on 2010-04-21
> **schurtek said:**
> It came right after an update via ethernet cable.

See above quote!

---

