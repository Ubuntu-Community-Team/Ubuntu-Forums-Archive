---
title: "can't connect to wifi  2200BG/ubuntu 8.10/acer travelmate 4100"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by toasty mofo on 2009-02-19
Hey, I'm having a lot of problems trying to connect to a wireless network from ubuntu. It acts as if the password I enter is continually wrong - keeps displaying the network manager prompt.

Here's the requested output
```
06:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)

dimitri@d-crunch:~$ iwconfig
lo        no wireless extensions.

eth0      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

dimitri@d-crunch:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0e:35:a6:97:59  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 Memory:c820b000-c820bfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1688 (1.6 KB)  TX bytes:1688 (1.6 KB)

iwlist scan
lo        Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: 00:1D:68:A7:F1:DB
                    ESSID:"BTHomeHub-0BF4"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=62/100  Signal level=-63 dBm  
                    Extra: Last beacon: 0ms ago
          Cell 02 - Address: 00:14:7F:94:07:A1
                    ESSID:"BTHomeHub-213A"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=62/100  Signal level=-71 dBm  
                    Extra: Last beacon: 216ms ago
          Cell 03 - Address: 00:1F:9E:D3:BD:50
                    ESSID:"BTOpenzone"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=42/100  Signal level=-75 dBm  
                    Extra: Last beacon: 528ms ago
          Cell 04 - Address: 00:1B:2F:FE:E6:00
                    ESSID:"budak"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=39/100  Signal level=-77 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 236ms ago
          Cell 05 - Address: 00:1E:74:86:D1:59
                    ESSID:"SKY53592"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=44/100  Signal level=-74 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 8076ms ago

pan0      Interface doesn't support scanning.

uname -mr
2.6.27-9-generic i686



```

also here's a syslog section that shows the disconnections

