---
title: "Broadcom wireless stopped working in Lucid"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by bauerber on 2010-05-05
Hi there,

after having tried out almost all suggestions found here and elsewhere on the internet, i'm somewhat at my wits end :-(
The situation:
I'm running Kubuntu 32Bit Version (at the mom 10.4) on a HP-Compaq 6735s (AMD Processor, Vanilla 32Bit Install). 
My first Install was last year with 9.4 and the Broadcom 4322 wireless worked like a charm after installing the proprietary STA-driver under System -> Hardware Drivers.
As the update didn't work out really without glitches, i did a fresh install and lost my wireless.
I tried various combinations and tutorials but to no avail. My card is found, the driver installed, but i cannot access my access-point.
I can SEE the access point (and all my neighbors'), but knetworkmanager does not seem to do anything.
To be sure, I installed wicd (nice tool by the way). Trying a connect here told my my credentials were bad (incorrect passphrase for my WPA2 Personal auth), which is not true.
I tried connecting without security, didn't get an IP.
So it seems somehow the card is working, but all functions needed for passing information to the access-point are unavailable.

This is what I tried:
both broadcom-drivers
fw-cutter
installing the driver by hand

Installing the driver via Hardware Drivers produced the same results as any other, viz the card is working, but not connecting.
Unfortunately knetworkmanagers error messages are a bit sparse, or rather non existant.
My guess is that somehow the firmware is not properly loaded (or the wrong type??).
Any pointers anybody?

Thanks

Bernhard

---

### Post by pdc on 2010-05-05
[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English)

this a diagnostic script that is used on OpenSuse but analyses any wireless;

run it; it is safe; it will analyse and suggest solutions; you can post the whole analysis back here for folks to review

---

### Post by bauerber on 2010-05-05
Thanks pdc,

will try that as soon as I get home!

---

### Post by bauerber on 2010-05-05
So. Came home, updated to new Kernel (2.6.32-22) and let the script you suggested run.
Heres the output, unfortunately no error messages :-(

```

==================================================================================================================
==================================================================================================================
*** uname -a
Linux mobi 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
==================================================================================================================
*** cat /etc/*[-_]release || cat /etc/*[-_]version
/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
==================================================================================================================
*** cat /etc/resolv | grep -i "nameserver"
==================================================================================================================
*** cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    mobi
==================================================================================================================
*** route -n
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
==================================================================================================================
*** ifconfig
eth0      Link encap:Ethernet  Hardware Adresse ##:##:##:##:##:#1  
          inet6-Adresse: fe80::224:81ff:fe5f:90da/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:700 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:506008 (506.0 KB)  TX bytes:149478 (149.4 KB)
          Interrupt:16 
eth1      Link encap:Ethernet  Hardware Adresse ##:##:##:##:##:#2  
          inet6-Adresse: fe80::221:ff:fec3:c6d9/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:144
          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 
lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:4496 (4.4 KB)  TX bytes:4496 (4.4 KB)
==================================================================================================================
*** ping tests
connect: Network is unreachable
Ping of 195.135.220.3 failed
ping: unknown host www.suse.de
Ping of www.suse.de failed
==================================================================================================================
*** lspci
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:4357] (rev 10)
06:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
==================================================================================================================
*** lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c050 Logitech, Inc. RX 250 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b083 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
==================================================================================================================
*** lsmod # (filtered)
| agpgart         | ahci            | bitblit         | bluetooth       | bnep             |
| bridge          | btusb           | fbcon           | fglrx           | font             |
| hid             | hp_accel        | i2c_piix4       | input_polldev   | l2cap            |
| led_class       | lib80211        | lib80211_crypt_tkip| lis3lv02d       | lp               |
| output          | ppdev           | rfcomm          | sco             | serio_raw        |
| shpchp          | sky2            | snd_hda_codec   | snd_hda_codec_analog| snd_hda_intel    |
| snd_hwdep       | snd_rawmidi     | snd_seq_device  | snd_seq_dummy   | snd_seq_midi     |
| snd_seq_oss     | softcursor      | stp             | tileblit        | uvcvideo         |
| v4l1_compat     | vga16fb         | vgastate        | video           | wl               |
==================================================================================================================
*** cat /etc/network/interfaces
--- /etc/network/interfaces
auto lo
iface lo inet loopback
==================================================================================================================
*** iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.
eth1      IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:5.58 GHz  Access Point: Not-Associated   
          Bit Rate:44 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
==================================================================================================================
*** Actual date for bias of following greps
20:03:23 2010-05-05
==================================================================================================================
*** grep -i radio /var/log/messages* | tail -n 5
==================================================================================================================
*** dmesg | grep -i radio | tail -n 5
==================================================================================================================
*** tail -n 300 /var/log/messages* | /bin/grep -i firmware | tail -n 5
==================================================================================================================
*** ls /lib/firmware/*
| 2.6.32-21-generic       | 2.6.32-22-generic       | 3com                    | acenic                   |
| adaptec                 | advansys                | agere_ap_fw.bin         | agere_sta_fw.bin         |
| aic94xx-seq.fw          | ar9170-1.fw             | ar9170-2.fw             | ar9170.fw                |
| ath3k-1.fw              | atmel_at76c502_3com.bin | atmel_at76c502.bin      | atmel_at76c502d.bin      |
| atmel_at76c502e.bin     | atmel_at76c504_2958.bin | atmel_at76c504a_2958.bin| atmel_at76c504.bin       |
| atmel_at76c506.bin      | atmsar11.fw             | av7110                  | b43                      |
| b43legacy               | bnx2                    | bnx2x-e1-4.8.53.0.fw    | bnx2x-e1-5.2.7.0.fw      |
| bnx2x-e1h-4.8.53.0.fw   | bnx2x-e1h-5.2.7.0.fw    | cis                     | cpia2                    |
| cxgb3                   | dabusb                  | dsp56k                  | dvb-fe-xc5000-1.6.114.fw |
| dvb-usb-dib0700-1.20.fw | e100                    | ea                      | edgeport                 |
| emi26                   | emi62                   | ess                     | i2400m-fw-usb-1.3.sbcf   |
| i2400m-fw-usb-1.4.sbcf  | intelliport2.bin        | ipw2100-1.3.fw          | ipw2100-1.3-i.fw         |
| ipw2100-1.3-p.fw        | ipw2200-bss.fw          | ipw2200-ibss.fw         | ipw2200-sniffer.fw       |
| iwlwifi-1000-3.ucode    | iwlwifi-3945-2.ucode    | iwlwifi-4965-2.ucode    | iwlwifi-5000-1.ucode     |
| iwlwifi-5000-2.ucode    | iwlwifi-5150-2.ucode    | iwlwifi-6000-4.ucode    | kaweth                   |
| keyspan                 | keyspan_pda             | korg                    | libertas                 |
| matrox                  | mts_cdma.fw             | mts_edge.fw             | mts_gsm.fw               |
| mwl8k                   | myricom                 | NPE-B                   | NPE-C                    |
| ositech                 | ql2100_fw.bin           | ql2200_fw.bin           | ql2300_fw.bin            |
| ql2322_fw.bin           | ql2400_fw.bin           | ql2500_fw.bin           | qlogic                   |
| r128                    | radeon                  | rt2561.bin              | rt2561s.bin              |
| rt2661.bin              | rt2860.bin              | rt2870.bin              | rt73.bin                 |
| RTL8192SE               | sb16                    | scripts                 | slicoss                  |
| sun                     | sxg                     | tehuti                  | ti_3410.fw               |
| ti_5052.fw              | tigon                   | tr_smctr.bin            | ttusb-budget             |
| usbdux                  | usbduxfast_firmware.bin | usbdux_firmware.bin     | v4l-cx231xx-avcore-01.fw |
| v4l-cx23418-apu.fw      | v4l-cx23418-cpu.fw      | v4l-cx23418-dig.fw      | v4l-cx2341x-dec.fw       |
| v4l-cx2341x-enc.fw      | v4l-cx2341x-init.mpg    | v4l-cx23885-avcore-01.fw| v4l-cx23885-enc.fw       |
| v4l-cx25840.fw          | v4l-pvrusb2-24xxx-01.fw | v4l-pvrusb2-29xxx-01.fw | vicam                    |
| whiteheat.fw            | whiteheat_loader.fw     | yam                     | yamaha                   |
| zd1201-ap.fw            | zd1201.fw               | zd1211                  |
--- /lib/firmware
| a0g0bsinitvals5.fw      | a0g0bsinitvals9.fw      | a0g0initvals5.fw        | a0g0initvals9.fw         |
| a0g1bsinitvals13.fw     | a0g1bsinitvals5.fw      | a0g1bsinitvals9.fw      | a0g1initvals13.fw        |
| a0g1initvals5.fw        | a0g1initvals9.fw        | b0g0bsinitvals13.fw     | b0g0bsinitvals5.fw       |
| b0g0bsinitvals9.fw      | b0g0initvals13.fw       | b0g0initvals5.fw        | b0g0initvals9.fw         |
| lp0bsinitvals13.fw      | lp0bsinitvals14.fw      | lp0bsinitvals15.fw      | lp0initvals13.fw         |
| lp0initvals14.fw        | lp0initvals15.fw        | n0absinitvals11.fw      | n0bsinitvals11.fw        |
| n0initvals11.fw         | pcm5.fw                 | ucode11.fw              | ucode13.fw               |
| ucode14.fw              | ucode15.fw              | ucode5.fw               | ucode9.fw                |
==================================================================================================================
*** ndiswrapper -l
No ndiswrapper module loaded
==================================================================================================================
*** Active processes
wpa_supplicant:YES knetworkmanager:YES nm-applet:NO
==================================================================================================================
*** grep 'eth|ath|wlan|ra' /etc/udev/rules.d/*net_persistent* /etc/udev/rules.d/*persistent-net*
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
==================================================================================================================
*** grep -r 'eth[0-10]|ath[0-10]|wlan[0-10]|ra[0-10]' /etc/modprobe.*
==================================================================================================================
*** iwlist scanning
eth1      Failed to read scan data : Invalid argument

No WLANs found
==================================================================================================================
*** NWElizaStates
IF:eth0 IM:1 IF:eth1 IM:2 DI:2 AP:0 FALON:1 NIC:1 cNiC:2:1 NI:1 cNI:1 NDIS:0 IP6:0 WLW:0 RTDT:debian 


```

strange. After updating i am no longer offered the broadcom-sta driver. installed the driver manually via the broadcom sources.
well, doesn't seem i got any closer ...
or do you see what's wrong?

---

### Post by nukedathlonman on 2010-05-05
Can you check your syslog - look to see if you see a message: "Association request to the driver failed" in it.  If so, I've been hacking at tryign to find the source of the problem for days and started the following bug on Launchpad: [https://bugs.launchpad.net/ubuntu/+bug/572777](https://bugs.launchpad.net/ubuntu/+bug/572777)

---

### Post by bauerber on 2010-05-06
Ok nukedathlonman, will do. 
Will take some time though ;-)

---

### Post by bauerber on 2010-05-06
@nukedathlonman
Well, no luck. The snippet you mentioned cannot be found, but (obviously depending on the type of driver I used) a couple of entries similar to the following can be found in syslog.


```

May  5 19:53:08 mobi NetworkManager: <WARN>  user_connection_get_settings_cb(): user_connection_get_settings_cb: Invalid connection: 'NMSettingWireless' / 'mac-address' invalid: 1
May  5 19:53:08 mobi NetworkManager: <WARN>  user_connection_get_settings_cb(): user_connection_get_settings_cb: Invalid connection: 'NMSettingWireless' / 'mac-address' invalid: 1
May  5 19:53:36 mobi bluetoothd[1014]: Discovery session 0x203974e8 with :1.35 activated
May  5 20:00:46 mobi kernel: [  648.619431] lib80211: common routines for IEEE802.11 drivers
May  5 20:00:46 mobi kernel: [  648.619445] lib80211_crypt: registered algorithm 'NULL'
May  5 20:01:00 mobi kernel: [  663.453375] wl 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May  5 20:01:00 mobi kernel: [  663.453385] wl 0000:06:00.0: setting latency timer to 64
May  5 20:01:00 mobi kernel: [  663.479815] lib80211_crypt: registered algorithm 'TKIP'
May  5 20:01:00 mobi kernel: [  663.480051] eth1: Broadcom BCM432b 802.11 Hybrid Wireless Controller 5.60.48.36 
May  5 20:01:00 mobi NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:09.0/0000:06:00.0/net/eth1, iface: eth1)
May  5 20:01:00 mobi NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:09.0/0000:06:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
May  5 20:01:00 mobi NetworkManager: <info>  (eth1): driver supports SSID scans (scan_capa 0x01).
May  5 20:01:00 mobi NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'wl')
May  5 20:01:00 mobi NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 20:01:00 mobi NetworkManager: <info>  (eth1): now managed
May  5 20:01:00 mobi NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
May  5 20:01:00 mobi NetworkManager: <info>  (eth1): bringing up device.
May  5 20:01:01 mobi NetworkManager: <info>  (eth1): preparing device.
May  5 20:01:01 mobi NetworkManager: <info>  (eth1): deactivating device (reason: 2).
May  5 20:01:01 mobi NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready
May  5 20:01:01 mobi NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 42)
May  5 20:01:02 mobi avahi-daemon[891]: Registering new address record for fe80::221:ff:fec3:c6d9 on eth1.*.
May  5 20:01:06 mobi wpa_supplicant[917]: WPS-AP-AVAILABLE 
May  5 20:01:11 mobi kernel: [  673.964035] eth1: no IPv6 routers present
May  5 20:01:16 mobi NetworkManager: <WARN>  wait_for_connection_expired(): Connection (2) /org/freedesktop/NetworkManagerSettings/0 failed to activate (timeout): (0) Connection was not provided by any settings service
May  5 20:01:26 mobi wpa_supplicant[917]: WPS-AP-AVAILABLE 
May  5 20:01:56 mobi wpa_supplicant[917]: WPS-AP-AVAILABLE 
May  5 20:02:36 mobi wpa_supplicant[917]: WPS-AP-AVAILABLE 


```

Interesting parts seem to be the device state changes (1->2 with reason 2), which preceeds the deactivation.

Does anybody know, where I can look up thoese state-changes and their reasons??

---

### Post by zaleksf on 2010-05-06
I have a similar problem.

I had been running Ubuntu 9.10 64-bit very successfully on my Dell 1420 laptop with a Broadcom 4328 wireless card and the proprietary drivers (v5.60.48.36). All was well - I could login to any wireless network that my system could detect at I could provide access info to.

I performed a clean install of Ubuntu 10.04 64-bit to this very same system. Everything works well except that I cannot log in to wireless systems that require a password. I can connect by hard-wire and I can connect to 'open' systems that do not require a password to get onto the wireless network.

I used a script to check my system (attached - the one recommended above didn't work for me). I ran this script while logged on to an 'open' wireless system. Any help you could offer would be greatly appreciated. The results are shown below:

-----------------------------------------------------------------------
zaleksf@name-b2crhh1:~$ sh check-wireless.sh
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 03
       serial: 00:23:4d:13:12:7e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=67.194.2.37 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f9ffc000-f9ffffff memory:f0000000-f00fffff(prefetchable)
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:fc:d8:0c
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:f9bf0000-f9bfffff
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 06:0B:0A:13:12:7E
                    ESSID:""
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:2/5  Signal level:-74 dBm  Noise level:-90 dBm
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 02 - Address: 06:0B:0A:7B:E4:79
                    ESSID:""
                    Mode:Managed
                    Frequency=2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-87 dBm  Noise level:-90 dBm
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 03 - Address: 0A:0B:0A:13:12:7E
                    ESSID:"MWireless"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:3/5  Signal level:-69 dBm  Noise level:-90 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 04 - Address: 06:0B:0A:13:12:7E
                    ESSID:"UM Wireless Network"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:3/5  Signal level:-68 dBm  Noise level:-90 dBm
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 05 - Address: 00:18:F8:B7:DF:4D
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00"
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:3/5  Signal level:-68 dBm  Noise level:-87 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 06 - Address: 00:1C:10:E2:0F:28
                    ESSID:"MHL WLAN 148"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-90 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

auto lo
iface lo inet loopback

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G86 [GeForce 8400M GS] [10de:0427] (rev a1)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 1058:0704 Western Digital Technologies, Inc. 
Bus 002 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Linux name-b2crhh1 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
[    0.000000] No NUMA configuration found
[    0.000000] No AGP bridge found
[    0.372096] ACPI: No dock devices found.
[    0.445530] pnp: PnP ACPI: found 12 devices
[    0.560179] hub 1-0:1.0: USB hub found
[    0.590179] hub 2-0:1.0: USB hub found
[    0.590506] hub 3-0:1.0: USB hub found
[    0.590745] hub 4-0:1.0: USB hub found
[    0.590950] hub 5-0:1.0: USB hub found
[    0.591169] hub 6-0:1.0: USB hub found
[    0.591379] hub 7-0:1.0: USB hub found
[    0.594823] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.597474] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   16.711787] lp: driver loaded but no devices found
[   17.287740] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[   17.307410] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 12)
[   17.310064] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   17.310768] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   18.130237] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   18.130323] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   18.130375] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   58.730430] usb-storage: device found at 4
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:2  Signal level:181  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

 * Reconfiguring network interfaces...                                                                                                                                     Ignoring unknown interface eth1=eth1.

