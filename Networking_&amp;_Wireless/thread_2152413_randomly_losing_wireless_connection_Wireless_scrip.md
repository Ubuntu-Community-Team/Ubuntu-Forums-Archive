---
title: "randomly losing wireless connection *Wireless script attached***"
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by BSherwood on 2013-06-07
I randomly lose connection to the internet. The connection bars at the top right will say im connected, but nothing loads. If I disconnect and then reconnects it sometimes brings the internet back. And other times I have to reboot to get it back. 

-Ubuntu 12.4 64 bit desktop.
-The router I am using is NETGEAR N300  Wireless Gigabit Router WNR3500L. If there is anything else I need to post to help troubleshoot please let me know what is needed, and HOW to get it.

Thanks in advance for any help!

---

### Post by matt_symes on 2013-06-07
Thread moved to **Networking and Wireless**.

---

### Post by BSherwood on 2013-06-07
found a script to run that can give more info. hope this helps!

```
*************** info trace ***************

***** uname -a *****

Linux ubuntu 3.5.0-32-generic #53~precise1-Ubuntu SMP Wed May 29 20:33:37 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

***** lspci *****

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
    Kernel driver in use: r8169

***** lsusb *****

Bus 002 Device 002: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 008 Device 002: ID 1007:8400  
Bus 008 Device 003: ID 1532:0015 Razer USA, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"NETGEAR63"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rtl8192cu              72752  0 
rtl8192c_common        49512  1 rtl8192cu
rtlwifi                76125  1 rtl8192cu
mac80211              555272  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              208382  2 rtlwifi,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [NETGEAR63] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *NETGEAR63:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WPA2

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR63"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007d57b1d2b2
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 00094E4554474541523633
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC191BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD870050F204104A00011010440001021041000100103B000103104700100F28DC16ECE955317635CE3DF75ADD671021000D4E4554474541522C20496E632E1023000A574E52333530304C76321024000A574E52333530304C763210420005333530304C1054000800060050F20400011011000A574E52333530304C7632100800020084103C000101
                    IE: Unknown: DD090010180203F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** dmesg *****

[   31.316235] rtl8192cu: Chip version 0x10
[   31.475822] rtl8192cu: MAC address: <MAC address removed>
[   31.475826] rtl8192cu: Board Type 0
[   31.476073] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   31.476153] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[   31.565568] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   31.565946] rtlwifi: wireless switch is on
[   31.589972] rtl8192cu: MAC auto ON okay!
[   31.625081] rtl8192cu: Tx queue select: 0x05
[   31.987364] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.987584] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.172395] wlan0: authenticate with <MAC address removed>
[   34.195634] wlan0: send auth to <MAC address removed> (try 1/3)
[   34.396013] wlan0: send auth to <MAC address removed> (try 2/3)
[   34.405972] wlan0: authenticated
[   34.420013] wlan0: associate with <MAC address removed> (try 1/3)
[   34.438973] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   34.439013] wlan0: associated
[   34.439682] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  447.940722] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  451.376332] wlan0: authenticate with <MAC address removed>
[  451.399766] wlan0: send auth to <MAC address removed> (try 1/3)
[  451.401359] wlan0: authenticated
[  451.416016] wlan0: associate with <MAC address removed> (try 1/3)
[  451.435222] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  451.435261] wlan0: associated
[  788.463938] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  791.648330] wlan0: authenticate with <MAC address removed>
[  791.671987] wlan0: send auth to <MAC address removed> (try 1/3)
[  791.673585] wlan0: authenticated
[  791.688025] wlan0: associate with <MAC address removed> (try 1/3)
[  791.691070] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  791.691109] wlan0: associated
[ 1542.162497] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1547.668348] wlan0: authenticate with <MAC address removed>
[ 1547.691844] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1547.693441] wlan0: authenticated
[ 1547.708017] wlan0: associate with <MAC address removed> (try 1/3)
[ 1547.711058] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 1547.711093] wlan0: associated
[ 1846.948710] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1850.176359] wlan0: authenticate with <MAC address removed>
[ 1850.199655] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1850.201250] wlan0: authenticated
[ 1850.216010] wlan0: associate with <MAC address removed> (try 1/3)
[ 1850.219117] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 1850.219149] wlan0: associated
[ 2080.694195] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2084.436332] wlan0: authenticate with <MAC address removed>
[ 2084.460058] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2084.462529] wlan0: authenticated
[ 2084.476016] wlan0: associate with <MAC address removed> (try 1/3)
[ 2084.479154] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 2084.479192] wlan0: associated
[ 4282.265030] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4310.824348] wlan0: authenticate with <MAC address removed>
[ 4310.847801] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4310.849395] wlan0: authenticated
[ 4310.864016] wlan0: associate with <MAC address removed> (try 1/3)
[ 4310.867639] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 4310.867671] wlan0: associated
[ 4331.303775] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4334.732339] wlan0: authenticate with <MAC address removed>
[ 4334.755696] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4334.757417] wlan0: authenticated
[ 4334.772017] wlan0: associate with <MAC address removed> (try 1/3)
[ 4334.775539] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 4334.775572] wlan0: associated
[ 4355.606184] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4359.732359] wlan0: authenticate with <MAC address removed>
[ 4359.755692] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4359.759276] wlan0: authenticated
[ 4359.772021] wlan0: associate with <MAC address removed> (try 1/3)
[ 4359.775156] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 4359.775191] wlan0: associated
[ 4380.294851] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4383.728345] wlan0: authenticate with <MAC address removed>
[ 4383.751940] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4383.754666] wlan0: authenticated
[ 4383.768015] wlan0: associate with <MAC address removed> (try 1/3)
[ 4383.771031] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 4383.771063] wlan0: associated
[ 4404.338711] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4407.724356] wlan0: authenticate with <MAC address removed>
[ 4407.747859] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4407.749461] wlan0: authenticated
[ 4407.764015] wlan0: associate with <MAC address removed> (try 1/3)
[ 4407.767080] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 4407.767113] wlan0: associated
[ 5424.245720] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 5427.896339] wlan0: authenticate with <MAC address removed>
[ 5427.919909] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5427.921883] wlan0: authenticated
[ 5427.936017] wlan0: associate with <MAC address removed> (try 1/3)
[ 5427.939125] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 5427.939157] wlan0: associated
[ 5551.404935] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 5556.600340] wlan0: authenticate with <MAC address removed>
[ 5556.623936] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5556.625411] wlan0: authenticated
[ 5556.640024] wlan0: associate with <MAC address removed> (try 1/3)
[ 5556.643156] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 5556.643191] wlan0: associated
[ 5858.231563] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 5862.128342] wlan0: authenticate with <MAC address removed>
[ 5862.151823] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5862.153425] wlan0: authenticated
[ 5862.168019] wlan0: associate with <MAC address removed> (try 1/3)
[ 5862.172292] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 5862.172325] wlan0: associated
[ 6449.726082] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6452.904334] wlan0: authenticate with <MAC address removed>
[ 6452.927820] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6452.930043] wlan0: authenticated
[ 6452.944032] wlan0: associate with <MAC address removed> (try 1/3)
[ 6452.947180] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 6452.947223] wlan0: associated
[ 6554.957169] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6557.852338] wlan0: authenticate with <MAC address removed>
[ 6557.875884] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6557.877360] wlan0: authenticated
[ 6557.892017] wlan0: associate with <MAC address removed> (try 1/3)
[ 6557.895854] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 6557.895886] wlan0: associated
[ 6697.801198] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6701.864335] wlan0: authenticate with <MAC address removed>
[ 6701.888226] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6701.890696] wlan0: authenticated
[ 6701.904020] wlan0: associate with <MAC address removed> (try 1/3)
[ 6701.907066] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 6701.907101] wlan0: associated
[ 7007.848736] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 7012.444381] wlan0: authenticate with <MAC address removed>
[ 7012.467997] wlan0: send auth to <MAC address removed> (try 1/3)
[ 7012.469818] wlan0: authenticated
[ 7012.484011] wlan0: associate with <MAC address removed> (try 1/3)
[ 7012.487188] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 7012.487221] wlan0: associated
[ 7427.987424] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 7431.180346] wlan0: authenticate with <MAC address removed>
[ 7431.203909] wlan0: send auth to <MAC address removed> (try 1/3)
[ 7431.205503] wlan0: authenticated
[ 7431.220022] wlan0: associate with <MAC address removed> (try 1/3)
[ 7431.223123] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 7431.223161] wlan0: associated
[ 8377.182960] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 8382.440343] wlan0: authenticate with <MAC address removed>
[ 8382.463879] wlan0: send auth to <MAC address removed> (try 1/3)
[ 8382.466351] wlan0: authenticated
[ 8382.480014] wlan0: associate with <MAC address removed> (try 1/3)
[ 8382.483101] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 8382.483137] wlan0: associated
[ 9312.237499] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 9316.132341] wlan0: authenticate with <MAC address removed>
[ 9316.155673] wlan0: send auth to <MAC address removed> (try 1/3)
[ 9316.179897] wlan0: authenticated
[ 9316.192020] wlan0: associate with <MAC address removed> (try 1/3)
[ 9316.195138] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 9316.195175] wlan0: associated
[ 9389.236211] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 9393.300336] wlan0: authenticate with <MAC address removed>
[ 9393.323804] wlan0: send auth to <MAC address removed> (try 1/3)
[ 9393.325270] wlan0: authenticated
[ 9393.340015] wlan0: associate with <MAC address removed> (try 1/3)
[ 9393.343012] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 9393.343046] wlan0: associated
[ 9644.941098] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 9648.944339] wlan0: authenticate with <MAC address removed>
[ 9648.967756] wlan0: send auth to <MAC address removed> (try 1/3)
[ 9649.168030] wlan0: send auth to <MAC address removed> (try 2/3)
[ 9649.170713] wlan0: authenticated
[ 9649.184015] wlan0: associate with <MAC address removed> (try 1/3)
[ 9649.186965] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 9649.187000] wlan0: associated

****************** done ******************


```

