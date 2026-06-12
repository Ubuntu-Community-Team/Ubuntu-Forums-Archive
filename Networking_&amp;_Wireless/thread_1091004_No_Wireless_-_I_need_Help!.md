---
title: "No Wireless - I need Help!"
date: 2009-03-08
forum: Networking &amp; Wireless
---

### Post by crokett on 2009-03-08
My laptop wireless was working ok at home with the Gnome network manager and network-admin.   However it would not connect to my LEAP network at work.  I installed Wicd. that worked at work but took forever to connect at home.  I removed that and reinstalled network-manager but could no longer connect to wireless at home.  I reinstalled wicd, Now I can't see any wireless networks at all. 

Hitting the refresh button in wicd does nothing.  I tried adding my home network ESSID as a hidden network, the wicd log file says it is setting that ESSID but the /etc/wicd/wireless-settings.conf file is empty.  

ifconfig lists both my wired and wireless adapters and wicd has the correct adapter selected for wireless.  

Any ideas?

---

### Post by Crafty Kisses on 2009-03-08
I need some more information, what are the results of these commands?
```
lsusb
lspci
lshw -C network
ifconfig
iwconfig
iwlist wlan0 scan
```
Post the results of those commands, and I or someone else can further assist you.

---

### Post by crokett on 2009-03-08
Here you go...


```

**lsusb results**
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
**lspci results**
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
 
**lshw results**
  *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:1a:6b:35:30:de
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.5-1 ip=192.168.1.8 latency=0 module=e1000e multicast=yes
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:19:7e:46:69:94
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:e7:0b:f8:b9:80
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
   
**ifconfig results**
ath0      Link encap:Ethernet  HWaddr 00:19:7e:46:69:94  
          inet6 addr: fe80::219:7eff:fe46:6994/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1a:6b:35:30:de  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:6bff:fe35:30de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2548 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1872438 (1.8 MB)  TX bytes:412423 (412.4 KB)
          Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1220 (1.2 KB)  TX bytes:1220 (1.2 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:9.65.239.107  P-t-P:9.65.239.107  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1362  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:16876 (16.8 KB)  TX bytes:4094 (4.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-19-7E-46-69-94-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:109 errors:0 dropped:0 overruns:0 frame:165723
          TX packets:417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:9237 (9.2 KB)  TX bytes:20358 (20.3 KB)
          Interrupt:17 

   
**iwconfig results**
ath0      IEEE 802.11g  ESSID:"DaCrib"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-77 dBm  Noise level=-77 dBm
          Rx invalid nwid:4  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

    
**iwlist scan results**
wlan0     Interface doesn't support scanning.



```

---

### Post by imdano on 2009-03-09
> **crokett said:**
> Hitting the refresh button in wicd does nothing.Try running wicd-client from a terminal, and post any error messages that pop up.  Even if wicd doesn't find anything when it scans, clicking refresh should at least make the GUI go gray for a few seconds.

---

### Post by crokett on 2009-03-09
Things are a little better.  After I updated the wireless driver wicd was able to see wireless networks at work again. Hopefully it can see them at home.  However I still cannot connect to a wireless network at work. I am not sure where I should be looking but I see this in syslog:

```

Mar  9 13:12:28 copernicus kernel: [ 4059.598621] wlan0: authenticate with AP 00:17:0f:e4:84:60
Mar  9 13:12:28 copernicus kernel: [ 4059.622855] wlan0: authenticated
Mar  9 13:18:29 copernicus kernel: [ 4420.895155] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate

```

I am required to use LEAP at work.  wicd has LEAP with WEP.  If I run the iwlist scan command now I see this. The question is what is in bold.  wicd has an option for LEAP with WEP. Should that work with the WEP listed below, or should I be looking for a client that supports LEAP w/WPA?

```

  Scan completed :
          Cell 01 - Address: 00:17:0F:E8:5C:E0
                    ESSID:""
                    Mode:Master
                    Channel:52
                    Frequency:5.26 GHz (Channel 52)
                    Quality=60/100  Signal level:-62 dBm  Noise level=-83 dBm
                    Encryption key:on
                    IE: Unknown: 000100
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050401020000
                    IE: Unknown: 070C555349240414340414950414
                    **IE: IEEE 802.11i/WPA2 Version 1**
                     **   Group Cipher : WEP-104**
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 851E040089001F00FF03190072706C2D61702D623230312D312D640005000026
                    IE: Unknown: 9606004096001100
                    IE: WPA Version 1
                        Group Cipher : WEP-104
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401
                    IE: Unknown: DD180050F2020101830003A5000027A5000042545E0062432F00
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000027facaef043
                    Extra: Last beacon: 9756ms ago


```

Here is the latest lshw for the wireless adapter. Google has several other references to this same issue with this adapter against WPA enabled networks. 
```

latency=0 module=e1000e multicast=yes
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:19:7e:46:69:94
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 module=ath5k multicast=yes wireless=IEEE 802.11abg

```

---

### Post by crokett on 2009-03-09
One more update.  I blacklisted the ath5k module and rolled back to the madwifi ath_pci driver after reading some bug reports on ath5k and WPA2.  That did not help.  The problem may be with wicd but at this point I am stuck.

---

### Post by crokett on 2009-03-09
Wireless is now working at home again.  wicd sees my home network and is connected with the older ath_pci driver.  I did have to enable SSID broadcast on my router.  It apparently does not like devices trying to attach without the SSID filled in and wicd did not want to take that as a parameter.  Maybe I should just get a WAP, a 2nd NIC and turn the linux server into a a router....

---

