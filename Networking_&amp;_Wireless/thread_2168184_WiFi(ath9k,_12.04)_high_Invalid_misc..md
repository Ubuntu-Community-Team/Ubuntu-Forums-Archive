---
title: "WiFi(ath9k, 12.04) high Invalid misc."
date: 2013-08-16
forum: Networking &amp; Wireless
---

### Post by shevchenko-rostislav on 2013-08-16
Dear Ubuntu users,

I have problem with my wi-fi connection ( it's in the first of 2 years using ubuntu) - my internet is really slow...I have high invalid misk. Month ago everything was allright.
1)Output **uname -a**
```
Linux rostyslav-K53E 3.5.0-37-generic #58~precise1-Ubuntu SMP Wed Jul 10 17:51:56 UTC 2013 i686 i686 i386 GNU

```
2)Output for **sudo lshw -class network**
```
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: e0:b9:a5:c5:e1:d4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-37-generic firmware=N/A ip=192.168.1.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:dea00000-dea0ffff


```
3)Output for **nm-tool**
```

- Device: wlan0  [kyivstar96] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        E0:B9:A5:C5:E1:D4

  Capabilities:
    Speed:           81 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Grave3:          Infra, F8:1A:67:D8:10:96, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA2
    TP-LINK_42B282:  Infra, F8:D1:11:42:B2:82, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Nameta:          Infra, 80:1F:02:49:1F:0E, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    FireGT-net:      Infra, 1C:AF:F7:28:52:30, Freq 2462 MHz, Rate 54 Mb/s, Strength 9 WPA WPA2
    *kyivstar96:     Infra, F8:1A:67:75:59:36, Freq 2462 MHz, Rate 54 Mb/s, Strength 63 WPA WPA2
    HomeMediaStation:Infra, AC:F1:DF:22:58:14, Freq 2427 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    dlink:           Infra, F0:7D:68:82:CE:04, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA2
    Dom:             Infra, 90:F6:52:84:63:A4, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA2
    Kiril:           Infra, 64:70:02:4C:44:5A, Freq 2412 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

```
4)Output for [B]lspci

[/B]```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)

```
5)Output for **iwconfig**
```

wlan0     IEEE 802.11bgn  ESSID:"kyivstar96"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: F8:1A:67:75:59:36   
          Bit Rate=135 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:32  Invalid misc:878   Missed beacon:0

```

I read [http://ubuntuforums.org/showthread.php?t=2080238](http://ubuntuforums.org/showthread.php?t=2080238) - put cat /sys/module/ath9k/parameters/nohwcrypt equal to 1, change sudo gedit /etc/modprobe.d/ath9k.conf: options ath9k nohwcrypt=1.
It reduced Tx excessive retries from few thousands to tens( as you see), but Invalid misc - still very high!

Could you help me please.

Thanks,

Rostyslav

---

### Post by praseodym on 2013-08-17
Which encryption mode do you use? I recommend pure WPA2-AES, if possible and a fixed channel

---

### Post by shevchenko-rostislav on 2013-08-17
Dear [**[COLOR=#000000]praseodym[/COLOR]**]("http://ubuntuforums.org/member.php?u=1411497"),

Thanks for your answer. I use WPA & WPA2 Personal and I couldn't change it ( it's not my own wi-fi point, it's from the work). Maybe there are any other possibilities to fix this problem?

regards,
Rostyslav

---

### Post by praseodym on 2013-08-17
Try Wicd instead of the NM:
```

wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
# Installation
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
Deactivate the NM in autostart (or uninstall it). The Add-On handles mixed encryptions better (wicd holds the connection, NM scans frequently which causes disconnects with mixed mode [in mixed mode WPA is the 'fallback' mode])

---

