---
title: "WiFi not stable (RTL8188CE, Ubuntu 12.04)"
date: 2012-06-18
forum: Networking &amp; Wireless
---

### Post by rw42 on 2012-06-18
Hello, I am also having problems with my WiFi connection and hope to find some help here.
I am using a ProBook 4530s with Ubuntu 12.04 installed. After booting the wireless connection is established but every now and then it "hangs", so that nslookup etc. fails. Reconnecting makes it available again but usually not for long. The problem is not the wireless router since wifi works fine under Windows on the same machine and older Ubuntu versions on a different laptop.
I tried already many possible solutions from the forum (including disabling IPv6 or using an older kernel: 2.6.38) but none did help. Perhaps somebody with more experience can shed light on this miracle? Thanks!

$ uname -mr

```
3.2.0-25-generic x86_64
```$ lspci

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
23:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
23:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
23:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
24:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
25:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
26:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
```$ lsmod | grep rtl

```
rtl8192ce              79523  0 
rtl8192c_common        74648  1 rtl8192ce
rtlwifi               105727  1 rtl8192ce
mac80211              514621  3 rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              209821  2 rtlwifi,mac80211
```$ iwconfig

```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Zy_private_PF"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 50:67:F0:FB:6C:34   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0

eth0      no wireless extensions.
```$ dmesg | tail -50

```
[ 1511.127575] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1511.127581] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1511.127587] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1511.127593] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1511.127599] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1516.346286] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1517.512745] wlan0: authenticate with 50:67:f0:fb:6c:34 (try 1)
[ 1517.516570] wlan0: authenticated
[ 1517.516767] wlan0: associate with 50:67:f0:fb:6c:34 (try 1)
[ 1517.527136] wlan0: RX ReassocResp from 50:67:f0:fb:6c:34 (capab=0xc11 status=0 aid=3)
[ 1517.527141] wlan0: associated
[ 1517.527145] wlan0: moving STA 50:67:f0:fb:6c:34 to state 1
[ 1517.527148] wlan0: moving STA 50:67:f0:fb:6c:34 to state 2
[ 1517.538757] cfg80211: Calling CRDA for country: NL
[ 1517.541837] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.541842] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1517.541844] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.541846] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1517.541848] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.541851] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1517.541853] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.541855] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1517.541857] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.541859] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1517.541861] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.541864] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1517.541865] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.541868] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1517.541870] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.541872] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1517.541874] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.541877] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1517.541878] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.541881] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1517.541883] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.541885] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1517.541887] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.541889] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1517.541891] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.541894] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1517.541896] cfg80211: Disabling freq 2484 MHz
[ 1517.541899] cfg80211: Regulatory domain changed to country: NL
[ 1517.541901] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1517.541903] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1517.541905] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1517.541907] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1517.541909] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[ 1517.787846] wlan0: moving STA 50:67:f0:fb:6c:34 to state 3
[ 1528.130880] wlan0: no IPv6 routers present
[ 1627.376824] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
```$ sudo lshw -C network

```
  *-network               
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:24:00.0
       logical name: wlan0
       version: 01
       serial: 20:10:7a:fd:aa:46
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.2.0-25-generic firmware=N/A ip=192.168.1.56 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 ioport:3000(size=256) memory:d4700000-d4703fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:25:00.0
       logical name: eth0
       version: 06
       serial: e4:11:5b:37:70:91
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:52 ioport:2000(size=256) memory:d4404000-d4404fff memory:d4400000-d4403fff
```

---

### Post by wildmanne39 on 2012-06-18
Hi, please do:
```
gksudo gedit /etc/modprobe.d/rtl8192ce.conf
```
A new empty file will open, paste this one line into the file.

```
options rtl8192ce swenc=1
```

Proofread, save and close gedit.

Then set your wireless settings in network manager to match the screenshots.

Go into your router settings and make sure encryption is set to wpa2 only if you have that option it works best for ubuntu, then change the wireless speed to b/g take out the N because this driver does not handle N speed very well and that should take care of your issues.

Also unless you have a very fast connection changing b/g/n to just b/g will not slow your connection down a lot of times it makes it faster with this driver.
Thanks

---

### Post by rw42 on 2012-06-19
Thanks, I did as you suggested but unfortunately it did not change anything. The mysterious disconnects/timeouts remain. Any other commands I should run or logs I can post here?

---

### Post by wildmanne39 on 2012-06-19
Hi, what country are you in?

Please post the out put of:
```
nm-tool
iwconfig
iwlist chan
rfkill list all
```
```

