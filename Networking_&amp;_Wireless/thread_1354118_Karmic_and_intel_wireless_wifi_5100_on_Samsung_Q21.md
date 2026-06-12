---
title: "Karmic and intel wireless wifi 5100 on Samsung Q210"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by zyron72 on 2009-12-13
I'm unable to setup a wireless connection on Karmic.
I have build and installed the latest wireless drivers from [http://linuxwireless.org](http://linuxwireless.org) but still can't setup a working connection. Don't know what to do next. Any help is welcome.

lshw -C network:
  *-network                         
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation       
       physical id: 0                  
       bus info: pci@0000:02:00.0      
       logical name: wlan0             
       version: 00                     
       serial: 00:21:5d:8e:bb:5a       
       width: 64 bits                  
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f6000000-f6001fff

dmesg | grep iwl:
[16930.811339] iwlagn 0000:02:00.0: PCI INT A disabled
[16938.721662] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[16938.721665] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[16938.743339] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[16938.743342] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[16938.743604] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[16938.743637] iwlagn 0000:02:00.0: setting latency timer to 64
[16938.743698] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[16938.784309] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[16938.784389] iwlagn 0000:02:00.0: irq 30 for MSI/MSI-X
[16938.803605] phy0: Selected rate control algorithm 'iwl-agn-rs'
[16938.816433] iwlagn 0000:02:00.0: firmware: requesting lbm-iwlwifi-5000-2.ucode
[16938.830424] iwlagn 0000:02:00.0: loaded firmware version 8.24.2.12
[16938.987795] Registered led device: iwl-phy0::radio
[16938.987840] Registered led device: iwl-phy0::assoc
[16938.987880] Registered led device: iwl-phy0::RX
[16938.987918] Registered led device: iwl-phy0::TX


syslog:
Dec 13 20:34:57 nb-bart NetworkManager: <info>  Activation (wlan0) starting connection 'dommel'
Dec 13 20:34:57 nb-bart NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Dec 13 20:34:57 nb-bart NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 13 20:34:57 nb-bart NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 13 20:34:57 nb-bart NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 13 20:34:57 nb-bart NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 13 20:34:57 nb-bart NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 13 20:34:57 nb-bart NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Dec 13 20:34:57 nb-bart NetworkManager: <info>  Activation (wlan0/wireless): access point 'dommel' has security, but secrets are required.
Dec 13 20:34:57 nb-bart NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Dec 13 20:34:57 nb-bart NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 13 20:34:57 nb-bart NetworkManager: <WARN>  secrets_update_setting(): Failed to update connection secrets: 1 ipv4
Dec 13 20:34:57 nb-bart NetworkManager: <WARN>  secrets_update_setting(): Failed to update connection secrets: 1 802-1x
Dec 13 20:34:57 nb-bart NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 13 20:34:57 nb-bart NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 13 20:34:57 nb-bart NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Dec 13 20:34:57 nb-bart NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 13 20:34:57 nb-bart NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 13 20:34:57 nb-bart NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 13 20:34:57 nb-bart NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Dec 13 20:34:57 nb-bart NetworkManager: <info>  Activation (wlan0/wireless): connection 'dommel' has security, and secrets exist.  No new secrets needed.
Dec 13 20:34:57 nb-bart NetworkManager: <info>  Config: added 'ssid' value 'dommel'
Dec 13 20:34:57 nb-bart NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Dec 13 20:34:57 nb-bart NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Dec 13 20:34:57 nb-bart NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Dec 13 20:34:57 nb-bart NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec 13 20:34:57 nb-bart NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec 13 20:34:57 nb-bart NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 13 20:34:57 nb-bart NetworkManager: <info>  Config: set interface ap_scan to 1
Dec 13 20:34:57 nb-bart NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec 13 20:35:00 nb-bart wpa_supplicant[1159]: CTRL-EVENT-SCAN-RESULTS 
Dec 13 20:35:00 nb-bart wpa_supplicant[1159]: WPS-AP-AVAILABLE 
Dec 13 20:35:00 nb-bart wpa_supplicant[1159]: Trying to associate with 00:23:69:1d:8c:77 (SSID='dommel' freq=2412 MHz)
Dec 13 20:35:00 nb-bart NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec 13 20:35:00 nb-bart kernel: [17738.486909] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 1)
Dec 13 20:35:00 nb-bart kernel: [17738.682553] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 2)
Dec 13 20:35:00 nb-bart kernel: [17738.882564] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 3)
Dec 13 20:35:01 nb-bart kernel: [17739.082548] wlan0: direct probe to AP 00:23:69:1d:8c:77 timed out
Dec 13 20:35:10 nb-bart wpa_supplicant[1159]: CTRL-EVENT-SCAN-RESULTS 
Dec 13 20:35:10 nb-bart wpa_supplicant[1159]: Authentication with 00:23:69:1d:8c:77 timed out.
Dec 13 20:35:10 nb-bart NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec 13 20:35:15 nb-bart NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec 13 20:35:18 nb-bart wpa_supplicant[1159]: CTRL-EVENT-SCAN-RESULTS 
Dec 13 20:35:18 nb-bart wpa_supplicant[1159]: WPS-AP-AVAILABLE 
Dec 13 20:35:18 nb-bart wpa_supplicant[1159]: Trying to associate with 00:23:69:1d:8c:77 (SSID='dommel' freq=2412 MHz)
Dec 13 20:35:18 nb-bart NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec 13 20:35:18 nb-bart kernel: [17756.391613] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 1)
Dec 13 20:35:18 nb-bart kernel: [17756.592561] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 2)
Dec 13 20:35:18 nb-bart kernel: [17756.790438] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 3)
Dec 13 20:35:19 nb-bart kernel: [17756.992574] wlan0: direct probe to AP 00:23:69:1d:8c:77 timed out
Dec 13 20:35:26 nb-bart NetworkManager: <info>  wlan0: link timed out.
Dec 13 20:35:28 nb-bart wpa_supplicant[1159]: Authentication with 00:23:69:1d:8c:77 timed out.
Dec 13 20:35:28 nb-bart NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec 13 20:35:28 nb-bart NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec 13 20:35:31 nb-bart wpa_supplicant[1159]: CTRL-EVENT-SCAN-RESULTS 
Dec 13 20:35:31 nb-bart wpa_supplicant[1159]: WPS-AP-AVAILABLE 
Dec 13 20:35:31 nb-bart wpa_supplicant[1159]: Trying to associate with 00:23:69:1d:8c:77 (SSID='dommel' freq=2412 MHz)
Dec 13 20:35:31 nb-bart NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec 13 20:35:31 nb-bart kernel: [17769.613332] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 1)
Dec 13 20:35:31 nb-bart kernel: [17769.811387] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 2)
Dec 13 20:35:32 nb-bart kernel: [17770.010057] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 3)
Dec 13 20:35:32 nb-bart kernel: [17770.210247] wlan0: direct probe to AP 00:23:69:1d:8c:77 timed out
Dec 13 20:35:41 nb-bart wpa_supplicant[1159]: Authentication with 00:23:69:1d:8c:77 timed out.
Dec 13 20:35:41 nb-bart NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec 13 20:35:41 nb-bart NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec 13 20:35:44 nb-bart wpa_supplicant[1159]: CTRL-EVENT-SCAN-RESULTS 
Dec 13 20:35:44 nb-bart wpa_supplicant[1159]: WPS-AP-AVAILABLE 
Dec 13 20:35:44 nb-bart wpa_supplicant[1159]: Trying to associate with 00:23:69:1d:8c:77 (SSID='dommel' freq=2412 MHz)
Dec 13 20:35:44 nb-bart NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec 13 20:35:44 nb-bart kernel: [17782.863782] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 1)
Dec 13 20:35:45 nb-bart kernel: [17783.060072] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 2)
Dec 13 20:35:45 nb-bart kernel: [17783.260073] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 3)
Dec 13 20:35:45 nb-bart kernel: [17783.460058] wlan0: direct probe to AP 00:23:69:1d:8c:77 timed out
Dec 13 20:35:54 nb-bart wpa_supplicant[1159]: Authentication with 00:23:69:1d:8c:77 timed out.
Dec 13 20:35:54 nb-bart NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Dec 13 20:35:54 nb-bart NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec 13 20:35:58 nb-bart NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Dec 13 20:35:58 nb-bart NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Dec 13 20:35:58 nb-bart NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Dec 13 20:35:58 nb-bart NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected

---

### Post by zyron72 on 2009-12-13
Perhaps the linux kernel version is of any help:

uname -a:
Linux nb-bart 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux

---

### Post by bkratz on 2009-12-13
Here is a thread with a lot of users having the same problem and several of them fixed it in different manners (some never), but I think it is worth reading to see if any of your symptoms match. Especially note their comments about different types of encryption.

[http://ubuntuforums.org/showthread.php?t=1307396&highlight=5100](http://ubuntuforums.org/showthread.php?t=1307396&highlight=5100)

---

### Post by zyron72 on 2009-12-14
Thanks bkratz, but could not fix it with the info found in that link (didn't try the customized kernel build)

Below is a repost of the information conform to the guidelines found in the sticky.

1) Machine Brand and Model:
Samsung Q210 Laptop

2) Wireless Brand, Model and Wireless Chipset:
lspci -nn | grep '5100'
02:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]

3) Check interface:
ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:21:5d:8e:bb:5a
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     IEEE 802.11abgn  ESSID:"dommel"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=15 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

4) Check for modules:
lsmod | grep iwlagn
iwlagn                124768  0
iwlcore               134820  1 iwlagn
mac80211              243360  2 iwlagn,iwlcore
cfg80211              152424  3 iwlagn,iwlcore,mac80211

