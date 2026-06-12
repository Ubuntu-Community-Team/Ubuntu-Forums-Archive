---
title: "Wireless suddenly not working 12.04 on Lenovo ThinkPad W520"
date: 2013-06-20
forum: Networking &amp; Wireless
---

### Post by Eric N Wilson on 2013-06-20
I've been using a Lenovo ThinkPad W520 for two years with Ubuntu, and with 12.04 for over a year. Recently my wireless stopped working.

My network is fine, other computers can connect to it without problems.

I tried using a USB wifi adapter, one that works on another Ubuntu 12.04 laptop (a very old Dell that can no longer receive wireless) and that doesn't help. It just keeps looking and looking, but never connecting to the network.

I was curious if upgrading Ubuntu would help. Due to a graphics incompatability, that upgrade failed, and I was forced to re-install Ubuntu 12.04. Surprisingly, after the re-install, the wireless worked again, for a few days. But now I'm back to no wireless.

I would appreciate troubleshooting help. What should I try?

---

### Post by varunendra on 2013-06-20
Welcome to the forums Eric !

Please run the following commands in a terminal (Ctrl + Alt + T) and post back their outputs to show us what card and drivers you have :
```
lspci -nnk | grep -iA2 net
```

Also, plug in the USB adapter and post back -
```
lsusb
```
We can try to troubleshoot whichever is easier.

Additionally, also show us the outputs of -
```
rfkill list
nm-tool
```

While posting the outputs, please use code tags (follow the link in my signature to see an example) to preserve the formatting. Thanks !

---

### Post by Eric N Wilson on 2013-06-20
Thanks much for the quick reply. Here is the requested information:

```

eric@ewilson:~$ lspci -nnk | grep -iA2 net00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Lenovo Device [17aa:21ce]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
	Kernel driver in use: rtl8192ce

```

```

eric@ewilson:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 005: ID 0a5c:217f Broadcom Corp. Bluetooth Controller
Bus 001 Device 004: ID 04f2:b217 Chicony Electronics Co., Ltd 
Bus 003 Device 004: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter

```

```

eric@ewilson:~$ rfkill list


1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
19: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
20: phy2: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

```

```

eric@ewilson:~$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             unavailable
  Default:           no
  HW Address:        00:E0:4C:32:C5:85


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             unavailable
  Default:           no
  HW Address:        EC:55:F9:C1:F8:DF


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 




- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        F0:DE:F1:60:0F:9C


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.69
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1
    DNS:             184.16.33.54

```

---

### Post by varunendra on 2013-06-20
> **Eric N Wilson said:**
> 
```

eric@ewilson:~$ rfkill list
2: phy0: Wireless LAN
	**Soft blocked: [COLOR="#FF0000"]yes[/COLOR]**
	Hard blocked: no
19: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
20: phy2: Wireless LAN
	**Soft blocked: [COLOR="#FF0000"]yes[/COLOR]**
	Hard blocked: no

```
In the outputs above, the wireless seems to be "Soft Blocked". Means - it is turned off by software switch. Make sure the "Enable Wireless" option has a tick-mark in Network manager's drop-down list (the network icon on the top-right corner). If it is already ticked, try -
```
sudo rfkill unblock all
```

Also, disconnect the cable while doing this, as Network Manager prefers wired connection over wireless (assuming wired is fast).

When done, run the "rfkill list" command again and make sure that Wireless interface doesn't show up as "Soft blocked : yes". If it appears unblocked, and still you are unable to connect, follow the "Wireless Script" link in my signature and post back the diagnostics report as the linked post asks to do. Run the script when the cable is disconnected, and you are trying to connect wirelessly.

The driver you are using for the internal adapter has been problematic for some users recently. We may need to install proprietary driver for it if native one doesn't work.

For now, we are only focusing on the internal card, although the usb one should also work smoothly.

---

### Post by Eric N Wilson on 2013-06-20
Sorry about having wireless disabled while running `rfkill list`. I've enabled it, and it shows `Soft blocked: no`, and I can still not connect.

Here are the results of the script:

```



*************** info trace ***************


***** uname -a *****


Linux ewilson 3.2.0-48-generic-pae #74-Ubuntu SMP Thu Jun 6 20:05:01 UTC 2013 i686 i686 i386 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise


***** lspci *****


00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Lenovo Device [17aa:21ce]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
	Kernel driver in use: rtl8192ce


***** lsusb *****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 005: ID 0a5c:217f Broadcom Corp. Bluetooth Controller
Bus 001 Device 004: ID 04f2:b217 Chicony Electronics Co., Ltd 


***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:"Wilson"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




***** rfkill *****


1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
22: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


***** lsmod *****


rt2800usb              22373  0 
rt2800lib              53298  1 rt2800usb
crc_ccitt              12627  1 rt2800lib
rt2x00usb              20099  1 rt2800usb
rt2x00lib              48875  3 rt2800usb,rt2800lib,rt2x00usb
rtl8192ce              75529  0 
rtl8192c_common        69519  1 rtl8192ce
rtlwifi                95855  1 rtl8192ce
mac80211              436493  6 rt2800lib,rt2x00usb,rt2x00lib,rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              178877  3 rt2x00lib,rtlwifi,mac80211


***** nm-tool *****


NetworkManager Tool


State: connecting


- Device: wlan0  [Wilson] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    belkin54g:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 97 WPA WPA2
    NETGEAR84:       Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 97 WPA2
    Sammy2:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 94 WPA2
    Wilson:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 97 WEP




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


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


auto lo
iface lo inet loopback




***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"Wilson"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001c7791868aa
                    Extra: Last beacon: 364ms ago
                    IE: Unknown: 000657696C736F6E
                    IE: Unknown: 010882848B96A4B0C8EC
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32048C9298E0
                    IE: Unknown: DD090010180202F0000000
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"belkin54g"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000db65696586
                    Extra: Last beacon: 748ms ago
                    IE: Unknown: 000962656C6B696E353467
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD970050F204104A0001101044000102103B00010210470010E7FE1B918CD5031098DD002275566B4C1021000642656C6B696E1023000F463544373233342D342D763130303010240007575053303030311042000E32303931313732333431363537301054000800060050F204000110110020463544373233342D34000000000000000000000000000000000000000000000010080002008C
                    IE: Unknown: DD090010180202F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR84"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000075f23dad40
                    Extra: Last beacon: 360ms ago
                    IE: Unknown: 00094E4554474541523834
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030108
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1608080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A0001101044000102103B00010310470010E53933613506EAA85517A1DBAA5F4BC11021000D4E4554474541522C20496E632E1023000A574E44523334303076321024000A574E44523334303076321042000230311054000800060050F20400011011000A574E4452333430307632100800020004103C000103
                    IE: Unknown: DD090010180200F0040000
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


[45116.724871] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[45116.771961] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[45119.729724] wlan0: authenticate with <MAC address removed> (try 1)
[45119.732219] wlan0: authenticated
[45119.732691] wlan0: associate with <MAC address removed> (try 1)
[45119.735524] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[45119.735532] wlan0: associated
[45119.736607] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[45130.389327] wlan0: no IPv6 routers present
[45137.957261] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[45150.738113] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[45745.963460] rtl8192ce 0000:03:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x107)
[45745.963486] rtl8192ce 0000:03:00.0: restoring config space at offset 0x6 (was 0x4, writing 0xf3a00004)
[45745.963494] rtl8192ce 0000:03:00.0: restoring config space at offset 0x4 (was 0x1, writing 0x5001)
[45745.963500] rtl8192ce 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[45745.963508] rtl8192ce 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[45745.964126] rtlwifi: wireless switch is on
[45936.032471] Registered led device: rt2800usb-phy2::radio
[45936.032504] Registered led device: rt2800usb-phy2::assoc
[45936.032528] Registered led device: rt2800usb-phy2::quality
[45936.045342] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[46297.930875] rtl8192ce 0000:03:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x107)
[46297.930900] rtl8192ce 0000:03:00.0: restoring config space at offset 0x6 (was 0x4, writing 0xf3a00004)
[46297.930908] rtl8192ce 0000:03:00.0: restoring config space at offset 0x4 (was 0x1, writing 0x5001)
[46297.930914] rtl8192ce 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[46297.930923] rtl8192ce 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[46297.931698] rtlwifi: wireless switch is on
[46298.589608] rt2800usb 3-1:1.0: no reset_resume for driver rt2800usb?
[46299.061449] Registered led device: rt2800usb-phy3::radio
[46299.061463] Registered led device: rt2800usb-phy3::assoc
[46299.061477] Registered led device: rt2800usb-phy3::quality
[46299.709261] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[46478.927327] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[46479.265621] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[46479.887657] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[46479.930467] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[46482.885620] wlan0: authenticate with <MAC address removed> (try 1)
[46482.890369] wlan0: authenticated
[46482.890505] wlan0: associate with <MAC address removed> (try 1)
[46482.894573] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[46482.894576] wlan0: associated
[46482.895044] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[46493.533047] wlan0: no IPv6 routers present
[46528.784703] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[46530.578219] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[46532.656830] wlan0: authenticate with <MAC address removed> (try 1)
[46532.660973] wlan0: authenticated
[46532.661350] wlan0: associate with <MAC address removed> (try 1)
[46532.664886] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[46532.664895] wlan0: associated
[46543.572313] wlan0: no IPv6 routers present
[46577.722489] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[46580.519569] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[46581.713602] wlan0: authenticate with <MAC address removed> (try 1)
[46581.735110] wlan0: authenticated
[46581.735511] wlan0: associate with <MAC address removed> (try 1)
[46581.738759] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[46581.738768] wlan0: associated
[46591.813970] wlan0: no IPv6 routers present
[46626.656716] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[46629.463835] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[46630.658202] wlan0: authenticate with <MAC address removed> (try 1)
[46630.660993] wlan0: authenticated
[46630.663960] wlan0: associate with <MAC address removed> (try 1)
[46630.669238] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[46630.669251] wlan0: associated
[46641.102245] wlan0: no IPv6 routers present
[46675.590769] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[46680.392329] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[46720.335595] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[46770.273946] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[46830.193632] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[46890.118290] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[46950.038530] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[46976.016711] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[46977.210182] wlan0: authenticate with <MAC address removed> (try 1)
[46977.216964] wlan0: authenticated
[46977.217103] wlan0: associate with <MAC address removed> (try 1)
[46977.220763] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[46977.220773] wlan0: associated
[46987.550291] wlan0: no IPv6 routers present
[47022.146070] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[47024.955394] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[47026.150710] wlan0: authenticate with <MAC address removed> (try 1)
[47026.162461] wlan0: authenticated
[47026.162773] wlan0: associate with <MAC address removed> (try 1)
[47026.178827] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[47026.178837] wlan0: associated
[47036.223346] wlan0: no IPv6 routers present
[47072.080912] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[47074.890114] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[47076.082278] wlan0: authenticate with <MAC address removed> (try 1)
[47076.086498] wlan0: authenticated
[47076.087077] wlan0: associate with <MAC address removed> (try 1)
[47076.095793] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[47076.095805] wlan0: associated
[47086.989713] wlan0: no IPv6 routers present
[47121.017215] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[47123.824794] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[47125.019068] wlan0: authenticate with <MAC address removed> (try 1)
[47125.021757] wlan0: authenticated
[47125.025138] wlan0: associate with <MAC address removed> (try 1)
[47125.028368] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[47125.028379] wlan0: associated
[47135.998344] wlan0: no IPv6 routers present
[47169.955144] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[47189.731500] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[47249.653535] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[47309.581496] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[47369.501093] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[47429.425741] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[47470.386246] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[47471.586533] wlan0: authenticate with <MAC address removed> (try 1)
[47471.590210] wlan0: authenticated
[47471.590480] wlan0: associate with <MAC address removed> (try 1)
[47471.596773] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[47471.596783] wlan0: associated
[47481.638893] wlan0: no IPv6 routers present
[47516.517407] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[47519.311703] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[47520.503174] wlan0: authenticate with <MAC address removed> (try 1)
[47520.507873] wlan0: authenticated
[47520.508288] wlan0: associate with <MAC address removed> (try 1)
[47520.513755] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[47520.513758] wlan0: associated
[47531.222776] wlan0: no IPv6 routers present


****************** done ******************

```