sudo cat /var/log/syslog | grep -e rtl -e firmware -e wpa -e wlan -e etork | tail -n100
```
run the above commands when you can not connect.

Also post the contents of:
```
gksudo gedit /etc/modprobe.d/rtl8192ce.conf
```
Thanks

---

### Post by rw42 on 2012-06-19
I am in NL. Here are the requested results:

$ nm-tool 

```
NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        E4:11:5B:37:70:91

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Zy_private_PF] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        20:10:7A:FD:AA:46

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    ZiggoA304C:      Infra, 7C:E9:D3:39:89:BE, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    studio-WT3:      Infra, 00:23:69:77:DD:4F, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WPA
    @Home00880:      Infra, 00:1B:2F:F5:76:AA, Freq 2462 MHz, Rate 54 Mb/s, Strength 99 WPA
    dachrizznet:     Infra, 00:16:0A:1C:F6:E8, Freq 2462 MHz, Rate 54 Mb/s, Strength 99 WPA2
    Sitecom_df6060:  Infra, 00:0C:F6:DF:60:60, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA
    Ziggo8BCCA0:     Infra, 00:0C:F6:8B:CC:A0, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WEP
    Eminent:         Infra, 00:14:5C:88:50:40, Freq 2432 MHz, Rate 54 Mb/s, Strength 77
    knaap:           Infra, E0:69:95:3D:ED:65, Freq 2472 MHz, Rate 54 Mb/s, Strength 70
    *Zy_private_PF:  Infra, 50:67:F0:FB:6C:34, Freq 2427 MHz, Rate 54 Mb/s, Strength 61 WPA2
    WiFiCP:          Infra, 00:23:F8:B4:41:BB, Freq 2442 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    ARV7519A560FE:   Infra, 88:25:2C:A5:60:FE, Freq 2432 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    novic123:        Infra, 00:1A:92:80:7F:EC, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 WEP
    Out of Order:    Infra, C0:3F:0E:E6:A9:7A, Freq 2452 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    9743KX7TURKOOI:  Infra, 68:7F:74:30:65:D8, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.56
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             8.8.8.8
    DNS:             8.8.4.4
```
$ iwconfig

```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Zy_private_PF"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 50:67:F0:FB:6C:34   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:12   Missed beacon:0

eth0      no wireless extensions.
```
$ iwlist chan

```
lo        no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.427 GHz (Channel 4)

eth0      no frequency information.
```
$ rfkill list all

```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

$ sudo cat /var/log/syslog | grep -e rtl -e firmware -e wpa -e wlan -e etork | tail -n100

