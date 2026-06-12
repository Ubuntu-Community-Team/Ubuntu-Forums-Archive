---
title: "WPA2 authentification times out"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by iarspider on 2010-12-05
I've got a Dell XPS M1530 with Intel 4965 AGN wireless card (dual-booting Ubuntu 10.10 and WIndows 7) connecting to a D-Link DIR-855 (simultaneous dual-band router). The router serves two SSIDs: one on 2.4 GHz, one on 5 GHz.

When I installed Ubuntu 10.04 (clean install) on laptop, both 2.4 GHz and 5 GHz modes were working fine. However, since the upgrade to 10.10 I can't connect on 5 GHz, but can on 2.4 GHz. I'm 1000% sure I use correct passphrase, and the router doesn't use MAC filtering. I can connect on 5 GHz from Windows 7.

Here is an extract from daemon.log:
```

Dec  5 12:01:03 CYBERNOTE NetworkManager[1209]: <info> (wlan0): bringing up device.
Dec  5 12:01:03 CYBERNOTE NetworkManager[1209]: <info> (wlan0): supplicant interface state:  starting -> ready
Dec  5 12:01:03 CYBERNOTE NetworkManager[1209]: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> Activation (wlan0) starting connection 'Auto homewlan50'
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> Activation (wlan0/wireless): access point 'Auto homewlan50' has security, but secrets are required.
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> Activation (wlan0/wireless): connection 'Auto homewlan50' has security, and secrets exist.  No new secrets needed.
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> Config: added 'ssid' value 'homewlan50'
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> Config: added 'scan_ssid' value '1'
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> Config: added 'psk' value '<omitted>'
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> Config: set interface ap_scan to 1
Dec  5 12:01:09 CYBERNOTE NetworkManager[1209]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Dec  5 12:01:11 CYBERNOTE wpa_supplicant[1311]: Trying to associate with 00:22:b0:b5:af:75 (SSID='homewlan50' freq=5200 MHz)
Dec  5 12:01:11 CYBERNOTE NetworkManager[1209]: <info> (wlan0): supplicant connection state:  scanning -> associating
Dec  5 12:01:21 CYBERNOTE wpa_supplicant[1311]: Authentication with 00:22:b0:b5:af:75 timed out.
Dec  5 12:01:21 CYBERNOTE NetworkManager[1209]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Dec  5 12:01:21 CYBERNOTE NetworkManager[1209]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Dec  5 12:01:22 CYBERNOTE wpa_supplicant[1311]: Trying to associate with 00:22:b0:b5:af:75 (SSID='homewlan50' freq=5200 MHz)
Dec  5 12:01:22 CYBERNOTE NetworkManager[1209]: <info> (wlan0): supplicant connection state:  scanning -> associating
Dec  5 12:01:32 CYBERNOTE wpa_supplicant[1311]: Authentication with 00:22:b0:b5:af:75 timed out.
Dec  5 12:01:32 CYBERNOTE NetworkManager[1209]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Dec  5 12:01:32 CYBERNOTE NetworkManager[1209]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Dec  5 12:01:34 CYBERNOTE wpa_supplicant[1311]: Trying to associate with 00:22:b0:b5:af:75 (SSID='homewlan50' freq=5200 MHz)
Dec  5 12:01:34 CYBERNOTE NetworkManager[1209]: <info> (wlan0): supplicant connection state:  scanning -> associating
Dec  5 12:01:44 CYBERNOTE wpa_supplicant[1311]: Authentication with 00:22:b0:b5:af:75 timed out.
Dec  5 12:01:44 CYBERNOTE NetworkManager[1209]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Dec  5 12:01:44 CYBERNOTE NetworkManager[1209]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Dec  5 12:01:45 CYBERNOTE wpa_supplicant[1311]: Trying to associate with 00:22:b0:b5:af:75 (SSID='homewlan50' freq=5200 MHz)
Dec  5 12:01:45 CYBERNOTE NetworkManager[1209]: <info> (wlan0): supplicant connection state:  scanning -> associating
Dec  5 12:01:51 CYBERNOTE NetworkManager[1209]: <warn> (wlan0): link timed out.
Dec  5 12:01:55 CYBERNOTE wpa_supplicant[1311]: Authentication with 00:22:b0:b5:af:75 timed out.
Dec  5 12:01:55 CYBERNOTE NetworkManager[1209]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Dec  5 12:01:55 CYBERNOTE NetworkManager[1209]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Dec  5 12:01:57 CYBERNOTE wpa_supplicant[1311]: Trying to associate with 00:22:b0:b5:af:75 (SSID='homewlan50' freq=5200 MHz)
Dec  5 12:01:57 CYBERNOTE NetworkManager[1209]: <info> (wlan0): supplicant connection state:  scanning -> associating
Dec  5 12:02:07 CYBERNOTE wpa_supplicant[1311]: Authentication with 00:22:b0:b5:af:75 timed out.
Dec  5 12:02:07 CYBERNOTE NetworkManager[1209]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Dec  5 12:02:07 CYBERNOTE NetworkManager[1209]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Dec  5 12:02:08 CYBERNOTE wpa_supplicant[1311]: Trying to associate with 00:22:b0:b5:af:75 (SSID='homewlan50' freq=5200 MHz)
Dec  5 12:02:08 CYBERNOTE NetworkManager[1209]: <info> (wlan0): supplicant connection state:  scanning -> associating
Dec  5 12:02:10 CYBERNOTE NetworkManager[1209]: <warn> Activation (wlan0/wireless): association took too long. 

```

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:21:9b:d8:c6:b4  
          inet6 addr: fe80::221:9bff:fed8:c6b4/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:172225 errors:0 dropped:0 overruns:0 frame:0
          TX packets:127175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:177761622 (177.7 MB)  TX bytes:23261289 (23.2 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:956 errors:0 dropped:0 overruns:0 frame:0
          TX packets:956 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77191 (77.1 KB)  TX bytes:77191 (77.1 KB)

pan1      Link encap:Ethernet  HWaddr 26:de:36:80:3b:48  
          inet addr:10.71.232.1  Bcast:10.71.232.255  Mask:255.255.255.0
          inet6 addr: fe80::24de:36ff:fe80:3b48/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:14580 (14.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:5c:52:6b:41  
          inet addr:192.168.1.92  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5cff:fe52:6b41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2084 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1557631 (1.5 MB)  TX bytes:398761 (398.7 KB)
 
```

iwconfig (associated to same AP but on 2.4 GHz):
```

wlan0     IEEE 802.11abg  ESSID:"homewlan24"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:22:B0:B5:AF:73   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lshw -C Network:
```

  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:d8:c6:b4
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A latency=0 link=no multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:f1ffc000-f1ffffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 61
       serial: 00:21:5c:52:6b:41
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-23-generic-pae firmware=228.61.2.24 ip=192.168.1.92 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:f1efe000-f1efffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes 

```

lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61) 

```

---