```
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Marking connection 'Auto BTHomeHub-0BF4' invalid. 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Activation (eth0) failed. 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  (eth0): device state change: 9 -> 3 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Activation (eth0) starting connection 'Auto BTHomeHub-213A' 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Activation (eth0/wireless): access point 'Auto BTHomeHub-213A' has security, but secrets are required. 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  (eth0): device state change: 5 -> 6 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 7 -> 0 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  (eth0): device state change: 6 -> 4 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Activation (eth0/wireless): connection 'Auto BTHomeHub-213A' has security, and secrets exist.  No new secrets needed. 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Config: added 'ssid' value 'BTHomeHub-213A' 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Config: added 'auth_alg' value 'SHARED' 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Config: added 'wep_key3' value '<omitted>' 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '3' 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  Config: set interface ap_scan to 1 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 0 -> 2 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 2 -> 3 
Feb 19 13:11:14 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 3 -> 0 
Feb 19 13:11:19 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 0 -> 3 
Feb 19 13:11:21 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 3 -> 0 
Feb 19 13:11:23 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 0 -> 3 
Feb 19 13:11:24 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 3 -> 0 
Feb 19 13:11:28 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 0 -> 3 
Feb 19 13:11:29 d-crunch NetworkManager: <info>  eth0: link timed out. 
Feb 19 13:11:30 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 3 -> 0 
Feb 19 13:11:33 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 0 -> 3 
Feb 19 13:11:33 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 3 -> 0 
Feb 19 13:11:37 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 0 -> 3 
Feb 19 13:11:39 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 3 -> 0 
Feb 19 13:11:41 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 0 -> 3 
Feb 19 13:11:42 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 3 -> 0 
Feb 19 13:11:45 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 0 -> 3 
Feb 19 13:11:45 d-crunch NetworkManager: <info>  eth0: link timed out. 
Feb 19 13:11:45 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 3 -> 0 
Feb 19 13:11:49 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 0 -> 2 
Feb 19 13:11:49 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 2 -> 3 
Feb 19 13:11:52 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 3 -> 0 
Feb 19 13:11:53 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 0 -> 3 
Feb 19 13:11:55 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 3 -> 0 
Feb 19 13:11:58 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 0 -> 3 
Feb 19 13:12:00 d-crunch NetworkManager: <info>  eth0: link timed out. 
Feb 19 13:12:01 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 3 -> 0 
Feb 19 13:12:03 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 0 -> 3 
Feb 19 13:12:04 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 3 -> 0 
Feb 19 13:12:07 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 0 -> 3 
Feb 19 13:12:07 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 3 -> 0 
Feb 19 13:12:12 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 0 -> 3 
Feb 19 13:12:13 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 3 -> 0 
Feb 19 13:12:14 d-crunch NetworkManager: <info>  Activation (eth0/wireless): association took too long. 
Feb 19 13:12:14 d-crunch NetworkManager: <info>  (eth0): device state change: 5 -> 6 
Feb 19 13:12:14 d-crunch NetworkManager: <info>  Activation (eth0/wireless): asking for new secrets 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 0 -> 3 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 3 -> 0 
Feb 19 13:12:16 d-crunch NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1512 (get_secrets_dialog_response_cb): canceled. 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  (eth0): device state change: 6 -> 9 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Activation (eth0) failed for access point (BTHomeHub-213A) 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Marking connection 'Auto BTHomeHub-213A' invalid. 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Activation (eth0) failed. 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  (eth0): device state change: 9 -> 3 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Activation (eth0) starting connection 'Auto BTHomeHub-0BF4' 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Activation (eth0/wireless): access point 'Auto BTHomeHub-0BF4' has security, but secrets are required. 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  (eth0): device state change: 5 -> 6 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  (eth0): device state change: 6 -> 4 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Activation (eth0/wireless): connection 'Auto BTHomeHub-0BF4' has security, and secrets exist.  No new secrets needed. 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Config: added 'ssid' value 'BTHomeHub-0BF4' 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  Config: set interface ap_scan to 1 
Feb 19 13:12:16 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 0 -> 2 
Feb 19 13:12:17 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 2 -> 3 
Feb 19 13:12:17 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 3 -> 4 
Feb 19 13:12:17 d-crunch NetworkManager: <info>  (eth0): supplicant connection state change: 4 -> 7 
Feb 19 13:12:17 d-crunch NetworkManager: <info>  Activation (eth0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'BTHomeHub-0BF4'. 
Feb 19 13:12:17 d-crunch NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Feb 19 13:12:17 d-crunch NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Feb 19 13:12:17 d-crunch NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Feb 19 13:12:17 d-crunch NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Feb 19 13:12:17 d-crunch dhclient: Internet Systems Consortium DHCP Client V3.1.1
Feb 19 13:12:17 d-crunch dhclient: Copyright 2004-2008 Internet Systems Consortium.
Feb 19 13:12:17 d-crunch dhclient: All rights reserved.
Feb 19 13:12:17 d-crunch dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Feb 19 13:12:17 d-crunch dhclient: 
Feb 19 13:12:17 d-crunch NetworkManager: <info>  dhclient started with pid 5932 
Feb 19 13:12:17 d-crunch NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Feb 19 13:12:17 d-crunch NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit 
Feb 19 13:12:17 d-crunch dhclient: Listening on LPF/eth0/00:0e:35:a6:97:59
Feb 19 13:12:17 d-crunch dhclient: Sending on   LPF/eth0/00:0e:35:a6:97:59
Feb 19 13:12:17 d-crunch dhclient: Sending on   Socket/fallback
Feb 19 13:12:20 d-crunch dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Feb 19 13:12:25 d-crunch dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Feb 19 13:12:30 d-crunch ntfs-3g[5963]: Version 1.2506 external FUSE 27 
Feb 19 13:12:30 d-crunch ntfs-3g[5963]: Mounted /dev/sdb1 (Read-Only, label "HD-CEU2", NTFS 3.1) 
Feb 19 13:12:30 d-crunch ntfs-3g[5963]: Cmdline options: ro,nosuid,nodev,uhelper=hal,umask=222,utf8 
Feb 19 13:12:30 d-crunch ntfs-3g[5963]: Mount options: ro,nosuid,nodev,uhelper=hal,utf8,silent,allow_other,nonempty,default_permissions,relatime,fsname=/dev/sdb1,blkdev,blksize=4096 
Feb 19 13:12:30 d-crunch hald: mounted /dev/sdb1 on behalf of uid 1000
Feb 19 13:12:38 d-crunch dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Feb 19 13:12:57 d-crunch dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Feb 19 13:13:02 d-crunch NetworkManager: <info>  Device 'eth0' DHCP transaction took too long (>45s), stopping it. 
Feb 19 13:13:02 d-crunch NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 5932 
Feb 19 13:13:02 d-crunch NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Feb 19 13:13:02 d-crunch NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
Feb 19 13:13:02 d-crunch NetworkManager: <info>  Activation (eth0/wireless): could not get IP configuration for connection 'Auto BTHomeHub-0BF4'. 
Feb 19 13:13:02 d-crunch NetworkManager: <info>  (eth0): device state change: 7 -> 6 
Feb 19 13:13:02 d-crunch NetworkManager: <info>  Activation (eth0/wireless): asking for new secrets 
Feb 19 13:13:02 d-crunch NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 
Feb 19 13:13:04 d-crunch NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1512 (get_secrets_dialog_response_cb): canceled. 
Feb 19 13:13:04 d-crunch NetworkManager: <info>  (eth0): device state change: 6 -> 9 
Feb 19 13:13:04 d-crunch NetworkManager: <info>  Activation (eth0) failed for access point (BTHomeHub-0BF4) 
Feb 19 13:13:04 d-crunch NetworkManager: <info>  Marking connection 'Auto BTHomeHub-0BF4' invalid. 
Feb 19 13:13:04 d-crunch NetworkManager: <info>  Activation (eth0) failed. 
Feb 19 13:13:04 d-crunch NetworkManager: <info>  (eth0): device state change: 9 -> 3 
Feb 19 13:13:04 d-crunch NetworkManager: <info>  (eth0): deactivating device (reason: 0).
```