```
Jun 20 03:05:43 hal kernel: [   19.800576] wlan0: moving STA 50:67:f0:fb:6c:34 to state 1
Jun 20 03:05:43 hal kernel: [   19.800583] wlan0: moving STA 50:67:f0:fb:6c:34 to state 2
Jun 20 03:05:43 hal NetworkManager[906]: <info> (wlan0): supplicant interface state: associating -> associated
Jun 20 03:05:43 hal kernel: [   19.813058] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 20 03:05:44 hal NetworkManager[906]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jun 20 03:05:44 hal wpa_supplicant[1002]: WPA: Key negotiation completed with 50:67:f0:fb:6c:34 [PTK=CCMP GTK=CCMP]
Jun 20 03:05:44 hal wpa_supplicant[1002]: CTRL-EVENT-CONNECTED - Connection to 50:67:f0:fb:6c:34 completed (auth) [id=0 id_str=]
Jun 20 03:05:44 hal kernel: [   20.980393] wlan0: moving STA 50:67:f0:fb:6c:34 to state 3
Jun 20 03:05:44 hal NetworkManager[906]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jun 20 03:05:44 hal NetworkManager[906]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Zy_private_PF'.
Jun 20 03:05:44 hal NetworkManager[906]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 20 03:05:44 hal NetworkManager[906]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun 20 03:05:44 hal NetworkManager[906]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 20 03:05:44 hal NetworkManager[906]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 20 03:05:44 hal NetworkManager[906]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun 20 03:05:45 hal NetworkManager[906]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jun 20 03:05:45 hal dhclient: Listening on LPF/wlan0/20:10:7a:fd:aa:46
Jun 20 03:05:45 hal dhclient: Sending on   LPF/wlan0/20:10:7a:fd:aa:46
Jun 20 03:05:45 hal dhclient: DHCPREQUEST of 192.168.1.56 on wlan0 to 255.255.255.255 port 67
Jun 20 03:05:55 hal kernel: [   31.429181] wlan0: no IPv6 routers present
Jun 20 03:06:02 hal dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun 20 03:06:05 hal dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun 20 03:06:08 hal dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jun 20 03:06:13 hal dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Jun 20 03:06:27 hal dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jun 20 03:06:29 hal NetworkManager[906]: <warn> (wlan0): DHCPv4 request timed out.
Jun 20 03:06:30 hal NetworkManager[906]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1743
Jun 20 03:06:30 hal NetworkManager[906]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Jun 20 03:06:30 hal NetworkManager[906]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Jun 20 03:06:30 hal NetworkManager[906]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Jun 20 03:06:30 hal NetworkManager[906]: <warn> Activation (wlan0) failed for access point (Zy_private_PF)
Jun 20 03:06:30 hal NetworkManager[906]: <warn> Activation (wlan0) failed.
Jun 20 03:06:30 hal NetworkManager[906]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Jun 20 03:06:30 hal NetworkManager[906]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun 20 03:06:30 hal NetworkManager[906]: <info> (wlan0): deactivating device (reason 'none') [0]
Jun 20 03:06:30 hal kernel: [   66.300412] wlan0: deauthenticating from 50:67:f0:fb:6c:34 by local choice (reason=3)
Jun 20 03:06:30 hal kernel: [   66.438782] wlan0: moving STA 50:67:f0:fb:6c:34 to state 2
Jun 20 03:06:30 hal kernel: [   66.438795] wlan0: moving STA 50:67:f0:fb:6c:34 to state 1
Jun 20 03:06:30 hal kernel: [   66.438803] wlan0: moving STA 50:67:f0:fb:6c:34 to state 0
Jun 20 03:06:30 hal wpa_supplicant[1002]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Jun 20 03:06:30 hal NetworkManager[906]: <info> (wlan0): supplicant interface state: completed -> disconnected
Jun 20 03:06:31 hal kernel: [   67.098639] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
Jun 20 03:06:32 hal NetworkManager[906]: <info> Activation (wlan0) starting connection 'Zy_private_PF'
Jun 20 03:06:32 hal NetworkManager[906]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 20 03:06:32 hal NetworkManager[906]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 20 03:06:32 hal NetworkManager[906]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 20 03:06:32 hal NetworkManager[906]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 20 03:06:32 hal NetworkManager[906]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 20 03:06:32 hal NetworkManager[906]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 20 03:06:32 hal NetworkManager[906]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 20 03:06:32 hal NetworkManager[906]: <info> Activation (wlan0/wireless): access point 'Zy_private_PF' has security, but secrets are required.
Jun 20 03:06:32 hal NetworkManager[906]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jun 20 03:06:32 hal NetworkManager[906]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 20 03:06:32 hal NetworkManager[906]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 20 03:06:32 hal NetworkManager[906]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 20 03:06:32 hal NetworkManager[906]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jun 20 03:06:32 hal NetworkManager[906]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 20 03:06:32 hal NetworkManager[906]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 20 03:06:32 hal NetworkManager[906]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 20 03:06:32 hal NetworkManager[906]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 20 03:06:32 hal NetworkManager[906]: <info> Activation (wlan0/wireless): connection 'Zy_private_PF' has security, and secrets exist.  No new secrets needed.
Jun 20 03:06:32 hal NetworkManager[906]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 20 03:06:33 hal wpa_supplicant[1002]: Failed to initiate AP scan.
Jun 20 03:06:33 hal wpa_supplicant[1002]: Trying to authenticate with 50:67:f0:fb:6c:34 (SSID='Zy_private_PF' freq=2427 MHz)
Jun 20 03:06:33 hal kernel: [   69.154333] wlan0: authenticate with 50:67:f0:fb:6c:34 (try 1)
Jun 20 03:06:33 hal wpa_supplicant[1002]: Trying to associate with 50:67:f0:fb:6c:34 (SSID='Zy_private_PF' freq=2427 MHz)
Jun 20 03:06:33 hal NetworkManager[906]: <info> (wlan0): supplicant interface state: disconnected -> authenticating
Jun 20 03:06:33 hal kernel: [   69.156054] wlan0: authenticated
Jun 20 03:06:33 hal kernel: [   69.156639] wlan0: associate with 50:67:f0:fb:6c:34 (try 1)
Jun 20 03:06:33 hal NetworkManager[906]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun 20 03:06:33 hal kernel: [   69.165466] wlan0: RX ReassocResp from 50:67:f0:fb:6c:34 (capab=0xc11 status=0 aid=2)
Jun 20 03:06:33 hal kernel: [   69.165478] wlan0: associated
Jun 20 03:06:33 hal kernel: [   69.165489] wlan0: moving STA 50:67:f0:fb:6c:34 to state 1
Jun 20 03:06:33 hal kernel: [   69.165496] wlan0: moving STA 50:67:f0:fb:6c:34 to state 2
Jun 20 03:06:33 hal wpa_supplicant[1002]: Associated with 50:67:f0:fb:6c:34
Jun 20 03:06:33 hal NetworkManager[906]: <info> (wlan0): supplicant interface state: associating -> associated
Jun 20 03:06:33 hal NetworkManager[906]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jun 20 03:06:33 hal wpa_supplicant[1002]: WPA: Key negotiation completed with 50:67:f0:fb:6c:34 [PTK=CCMP GTK=CCMP]
Jun 20 03:06:33 hal wpa_supplicant[1002]: CTRL-EVENT-CONNECTED - Connection to 50:67:f0:fb:6c:34 completed (reauth) [id=0 id_str=]
Jun 20 03:06:33 hal kernel: [   70.015698] wlan0: moving STA 50:67:f0:fb:6c:34 to state 3
Jun 20 03:06:33 hal NetworkManager[906]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jun 20 03:06:33 hal NetworkManager[906]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Zy_private_PF'.
Jun 20 03:06:33 hal NetworkManager[906]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 20 03:06:33 hal NetworkManager[906]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun 20 03:06:33 hal NetworkManager[906]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 20 03:06:33 hal NetworkManager[906]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 20 03:06:33 hal NetworkManager[906]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun 20 03:06:33 hal NetworkManager[906]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jun 20 03:06:33 hal dhclient: Listening on LPF/wlan0/20:10:7a:fd:aa:46
Jun 20 03:06:33 hal dhclient: Sending on   LPF/wlan0/20:10:7a:fd:aa:46
Jun 20 03:06:33 hal dhclient: DHCPREQUEST of 192.168.1.56 on wlan0 to 255.255.255.255 port 67
Jun 20 03:06:34 hal NetworkManager[906]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jun 20 03:06:34 hal NetworkManager[906]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 20 03:06:34 hal NetworkManager[906]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jun 20 03:06:35 hal NetworkManager[906]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jun 20 03:06:35 hal NetworkManager[906]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun 20 03:06:35 hal NetworkManager[906]: <info> Policy set 'Zy_private_PF' (wlan0) as default for IPv4 routing and DNS.
Jun 20 03:06:35 hal NetworkManager[906]: <info> Activation (wlan0) successful, device activated.
Jun 20 03:06:35 hal NetworkManager[906]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jun 20 03:06:44 hal kernel: [   80.990730] wlan0: no IPv6 routers present
```$ cat /etc/modprobe.d/rtl8192ce.conf