5) Kernel boot messages:
dmesg | grep wlan0
[   20.803345] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   59.374077] wlan0: deauthenticating from 00:23:69:1d:8c:77 by local choice (reason=3)
[   59.374124] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 1)
[   59.570041] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 2)
[   59.770043] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 3)
[   59.970032] wlan0: direct probe to AP 00:23:69:1d:8c:77 timed out
[   72.554441] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 1)
[   72.750036] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 2)
[   72.950039] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 3)
[   73.150030] wlan0: direct probe to AP 00:23:69:1d:8c:77 timed out
[   85.777882] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 1)
[   85.970072] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 2)
[   86.170065] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 3)
[   86.370054] wlan0: direct probe to AP 00:23:69:1d:8c:77 timed out
[   98.989012] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 1)
[   99.180070] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 2)
[   99.380058] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 3)
[   99.580064] wlan0: direct probe to AP 00:23:69:1d:8c:77 timed out

6) Network configuration:
sudo lshw -C network
[sudo] password for bart:
  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:5d:8e:bb:5a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f6000000-f6001fff

7) Scan for networks:
iwlist wlan0 scan                       
wlan0     Scan completed :                              
          // removed this info because irrelevant: Cell 01 -                                       
          Cell 02 - Address: 00:23:69:1D:8C:77                                           
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm
                    Encryption key:on
                    ESSID:"dommel"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000c11d8150
                    Extra: Last beacon: 3040ms ago
                    IE: Unknown: 0006646F6D6D656C
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A8800023691D8C77103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000

8) Ubuntu version:
lsb_release -d
Description:    Ubuntu 9.10

9) Kernel/Architecture:
uname -mr
2.6.31-16-generic x86_64

10) Restarting the network:
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                  Ignoring unknown interface eth0=eth0.

---

### Post by coffeecat on 2009-12-14
Did you try with the drivers that come with a default install of Karmic before you downloaded and installed the drivers from linuxwireless? The Intel 5100 wireless on this Sony laptop works out of the box in Karmic. I've tried both Ubuntu and Kubuntu. In each case (K)Network Manager connected in seconds.

I was intrigued by these lines from your lshw -C network and dmesg:

> **zyron72 said:**
> 

lshw -C network:

...

       product: Wireless WiFi Link 5100
       vendor: Intel Corporation

...

**driver=iwlagn**

-

dmesg | grep iwl:
[16930.811339] **iwlagn 0000:02:00.0: PCI INT A disabled**
[16938.721662] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks

Now compare my lshw:

```
*-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 00
       serial: 00:22:fb:23:ac:d6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.64 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:d0500000-d0501fff
```and dmesg....

```
$ dmesg | grep iwl
[   18.726219] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   18.726224] iwlagn: Copyright(c) 2003-2009 Intel Corporation
```Mine is running just fine with the inbuilt iwlagn driver. It looks as though your iwl3945 driver is interfering with the iwlagn. Is the iwl3945 the one you downloaded and installed? Have you tried booting from a live CD and seeing if you can connect with the inbuilt driver?