My computer is an Acer Travelmate 4100, please tell me if I need to give more info. 

I notice that my ethernet card doesn't show up, and instead my wireless card has the title eth0, does this mean anything?

Any help you can give me would be great, thanks

---

### Post by toasty mofo on 2009-02-21
Bump??

I can't access the internet at all. The network is WEP encrypted, all the hardware works fine when I'm using XP.

---

### Post by superprash2003 on 2009-02-21
did you use the right authentication type like 64bit or 128 bit etc.. try all combinations if not sure

---

### Post by toasty mofo on 2009-02-21
how do I enter a 64 bit hex key as 128 bit??

---

### Post by superprash2003 on 2009-02-22
it usually pops up asking for the WEP key.. where you could choose the type like 64bit or 128bit..

---

### Post by toasty mofo on 2009-02-22
yes, but my key is still 64 bit... would you have me add random values to make up the other 64 bits??

---

### Post by Joe2Shoe on 2009-02-22
I'm running Ubuntu v8.10 on one of my laptops with that same exact IntelPRO 2200BG PCI WiFi card installed.
It works fine.  I'm using WEP with a 64 character password.
Try changing from 64bit to 128bit password.

---

### Post by toasty mofo on 2009-02-24
I'm not going to change my network to revolve around ubuntu. I'm going to drop ubuntu, wifi works ootb with windows. 

It used to work fine with hardy but as I don't have a postgrad in networking I guess I'm too stupid to be allowed 8.10. Thanks for the non-answers.

---

### Post by superprash2003 on 2009-02-25
dont worry about the no of characters.. use the correct,original WEP key itself.. you dont need to add anything.. just try the same key for 64bit and 128bit

---

