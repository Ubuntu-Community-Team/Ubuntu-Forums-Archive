---
title: "Wireless connection established, no internet access"
date: 2013-08-20
forum: Networking &amp; Wireless
---

### Post by brill2 on 2013-08-20
I have a laptop running ubuntu 12.04 and a desktop computer running windows 7. The desktop had no problems connecting the internet through to my wireless router, but my laptop has problems.
I can connect to the network, but I don't have internet access. When i use an ethernet cable on the same laptop and router, I do have internet access. The wireless on the laptop _does_ work on other wireless routers (wireless in two different universities). 
Here are the outputs of some frequently asked commands:

```
corine@Corine-Laptop:~$ ifconfigeth0      Link encap:Ethernet  HWaddr d4:be:d9:84:32:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:95 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6080 (6.0 KB)  TX bytes:6080 (6.0 KB)


wlan0     Link encap:Ethernet  HWaddr 60:67:20:e0:53:84  
          inet addr:192.168.1.63  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6267:20ff:fee0:5384/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1631 (1.6 KB)  TX bytes:38224 (38.2 KB)


corine@Corine-Laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0






corine@Corine-Laptop:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no




corine@Corine-Laptop:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
^C
--- 8.8.8.8 ping statistics ---
12 packets transmitted, 0 received, 100% packet loss, time 10999ms


corine@Corine-Laptop:~$ ping www.google.com
^Z
[1]+  Stopped                 ping www.google.com






corine@Corine-Laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1c.5 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 6 (rev c4)
00:1c.6 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 7 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 (rev 34)
0b:00.0 SD Host controller: O2 Micro, Inc. Device 8221 (rev 05)
0c:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761 Gigabit Ethernet PCIe (rev 10)




corine@Corine-Laptop:~$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        D4:BE:D9:84:32:84


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: wlan0  [Zy_private_UW7UNA] -------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        60:67:20:E0:53:84


  Capabilities:
    Speed:           135 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    H220N8011DA:     Infra, FC:C8:97:80:11:DA, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    HG655D-CF3935:   Infra, 7A:E8:7B:CF:39:34, Freq 2452 MHz, Rate 54 Mb/s, Strength 45 WPA2
    vergeethetmaar:  Infra, 50:7E:5D:96:EA:61, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Ziggo:           Infra, 7E:E9:D3:18:07:E0, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2 Enterprise
    Jeanurvine:      Infra, A4:17:31:67:C7:53, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2
    Ziggo:           Infra, A6:17:31:67:C7:54, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2 Enterprise
    komkommertijd:   Infra, F4:EC:38:C7:9F:24, Freq 2472 MHz, Rate 54 Mb/s, Strength 25 WPA2
    Ziggo8A514:      Infra, 7C:E9:D3:18:07:EF, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA2
    linksys at home: Infra, 00:1E:E5:70:2F:0C, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA
    Doergamisier:    Infra, 00:23:54:ED:01:B0, Freq 2427 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    *Zy_private_UW7UNA: Infra, CC:5D:4E:9E:F3:8C, Freq 2412 MHz, Rate 54 Mb/s, Strength 78 WPA2
    Sitecom01F408:   Infra, 64:D1:A3:01:F4:08, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA2
    Ziggo:           Infra, EE:55:F9:20:D0:75, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    MRSJONES:        Infra, 4C:AC:0A:22:55:69, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Ziggo3E5D4:      Infra, EC:55:F9:20:D0:74, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA2
    SpeedTouchC452C7:Infra, 00:24:17:05:66:39, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    SitecomBDFB4C:   Infra, 00:0C:F6:BD:FB:4C, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    MMC@home:        Infra, 00:1A:70:99:A1:E4, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Zy_private_3779R7: Infra, CC:5D:4E:07:A9:F4, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA2
    Sitecom743550:   Infra, 00:0C:F6:74:35:50, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA2


  IPv4 Settings:
    Address:         192.168.1.63
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254
    DNS:             195.241.77.55
    DNS:             195.241.77.58







```

---

### Post by chili555 on 2013-08-20
I suggest you check here: [http://ubuntuforums.org/showthread.php?t=2168188&highlight=iwlwifi](http://ubuntuforums.org/showthread.php?t=2168188&highlight=iwlwifi)

---

### Post by brill2 on 2013-08-21
That did the trick. Thanks chili!

---