```
options rtl8192ce swenc=1
```

---

### Post by wildmanne39 on 2012-06-19
Hi, you have a lot of networks in your area I suggest you change the channel in your router to 1 or 11 and see if that helps, also I would remove the special characters that you have in your network name the (underscores) from your router settings and in network manager.
Thanks

---

### Post by rw42 on 2012-06-20
I tried different channels but still the same effect. Also, everthing works fine
with Windows 7 on the same laptop and with Ubuntu 10.10 on a different
one. So I assume it must be something related to the current version of the
driver / the kernel and/or Ubuntu 12.04. Any other ideas?

---

### Post by meijer.o on 2012-06-20
This wifi card can work, I have the same notebook.

Try to disable power save, see modinfo mudule name

I think you have to add

options ips=0

Best regards,

otto meijer

---

### Post by rw42 on 2012-06-20
Thanks, but power save it already switched off (ips=0). It was one of the first things I tried out. :-(

---

### Post by wildmanne39 on 2012-06-20
Hi, please post the output of:
```
Cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo
```
Thanks

---

### Post by Ranko Kohime on 2012-06-20
This sounds like the same problem I'm having.  Does the issue occur without encryption enabled?

My issue occurs only when using WPA1 or WPA2.

ETA: It also only occurs when mixing different devices on the network, i.e., a B/G-capable computer with B/G/N-capable computers.

---

### Post by wildmanne39 on 2012-06-20
Hi Ranko Kohime, if you need help please start your own thread so it does not get confusing.
Thanks

---

### Post by Ranko Kohime on 2012-06-20
> **wildmanne39 said:**
> Hi Ranko Kohime, if you need help please start your own thread so it does not get confusing.
Thanks
I did, actually.  It's about 3 pages down by now.  :|

I figure that if several of us are experiencing a similar issue, it might help to see what parallels there are between our individual circumstances.

My thread: [Wireless network 'stops' at random with mixed network + WPA]("http://ubuntuforums.org/showthread.php?t=2007199")

---

### Post by trulynon on 2012-06-21
I have the same notebook, but mine have Atheros WiFi adapter, but I was having the same problems. Have you tried to update Realtek Semiconductor Co., Ltd. RTL8111/8168B drivers, as it suggested [[COLOR="Red"]here[/COLOR]]("http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/")? I did it and it works now. I also setup my router on WPA2 encryption and disabled mixed channels (b+g). Currently I using only G and it works great, no an issue with disconnecting.

---

### Post by wildmanne39 on 2012-06-21
Hi trulynon, that is good information but it is for the ethernet connection and the OP is trying to get his wireless stable.
Thanks

---

### Post by rw42 on 2012-06-21
> **wildmanne39 said:**
> Hi, please post the output of:
Cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo Thanks

$ cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo

```
minstrel_ht
```

---

### Post by wildmanne39 on 2012-06-21
Hi, I just got through fixing this issue with another user, there is one more thing that we need to do and I think it will fix your problem as well.

[COLOR="Red"]You need to run these commands in this order!!![/COLOR]
```
sudo apt-get install wicd
```
Then:
```
sudo apt-get purge network-manager network-manager-gnome
```

I believe you have to manually setup your connection in wicd, set your server to google and disable IPV6 just like in network manger, and for DHCP I believe you need to set it to dhclient unless something has changed, if so please let us know.
Thanks

---

### Post by rw42 on 2012-06-22
Thanks, but using wicd unfortunately also did not help. I uninstalled network-manager and configured wicd. I tried different settings, static DNS, disabled ipv6, but no change. The connection is still "lost" after a few seconds, although wicd indicates it is still connected. My impression is that it even was a bit more stable with network-manager.

---

### Post by wildmanne39 on 2012-06-22
Hi, I also suggest you take out the _ underscores in your network name out in the router and your network settings and see if that makes it more stable.
Thanks

---

### Post by rw42 on 2012-06-24
> **wildmanne39 said:**
> Hi, I also suggest you take out the _ underscores in your network name out in the router and your network settings and see if that makes it more stable.

Unfortunately that also did not help. :-(
What else can I do except trying an older version of Ubuntu?

---

### Post by wildmanne39 on 2012-06-24
Hi, do you still have all the changes we made the way that we made them?

I still see N speed enabled in the router > 802.11bgn
please try one more time to take the change to 802.11bg, also with the error messages I believe wicd is your best option, everything we have tried usually makes the connection stable but it takes all these changes together so please keep them all as we try more options.
Thanks

---

### Post by rw42 on 2012-06-25
> **wildmanne39 said:**
> Hi, do you still have all the changes we made the way that we made them?

I still see N speed enabled in the router 
please try one more time to take the change to 802.11bg, also with the error messages I believe wicd is your best option, everything we have tried usually makes the connection stable but it takes all these changes together so please keep them all as we try more options.

Aha, thanks! I checked again in the router options and there the mode is definitely 802.11b/g without "n". Do I have to configure something on the "laptop" side as well? Neither in network-manager nor in wicd I can find preferences for the speed. (wicd is still installed and used.) BTW, iwconfig indicates a bit rate of 54 M/s while before changing to b/g in the router it was 150 M/s.
Thanks.

---

### Post by wildmanne39 on 2012-06-25
Hi, no just in the router and I hope that works because I am out of idea's.
Thanks

---

### Post by rw42 on 2012-06-25
> **wildmanne39 said:**
> Hi, no just in the router and I hope that works because I am out of idea's.

It is definitely changed in the router, although iwconfig is still displaying 802.11bgn. :-(

---

### Post by rw42 on 2012-06-25
Could it be a firmware problem since lshw -C network reports

```
firmware=N/A
```Although dmesg reports

```
rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
```I hope it's not a stupid question, I am not that experienced with wifi configs.

---

### Post by wildmanne39 on 2012-06-25
Hi, no it is not that your firmware is missing.

The only suggestion that I can make is go to the manufacturers website and see if they have an updated driver you can install or try ndiswrapper, which I have no experience with.
Thanks

---