---

### Post by Hadaka on 2013-06-07
Hi try going into your network mgr. and setting
IPv6 to Ignore..see attached.
[ATTACH=CONFIG]243636[/ATTACH]
to disable IPv6 in 12.04 you can do..
```
sudo gedit /etc/sysctl.conf 
```
and add these lines...
```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```
save and close gedit
then to reset sysctl do..
```
sudo sysctl -p
```
Try the Ignore first..if it helps then do the disable code.
thanks.

---

### Post by BSherwood on 2013-06-07
I tired both suggestions that you've made, but I still lose connection.
 It's strange because it never tells me my connection is lost, and my connection meter in the upper right hand corner still shows that I'm connected. But when I'm using Firefox everything is going fine then all the sudden I can't load pages. I even tried connecting to Mangle ( a ventrilo substitute ) and ping [www.google.com]("http://www.google.com") and no connection for those either. 

note* connection still works fine on the Windows 7 side.
**edit - as far as adding the 3 lines to the sysctl.conf , I can just cut and paste those to the bottom of the doc.? Then when I reset sysctl it will show those 3 lines in terminal? -my first day with linux, just wanted to make sure I'm doing it right.

---

### Post by Hadaka on 2013-06-07
Hi, if seting IPv6 to ignore with network mgr. didnt help
then i wouldnt bother with writing the file. But..yes once
you save and close gedit..those lines will remain part of that file.
Are you running WPA2/WPA mixed?..if YES then try to set your router
to WPA2 only.You might also try changing the channel in the router settings.
thanks.

---

### Post by BSherwood on 2013-06-07
> **Hadaka said:**
>  try to set your router to WPA2 only.You might also try changing the channel in the router settings.
thanks.

I don't know how to do that :( 
I tried searching google for a bit, but didn't come up with much on how to get JUST WPA2.

---

### Post by Hadaka on 2013-06-07
You need to make the change in your router and in network mgr.
So get the specs on your router..log in and look around, The real
problem is probably the fact that your wireless is N only, and sometimes
linux/Ubuntu just doesnt fly with N speeds, It all depends on the router,the
type of computer you have,the type of wireless card you have,your configuration,
what you use to manage the network...and as far as I can tell, maybe even the Moon
phase, its really hit and miss.All because the manufactures of the wifi unit just dont
supply decent linux drivers. I wish I had some happy easy fix for you, but I dont. There
are just way too many variables that are involved. So keep trying and hopefully you will
hit on something that works for you, or perhaps someone else will chime in with things
for your to try,sorry I have no further suggestions for you.
good luck !!!

---