---

### Post by zyron72 on 2009-12-14
@coffeecat
1) I installed a fresh Kubuntu Karmic on my laptop when it was released, but didn't try wireless right away. Last week I upgraded to kernel 2.6.31-16 and tried to get wireless working. I tried various settings (B/G/N, plain/WEP/WPA(2)) all without success. Then I tried to add the option pci=use_crs to the grub configuration, and tried to install the latest compat wireless drivers which I have running now (2.6.32). All without success.

Next are my current kernel messages (go in par with the logging above only better grep'ing):
```
dmesg | grep iwl
[   19.951345] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   19.951348] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   19.963916] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.963950] iwlagn 0000:02:00.0: setting latency timer to 64
[   19.964010] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   20.003126] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   20.003210] iwlagn 0000:02:00.0: irq 30 for MSI/MSI-X
[   20.010605] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   20.493057] iwlagn 0000:02:00.0: firmware: requesting lbm-iwlwifi-5000-2.ucode
[   20.622629] iwlagn 0000:02:00.0: loaded firmware version 8.24.2.12
[   20.774390] Registered led device: iwl-phy0::radio
[   20.774409] Registered led device: iwl-phy0::assoc
[   20.774426] Registered led device: iwl-phy0::RX
[   20.774448] Registered led device: iwl-phy0::TX
```2) I have put iwl3945 on the blacklist in /etc/modprobe.d/blacklist.conf, doesn't change a thing.
3) I have tried the live cd (has kernel 2.6.31-14-generic x86_64), it doesn't work. I had a look at the syslog and see these common errors:

```
NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed                     
NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
...
kernel: [  470.824778] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 1)
kernel: [  471.020041] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 2)
kernel: [  471.220041] wlan0: direct probe to AP 00:23:69:1d:8c:77 (try 3)
kernel: [  471.420049] wlan0: direct probe to AP 00:23:69:1d:8c:77 timed out
```I guess there is no point in a reinstall since live-cd doesn't work neither ...

---

### Post by coffeecat on 2009-12-15
That is disappointing. I've seen a couple of other threads where people were having problems with the 5100 chipset. It's odd that it works in some machines and not others. I wonder if it might be something to do with the ACPI implementation in some machines. That seems to be a minefield of causing bizarre problems.

---

### Post by zyron72 on 2009-12-15
I've added "acpi=off" to the grub configuration, did a reboot and tried to setup a connection. Also no success. I see the same errors again in syslog (NM_IS_SETTING_802_1X) and dmesg (direct probe to AP timeout)

---

### Post by zyron72 on 2009-12-16
Got it working! I think it has nothing todo with kubuntu, but i'm not sure about that because i'm still working with the latest compat wireless driver (2.6.32).
The problem was caused by my access point. I have a Linksys WRT160N-V2 access point, I needed to change the 'Standard Channel' in the 'Basic Wireless Settings' from 'Auto' to '11 - 2,462GHz'.
I've been able to create a connection over Wireless-N in 'plain' and with 'wpa2 personal'.

Thanks for the help!

---

### Post by coffeecat on 2009-12-16
> **zyron72 said:**
> I have a Linksys WRT160N-V2 access point, I needed to change the 'Standard Channel' in the 'Basic Wireless Settings' from 'Auto' to '11 - 2,462GHz'.
I've been able to create a connection over Wireless-N in 'plain' and with 'wpa2 personal'.

That's interesting. I'm using an older Linksys 'G' router and I can only set individual channels (1-13) - obviously on the 2.4GHz frequencies since it's G. There's no 'auto' setting in 'Basic Wireless'.

Does the 'auto' setting use the 5GHz band? If so, I wonder if this might be the problem.

---

### Post by zyron72 on 2009-12-16
These are the options I can select from the Standard Channel: Auto; 1-2,412Ghz; 2-2,417Ghz; 3-2,422Ghz; 4-2,427Ghz; 5-2,432Ghz; 6-2,437; 7-2,442Ghz; 8-2,447Ghz; 9-2,452Ghz; 10-2,457Ghz; 11-2,462Ghz. A quick look into the UserGuide doesn't reveal anything about 5GHz ...

---

### Post by coffeecat on 2009-12-16
Hmmm. Curious. I wonder what 'Auto' does.

---

