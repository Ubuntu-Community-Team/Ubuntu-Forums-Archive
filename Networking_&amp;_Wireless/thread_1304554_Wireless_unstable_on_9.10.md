---
title: "Wireless unstable on 9.10"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by Linuxgood on 2009-10-29
I have a PCI card in my computer, which worked flawlessly until yesterday. I installed Ubuntu 9.10 RC a couple of days ago, and it worked there until something happened, maybe some software upgrades broke it ?

Now, to get wireless internet I have a USB stick, which works for a period of time and then dies. If I then unplug it and plug in again, it works again. Also, the wireless app in the upper right corner is sometimes searching for the net and reports back connection off, but there is connection anyway.

My wireless PCI card worked fine in 9.04

USB: Ather USB2.0 WLAN
PCI: Ralink RT2561 802.11g

---

### Post by GarrettFoster on 2009-11-04
I am going to piggy-back on this thread as my card is also a RT2561 and I am also experiencing problems after upgrading from 9.04 to 9.10. My card is also a pci version. I did pull it out and check to make sure it was the right card that was detected by the system. 

My results are similar to those of the OP. I can use the Internet fine for a while and then suddenly for some unknown reason the card will just disconnect. After is disconnects it tries to re-connect automatically but normally fails to do so even though I can see all the networks at reasonable strength through network manager. The only work-around I have right now is to disable the wireless, disable the network and then re-enable everything a few seconds later.

