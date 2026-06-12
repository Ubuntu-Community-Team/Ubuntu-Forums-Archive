---
title: "Intel 2200 bg on Thinkpad T40"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by Gumon on 2010-11-11
I have an old ThinkPad T40 2374, founded on e-bay with no OS and no wireless card and I ended installing Ubuntu Karmic and bought an Intel Pro/wireless 2200 bg  (Calexico) but the wireless can not find an IP. I am using a mac address instead of wep or wpa.

Can anybody help me to sort this out please. I am attaching a txt file with the results of: cat /var/log/syslog | grep -i network, iwconfig, lshw -C network,  dmesg | grep ipw, iwlist scan.  In that order.

Thank you.

---

### Post by Gumon on 2010-11-11
I could not manage to upload the txt file so instead:

Nov 11 22:54:54 gutmon-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/eth1, iface: eth1)
Nov 11 22:54:54 gutmon-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/eth1, iface: eth1): no ifupdown configuration found.
Nov 11 22:54:54 gutmon-laptop NetworkManager: <info>  (eth1): driver supports SSID scans (scan_capa 0x21).
Nov 11 22:54:54 gutmon-laptop NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'ipw2200')
Nov 11 22:54:54 gutmon-laptop NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Nov 11 22:54:54 gutmon-laptop NetworkManager: <info>  (eth1): now managed
Nov 11 22:54:54 gutmon-laptop NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Nov 11 22:54:54 gutmon-laptop NetworkManager: <info>  (eth1): bringing up device.
Nov 11 22:54:54 gutmon-laptop NetworkManager: <info>  (eth1): preparing device.
Nov 11 22:54:54 gutmon-laptop NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Nov 11 22:54:54 gutmon-laptop NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Nov 11 22:54:54 gutmon-laptop NetworkManager: <info>  modem-manager is now available
Nov 11 22:54:54 gutmon-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Nov 11 22:54:54 gutmon-laptop NetworkManager: <info>  Trying to start the supplicant...
Nov 11 22:54:54 gutmon-laptop NetworkManager: <info>  (eth1): supplicant manager state:  down -> idle
Nov 11 22:54:54 gutmon-laptop NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 0)
Nov 11 22:54:54 gutmon-laptop NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready
Nov 11 22:55:26 gutmon-laptop NetworkManager: <info>  Activation (eth1) starting connection 'Auto porfin'
Nov 11 22:55:26 gutmon-laptop NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
Nov 11 22:55:26 gutmon-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Nov 11 22:55:26 gutmon-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Nov 11 22:55:26 gutmon-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Nov 11 22:55:26 gutmon-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Nov 11 22:55:26 gutmon-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Nov 11 22:55:26 gutmon-laptop NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Nov 11 22:55:26 gutmon-laptop NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto porfin' requires no security.  No secrets needed.
Nov 11 22:55:26 gutmon-laptop NetworkManager: <info>  Config: added 'ssid' value 'porfin'
Nov 11 22:55:26 gutmon-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Nov 11 22:55:26 gutmon-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Nov 11 22:55:26 gutmon-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Nov 11 22:55:26 gutmon-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Nov 11 22:55:26 gutmon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  inactive -> scanning
Nov 11 22:55:53 gutmon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Nov 11 22:55:58 gutmon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
Nov 11 22:55:58 gutmon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Nov 11 22:55:58 gutmon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Nov 11 22:56:03 gutmon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
Nov 11 22:56:03 gutmon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Nov 11 22:56:03 gutmon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Nov 11 22:56:08 gutmon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
Nov 11 22:56:08 gutmon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Nov 11 22:56:08 gutmon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Nov 11 22:56:13 gutmon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
Nov 11 22:56:13 gutmon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Nov 11 22:56:14 gutmon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Nov 11 22:56:19 gutmon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
Nov 11 22:56:19 gutmon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Nov 11 22:56:19 gutmon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Nov 11 22:56:24 gutmon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
Nov 11 22:56:24 gutmon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Nov 11 22:56:24 gutmon-laptop NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Nov 11 22:56:27 gutmon-laptop NetworkManager: <info>  Activation (eth1/wireless): association took too long, failing activation.
Nov 11 22:56:27 gutmon-laptop NetworkManager: <info>  (eth1): device state change: 5 -> 9 (reason 11)
Nov 11 22:56:27 gutmon-laptop NetworkManager: <info>  Activation (eth1) failed for access point (porfin)
Nov 11 22:56:27 gutmon-laptop NetworkManager: <info>  Marking connection 'Auto porfin' invalid.
Nov 11 22:56:27 gutmon-laptop NetworkManager: <info>  Activation (eth1) failed.
Nov 11 22:56:27 gutmon-laptop NetworkManager: <info>  (eth1): device state change: 9 -> 3 (reason 0)
Nov 11 22:56:27 gutmon-laptop NetworkManager: <info>  (eth1): deactivating device (reason: 0).


iwconfig

eth1      unassociated  ESSID:"porfin"  
          Mode:Managed  Channel=0  Access Point: 00:1F:B3:00:22:81   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lshw -C network

*-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:57:ea:05
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: irq:11 memory:c0200000-c0200fff

---

### Post by Gumon on 2010-11-11
gutmon@gutmon-laptop:~$ dmesg | grep ipw

[   22.108460] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   22.108465] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   22.289853] ipw2200 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   22.289948] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   22.290005] ipw2200 0000:02:02.0: firmware: requesting ipw2200-bss.fw
[   22.734726] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)


gutmon@gutmon-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:26:F2:01:E2:CC
                    ESSID:"themadhouse"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=51/100  Signal level=-70 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 232ms ago
          Cell 02 - Address: 00:1B:2F:0A:23:AA
                    ESSID:"TheVillage"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=59/100  Signal level=-65 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Extra: Last beacon: 160ms ago
          Cell 03 - Address: 00:1F:B3:00:22:81
                    ESSID:"porfin"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:0
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=70/100  Signal level=-58 dBm  
                    Extra: Last beacon: 156ms ago
                    Extra: Channel flags: INVALID 
          Cell 04 - Address: 00:1B:9E:E1:43:E5
                    ESSID:"TalkTalkWhit"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=33/100  Signal level=-80 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 2612ms ago
          Cell 05 - Address: 02:24:17:E5:AC:F5
                    ESSID:"BTFON"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=44/100  Signal level=-74 dBm  
                    Extra: Last beacon: 180ms ago
          Cell 06 - Address: 00:24:17:E5:AC:F3
                    ESSID:"BTHomeHub2-4K8R"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=42/100  Signal level=-75 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 180ms ago
          Cell 07 - Address: 02:24:17:E5:AC:F4
                    ESSID:"BTOpenzone"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=41/100  Signal level=-76 dBm  
                    Extra: Last beacon: 184ms ago

---