---

### Post by varunendra on 2013-06-20
> **Eric N Wilson said:**
> 
```

  Wireless Access Points 
    Wilson:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 97 **[COLOR="#FF0000"]WEP[/COLOR]**
...
...
wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (**Channel [COLOR="#FF0000"]6[/COLOR]**)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"Wilson"

```

A couple of more suggestions before we try something else.

[LIST]
[*]Are you using WEP encryption in the router? If yes, try changing it to pure WPA2-PSK (AES).
[*]Try changing the channel to 1 or 11 instead of 6.
[/LIST]
If these don't help, we are going to compile the proprietary driver.

---

### Post by Eric N Wilson on 2013-06-20
I changed the channel to 1, but I wasn't able to figure out how to change to WPA2-PSK (AES). So I disabled WEP, to see if that changed anything.

It didn't help, still no wireless connection.

---

### Post by DestructiveLabs on 2013-06-20
Have you tried manually configuring the connection settings under: Network Manager -> Edit Connections -> Wireless -> Wilson -> IPv4 tab ?

Sometimes changing the method from 'Automatic DHCP' to 'Manual' and configuring as per your network settings will allow you to connect.

i.e. : under "Addresses" on the IPv4 tab:
click :'ADD'
then give yourself a static IP ( usually 192.168.1.X)
netmask (255.255.255.0)
gateway (192.168.1.1)
DNS server : (192.168.1.1)
then 'Save'
and try to connect.
Those settings are general and may be different on your network but they are pretty standard.

I had to do this after installing DDWRT on my router for the first few days. Now I can use the automatic settings again. Not sure why the change but hey, technology can be quirky.

---

### Post by varunendra on 2013-06-21
> **Eric N Wilson said:**
> It didn't help, still no wireless connection.

You may try what DestructiveLabs suggested above (his idea isn't that much "Destructive", it actually helps sometimes ;)).

Alternately, let's just compile the proprietary driver.

[INDENT]**1)** Connect to internet via cable.

**2)** Download the RTL8188CE driver from Realtek's official site : [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2722](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2722)

**3)** Copy the downloaded file to your desktop > right-click > "Extract here". It will extract the files into a folder named "rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013".

**4)** Open the terminal and run the following commands (one command at a time > let it finish > next command) :
*(Tip : just type a few initial characters, then press "Tab" key to auto-complete path/filenames)*
```
sudo apt-get install build-essential linux-headers-generic
cd ~/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013
make
sudo make install
```
Watch out for errors, post back if there are any.[/INDENT]

If successful, you should have a working wireless after this.

---

### Post by Eric N Wilson on 2013-06-21
Thanks much, the new driver did the trick.

---