Anyways while it was down I ran through most of the stuff in this thread: [http://ubuntuforums.org/showthread.php?p=6183681]("http://ubuntuforums.org/showthread.php?p=6183681")

Here is the output

```
$ lsb_release -d
Description:	Ubuntu 9.10
```

```
$ uname -mr
2.6.31-14-generic i686
```

```
$ lspci -nn | grep Network
01:06.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
```


```

**After a disconnect**

$ iwconfig wlan0
wlan0     IEEE 802.11bg  Mode:Managed  Frequency:2.417 GHz  
          Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**While connected**

$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"3280_2D"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:14:6C:A2:50:B0   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


```

**After a disconnect**

$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: wmaster0
       version: 00
       serial: 00:fd:07:92:db:d2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fdef8000-fdefffff

**While Connected**

$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: wmaster0
       version: 00
       serial: 00:fd:07:92:db:d2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.3 latency=64 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fdef8000-fdefffff
```


```

**After a disconnect...note that Network Manager is still showing all the available networks**

$ iwlist wlan0 scanning
wlan0     No scan results

**While connected or trying to re-connect**

$ iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:18:39:EF:70:6D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"diceaxp"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b66c88185
                    Extra: Last beacon: 9464ms ago
                    IE: Unknown: 000764696365617870
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020014
          Cell 02 - Address: 00:14:6C:A2:50:B0
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"3280_2D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000ef76206d
                    Extra: Last beacon: 2600ms ago                
          Cell 03 - Address: 00:18:4D:9C:20:72
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Warren's Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002f717bc181
                    Extra: Last beacon: 2052ms ago
                    IE: Unknown: 001057617272656E2773204E6574776F726B
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F0101000EFF7F
                    IE: Unknown: DD1A00037F030100000000184D9C207202184D9C207264002C010E08
          Cell 04 - Address: 00:24:B2:28:FE:20
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"PaddlynMadlyn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001313810e5f7
                    Extra: Last beacon: 8844ms ago
                    IE: Unknown: 000D506164646C796E4D61646C796E
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:14:6C:95:45:56
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"OSCAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003df6e8b870
                    Extra: Last beacon: 8840ms ago
                    IE: Unknown: 00054F53434152
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020000
```

```
$  lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
arc4                    1660  2 
ecb                     2524  2 
rt61pci                20576  0 
crc_itu_t               1852  1 rt61pci
rt2x00pci               7900  1 rt61pci
rt2x00lib              29756  2 rt61pci,rt2x00pci
led_class               4096  1 rt2x00lib
iptable_filter          3100  0 
input_polldev           3716  1 rt2x00lib
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
nvidia               9586440  36 
mac80211              181236  2 rt2x00pci,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211
agpgart                34988  1 nvidia
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
eeprom_93cx6            1916  1 rt61pci
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ppdev                   6688  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                56180  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
serio_raw               5280  0 
k8temp                  4188  0 
parport_pc             31940  1 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
i2c_nforce2             6784  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  0 
usb_storage            52544  0 
floppy                 54916  0 
forcedeth              54152  0 
```


```

**At 22:23:00 I am manually disabling the network and re-enabling it to bring it back up. It connects successfully, but around 22:29:00 it disconnects on its own**

daemon.log
Nov  4 22:22:57 garrett-desktop NetworkManager: <info>  Sleeping...
Nov  4 22:22:57 garrett-desktop NetworkManager: <info>  (wlan0): now unmanaged
Nov  4 22:22:57 garrett-desktop NetworkManager: <info>  (wlan0): device state change: 2 -> 1 (reason 37)
Nov  4 22:22:57 garrett-desktop NetworkManager: <info>  (wlan0): cleaning up...
Nov  4 22:22:57 garrett-desktop NetworkManager: <info>  (eth0): now unmanaged
Nov  4 22:22:57 garrett-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 1 (reason 37)
Nov  4 22:22:57 garrett-desktop NetworkManager: <info>  (eth0): cleaning up...
Nov  4 22:22:57 garrett-desktop NetworkManager: <info>  (eth0): taking down device.
Nov  4 22:23:10 garrett-desktop NetworkManager: <info>  Waking up...
Nov  4 22:23:10 garrett-desktop NetworkManager: <info>  (wlan0): now managed
Nov  4 22:23:10 garrett-desktop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Nov  4 22:23:10 garrett-desktop NetworkManager: <info>  (wlan0): bringing up device.
Nov  4 22:23:10 garrett-desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Nov  4 22:23:10 garrett-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Nov  4 22:23:10 garrett-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Nov  4 22:23:10 garrett-desktop NetworkManager: <info>  (eth0): now managed
Nov  4 22:23:10 garrett-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Nov  4 22:23:10 garrett-desktop NetworkManager: <info>  (eth0): bringing up device.
Nov  4 22:23:10 garrett-desktop NetworkManager: <info>  (eth0): preparing device.
Nov  4 22:23:10 garrett-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Nov  4 22:23:16 garrett-desktop NetworkManager: <info>  (wlan0): bringing up device.
Nov  4 22:23:16 garrett-desktop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Nov  4 22:23:16 garrett-desktop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Nov  4 22:23:16 garrett-desktop wpa_supplicant[907]: Failed to initiate AP scan.
Nov  4 22:23:21 garrett-desktop wpa_supplicant[907]: CTRL-EVENT-SCAN-RESULTS 
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto 3280_2D'
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  (wlan0): preparing device.
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto 3280_2D' has security, but secrets are required.
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto 3280_2D' has security, and secrets exist.  No new secrets needed.
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  Config: added 'ssid' value '3280_2D'
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Nov  4 22:23:27 garrett-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov  4 22:23:27 garrett-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  Config: set interface ap_scan to 1
Nov  4 22:23:27 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Nov  4 22:23:28 garrett-desktop wpa_supplicant[907]: CTRL-EVENT-SCAN-RESULTS 
Nov  4 22:23:28 garrett-desktop wpa_supplicant[907]: Trying to associate with 00:14:6c:a2:50:b0 (SSID='3280_2D' freq=2417 MHz)
Nov  4 22:23:28 garrett-desktop wpa_supplicant[907]: Association request to the driver failed
Nov  4 22:23:28 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Nov  4 22:23:28 garrett-desktop wpa_supplicant[907]: Associated with 00:14:6c:a2:50:b0
Nov  4 22:23:28 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Nov  4 22:23:29 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Nov  4 22:23:29 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Nov  4 22:23:29 garrett-desktop wpa_supplicant[907]: WPA: Key negotiation completed with 00:14:6c:a2:50:b0 [PTK=TKIP GTK=TKIP]
Nov  4 22:23:29 garrett-desktop wpa_supplicant[907]: CTRL-EVENT-CONNECTED - Connection to 00:14:6c:a2:50:b0 completed (auth) [id=0 id_str=]
Nov  4 22:23:29 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Nov  4 22:23:29 garrett-desktop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '3280_2D'.
Nov  4 22:23:29 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov  4 22:23:29 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Nov  4 22:23:29 garrett-desktop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Nov  4 22:23:29 garrett-desktop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Nov  4 22:23:29 garrett-desktop NetworkManager: <info>  dhclient started with pid 2676
Nov  4 22:23:29 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Nov  4 22:23:29 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov  4 22:23:29 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Nov  4 22:23:29 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Nov  4 22:23:29 garrett-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.2
Nov  4 22:23:29 garrett-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov  4 22:23:29 garrett-desktop dhclient: All rights reserved.
Nov  4 22:23:29 garrett-desktop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov  4 22:23:29 garrett-desktop dhclient: 
Nov  4 22:23:29 garrett-desktop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Nov  4 22:23:29 garrett-desktop dhclient: Listening on LPF/wlan0/00:fd:07:92:db:d2
Nov  4 22:23:29 garrett-desktop dhclient: Sending on   LPF/wlan0/00:fd:07:92:db:d2
Nov  4 22:23:29 garrett-desktop dhclient: Sending on   Socket/fallback
Nov  4 22:23:29 garrett-desktop avahi-daemon[854]: Registering new address record for fe80::2fd:7ff:fe92:dbd2 on wlan0.*.
Nov  4 22:23:31 garrett-desktop dhclient: DHCPREQUEST of 192.168.1.3 on wlan0 to 255.255.255.255 port 67
Nov  4 22:23:32 garrett-desktop dhclient: DHCPACK of 192.168.1.3 from 192.168.1.1
Nov  4 22:23:32 garrett-desktop dhclient: bound to 192.168.1.3 -- renewal in 37393 seconds.
Nov  4 22:23:32 garrett-desktop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Nov  4 22:23:32 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Nov  4 22:23:32 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Nov  4 22:23:32 garrett-desktop NetworkManager: <info>    address 192.168.1.3
Nov  4 22:23:32 garrett-desktop NetworkManager: <info>    prefix 24 (255.255.255.0)
Nov  4 22:23:32 garrett-desktop NetworkManager: <info>    gateway 192.168.1.1
Nov  4 22:23:32 garrett-desktop NetworkManager: <info>    nameserver '192.168.1.1'
Nov  4 22:23:32 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Nov  4 22:23:32 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Nov  4 22:23:32 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Nov  4 22:23:32 garrett-desktop avahi-daemon[854]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.3.
Nov  4 22:23:32 garrett-desktop avahi-daemon[854]: New relevant interface wlan0.IPv4 for mDNS.
Nov  4 22:23:32 garrett-desktop avahi-daemon[854]: Registering new address record for 192.168.1.3 on wlan0.IPv4.
Nov  4 22:23:33 garrett-desktop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Nov  4 22:23:33 garrett-desktop NetworkManager: <info>  Policy set 'Auto 3280_2D' (wlan0) as default for routing and DNS.
Nov  4 22:23:33 garrett-desktop NetworkManager: <info>  Activation (wlan0) successful, device activated.
Nov  4 22:23:33 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Nov  4 22:23:34 garrett-desktop ntpdate[2729]: adjust time server 91.189.94.4 offset 0.014873 sec
Nov  4 22:23:38 garrett-desktop wpa_supplicant[907]: CTRL-EVENT-SCAN-RESULTS 
Nov  4 22:24:18 garrett-desktop wpa_supplicant[907]: CTRL-EVENT-SCAN-RESULTS 
Nov  4 22:25:18 garrett-desktop wpa_supplicant[907]: CTRL-EVENT-SCAN-RESULTS 
Nov  4 22:26:38 garrett-desktop wpa_supplicant[907]: CTRL-EVENT-SCAN-RESULTS 
Nov  4 22:27:18 garrett-desktop wpa_supplicant[907]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov  4 22:27:18 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Nov  4 22:27:18 garrett-desktop wpa_supplicant[907]: Associated with 00:14:6c:a2:50:b0
Nov  4 22:27:18 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associated
Nov  4 22:27:19 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Nov  4 22:27:19 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Nov  4 22:27:19 garrett-desktop wpa_supplicant[907]: WPA: Key negotiation completed with 00:14:6c:a2:50:b0 [PTK=TKIP GTK=TKIP]
Nov  4 22:27:19 garrett-desktop wpa_supplicant[907]: CTRL-EVENT-CONNECTED - Connection to 00:14:6c:a2:50:b0 completed (reauth) [id=0 id_str=]
Nov  4 22:27:19 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Nov  4 22:28:18 garrett-desktop wpa_supplicant[907]: CTRL-EVENT-SCAN-RESULTS 
Nov  4 22:29:22 garrett-desktop wpa_supplicant[907]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov  4 22:29:22 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Nov  4 22:29:22 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov  4 22:29:23 garrett-desktop wpa_supplicant[907]: Associated with 00:14:6c:a2:50:b0
Nov  4 22:29:23 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associated
Nov  4 22:29:24 garrett-desktop wpa_supplicant[907]: CTRL-EVENT-SCAN-RESULTS 
Nov  4 22:29:33 garrett-desktop wpa_supplicant[907]: Authentication with 00:14:6c:a2:50:b0 timed out.
Nov  4 22:29:33 garrett-desktop wpa_supplicant[907]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov  4 22:29:33 garrett-desktop wpa_supplicant[907]: Failed to initiate AP scan.
Nov  4 22:29:33 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Nov  4 22:29:33 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 11)
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 11).
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2676
Nov  4 22:29:38 garrett-desktop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto 3280_2D'
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto 3280_2D' has security, but secrets are required.
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Nov  4 22:29:38 garrett-desktop avahi-daemon[854]: Withdrawing address record for 192.168.1.3 on wlan0.
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  4 22:29:38 garrett-desktop avahi-daemon[854]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.3.
Nov  4 22:29:38 garrett-desktop avahi-daemon[854]: Interface wlan0.IPv4 no longer relevant for mDNS.
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto 3280_2D' has security, and secrets exist.  No new secrets needed.
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  Config: added 'ssid' value '3280_2D'
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Nov  4 22:29:38 garrett-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov  4 22:29:38 garrett-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  4 22:29:38 garrett-desktop NetworkManager: <info>  Config: set interface ap_scan to 1
Nov  4 22:29:43 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov  4 22:29:44 garrett-desktop wpa_supplicant[907]: CTRL-EVENT-SCAN-RESULTS 
Nov  4 22:29:44 garrett-desktop wpa_supplicant[907]: Trying to associate with 00:14:6c:a2:50:b0 (SSID='3280_2D' freq=2417 MHz)
Nov  4 22:29:44 garrett-desktop wpa_supplicant[907]: Association request to the driver failed
Nov  4 22:29:44 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Nov  4 22:29:45 garrett-desktop wpa_supplicant[907]: Associated with 00:14:6c:a2:50:b0
Nov  4 22:29:45 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Nov  4 22:29:45 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Nov  4 22:29:45 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Nov  4 22:29:45 garrett-desktop wpa_supplicant[907]: WPA: Key negotiation completed with 00:14:6c:a2:50:b0 [PTK=TKIP GTK=TKIP]
Nov  4 22:29:45 garrett-desktop wpa_supplicant[907]: CTRL-EVENT-CONNECTED - Connection to 00:14:6c:a2:50:b0 completed (reauth) [id=0 id_str=]
Nov  4 22:29:45 garrett-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Nov  4 22:29:45 garrett-desktop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '3280_2D'.
Nov  4 22:29:45 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov  4 22:29:45 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Nov  4 22:29:45 garrett-desktop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Nov  4 22:29:45 garrett-desktop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Nov  4 22:29:45 garrett-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.2
Nov  4 22:29:45 garrett-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov  4 22:29:45 garrett-desktop dhclient: All rights reserved.
Nov  4 22:29:45 garrett-desktop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov  4 22:29:45 garrett-desktop dhclient: 
Nov  4 22:29:45 garrett-desktop NetworkManager: <info>  dhclient started with pid 2784
Nov  4 22:29:45 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Nov  4 22:29:45 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov  4 22:29:45 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Nov  4 22:29:45 garrett-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Nov  4 22:29:45 garrett-desktop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Nov  4 22:29:45 garrett-desktop dhclient: Listening on LPF/wlan0/00:fd:07:92:db:d2
Nov  4 22:29:45 garrett-desktop dhclient: Sending on   LPF/wlan0/00:fd:07:92:db:d2
Nov  4 22:29:45 garrett-desktop dhclient: Sending on   Socket/fallback
Nov  4 22:29:47 garrett-desktop dhclient: DHCPREQUEST of 192.168.1.3 on wlan0 to 255.255.255.255 port 67
Nov  4 22:29:52 garrett-desktop dhclient: DHCPREQUEST of 192.168.1.3 on wlan0 to 255.255.255.255 port 67
Nov  4 22:30:05 garrett-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Nov  4 22:30:11 garrett-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Nov  4 22:30:14 garrett-desktop NetworkManager: <info>  (wlan0): device state change: 7 -> 2 (reason 0)
Nov  4 22:30:14 garrett-desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Nov  4 22:30:14 garrett-desktop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2784
Nov  4 22:30:14 garrett-desktop NetworkManager: <info>  (wlan0): taking down device.
Nov  4 22:30:14 garrett-desktop avahi-daemon[854]: Withdrawing address record for fe80::2fd:7ff:fe92:dbd2 on wlan0.
Nov  4 22:30:15 garrett-desktop NetworkManager: <info>  Sleeping...
Nov  4 22:30:15 garrett-desktop NetworkManager: <info>  (wlan0): now unmanaged
Nov  4 22:30:15 garrett-desktop NetworkManager: <info>  (wlan0): device state change: 2 -> 1 (reason 37)
Nov  4 22:30:15 garrett-desktop NetworkManager: <info>  (wlan0): cleaning up...
Nov  4 22:30:15 garrett-desktop NetworkManager: <info>  (eth0): now unmanaged
Nov  4 22:30:15 garrett-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 1 (reason 37)
Nov  4 22:30:15 garrett-desktop NetworkManager: <info>  (eth0): cleaning up...
Nov  4 22:30:15 garrett-desktop NetworkManager: <info>  (eth0): taking down device.
```



All help is very appreciated.

---

### Post by papangul on 2009-11-04
> **GarrettFoster said:**
> I am going to piggy-back on this thread as my card is also a RT2561 ...
I have exactly the same card and it's mostly doing fine in karmic.
I have the wicd network manager installed instead of network manager.
See this thread, although it is for jaunty, still the instructions are relevant:
[http://ubuntuforums.org/showthread.php?t=1150797](http://ubuntuforums.org/showthread.php?t=1150797)

---

### Post by GarrettFoster on 2009-11-05
> **papangul said:**
> I have exactly the same card and it's mostly doing fine in karmic.
I have the wicd network manager installed instead of network manager.
See this thread, although it is for jaunty, still the instructions are relevant:
[http://ubuntuforums.org/showthread.php?t=1150797](http://ubuntuforums.org/showthread.php?t=1150797)

I read about wicd earlier in some other threads as a possible work around. I would prefer it if Network-Manager worked out of the box, but I suppose I will give wicd a try and see if it is more stable. For reference I just opened synaptic and searched for wicd and installed it from there. Way easier if you can manage to get your internet working for a few minutes. :D

---

### Post by GarrettFoster on 2009-11-06
Just following up after a day of testing. Wicd has seemed much more stable. 

I would still like the default wireless to work, so I am willing to re-install Network Manager and report what it does if someone is interested in fixing it.

---