---

### Post by framplinux on 2010-05-11
> **zaleksf said:**
> ... I used a script to check my system (attached - the one recommended above didn't work for me). 
Pls let me know which problems you had to invoke the script collectNWData. I don't want this to happen and I'll fix this if you provide details about your problems with the script.

The script check-wireless.sh executes a lot of commands which help to detect wireless config problems. I'm interested to get in contact with the author of this script. Would be glad you either post the source url of this script in this thread or just send a PN to me.

I also learned there is a tool called lshw available on Ubuntu. Unfortunately it's output quite huge. On openSuSe there is a tool called hwinfo available which also provided a lot of info. In collectNWData I grep for important info to keep the ouput as small as possible. I'll add the output of lshw in collectNWData if it's running on Ubuntu - but need feedback which info is required and which one can be suppressed in the script output in order to keep the listing as short as possible.

---

### Post by bauerber on 2010-05-17
Curiously enough, after once more reinstalling wicd and completely getting rid of network-manager, my problem just disappeared (sort of).
Occasionally I still get the 'Invalid Authentication' notice, but trying again solves this every time.
This is quite frustrating, I'd rather have *solved* the problem.

Thanks for the input anyway!

---

### Post by AZ_RUNE on 2010-05-22
I am suffering the same issue on an ASUS 1201N EEEPC with an Intel 5300 wifi card.  I have been to the bug report [572777]("https://bugs.launchpad.net/ubuntu/+bug/572777") with no luck so far even with the 0.6.10 wpa supplicant.

Any further ideas and I am using Ubuntu 64-bit?


hobotekk@Silver-Bullet:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1) hobotekk@Silver-Bullet:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
05:00.0 VGA compatible controller: nVidia Corporation ION VGA [GeForce 9400M] (rev b1)
07:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection
09:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
hobotekk@Silver-Bullet:~$ 

00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
05:00.0 VGA compatible controller: nVidia Corporation ION VGA [GeForce 9400M] (rev b1)
07:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection
09:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
hobotekk@Silver-Bullet:~$

---

