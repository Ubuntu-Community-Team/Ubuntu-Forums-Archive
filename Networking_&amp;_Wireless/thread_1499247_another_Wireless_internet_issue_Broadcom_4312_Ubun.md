---
title: "another Wireless internet issue Broadcom 4312 Ubuntu 10.04"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by Coastal on 2010-06-01
I've been stalking the forums for the past few days trying various fixes to no avail.  I'm sorry for more clutter of this issue.  Here's what I have:

emachines e725 laptop, dual core T4400 Pentium, 64bit, running Windows 7 and just installed Ubuntu 10.04.

My ethernet port works for cat internet but wireless does not.    My wireless appears but when I open browser no connection.  Here is my ifconfig:

 ifconfig
eth0      Link encap:Ethernet  HWaddr 70:5a:b6:1e:ec:0f  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::725a:b6ff:fe1e:ec0f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2530 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:3908834 (3.9 MB)  TX bytes:319025 (319.0 KB)
          Interrupt:28 

eth1      Link encap:Ethernet  HWaddr c4:17:fe:4b:80:e7  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::c617:feff:fe4b:80e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:3 dropped:0 overruns:0 frame:18168
          TX packets:11 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2995 (2.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:300 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22560 (22.5 KB)  TX bytes:22560 (22.5 KB)

iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:199  Noise level:165
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.


**Im admittedly not great with networking but I'm learning quick thanks to this.  Thank you in advance for any assistance!  ~Josh**

---

### Post by pdc on 2010-06-02
try this diagnostic script

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/Benutzeranleitung/Usersguide-von/of-collectNWData.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/Benutzeranleitung/Usersguide-von/of-collectNWData.html#English)

download it and run it

see if it helps: it will offer solutions 

post the results back if not solved

---

### Post by Coastal on 2010-06-02
Thank you for your reply.  Here is what the script said:

--- Which type of your network connection should be tested?
--- (2) Wireless connection (WLAN)
--- What's the type of networktopology?
--- (2) WLAN HW router <---> LinuxClient
--- On which host is the script executed?
--- (1) LinuxClient
--- WLAN SSID to connect to: §§§§§§§§1

--- NWEliza is analyzing the system for common network configuration errors ...

!!! CND0110E: For the selected connection type there was no active network interface found on your system
!!! CND0450W: WLAN key masquerading is not fully tested on this distribution. Please check output file collectNWData.txt for visible WLAN keys and masquerade them manually
Linux yoshi-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
==================================================================================================================
*** cat /etc/*[-_]release || cat /etc/*[-_]version
/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
==================================================================================================================
*** cat /etc/resolv | grep -i "nameserver"
nameserver %%.%%.%.%%1
nameserver %%.%%.%.%%2
==================================================================================================================
*** cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    yoshi-laptop
==================================================================================================================
*** route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      0.0.0.0         255.255.255.0   U     2      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
==================================================================================================================
*** ifconfig
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:#1  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::725a:b6ff:fe1e:ec0f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1237 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1164 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:1201355 (1.2 MB)  TX bytes:244442 (244.4 KB)
          Interrupt:29 
eth1      Link encap:Ethernet  HWaddr ##:##:##:##:##:#2  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::c617:feff:fe4b:80e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:6643
          TX packets:11 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2995 (2.9 KB)
          Interrupt:17 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)
==================================================================================================================
*** ping tests
Ping of 195.135.220.3 failed
Ping of [www.suse.de](www.suse.de) OK
==================================================================================================================
*** lspci
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
05:00.0 Ethernet controller [0200]: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter [1969:1062] (rev c0)
==================================================================================================================
*** lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
==================================================================================================================
*** lsmod # (filtered)
| ahci            | atl1c           | bitblit         | drm             | drm_kms_helper   |
| fbcon           | font            | i2c_algo_bit    | i915            | intel_agp        |
| iptable_nat     | ipt_MASQUERADE  | lib80211        | lib80211_crypt_tkip| lp               |
| nf_conntrack_ftp| nf_conntrack_h323| nf_conntrack_ipv4| nf_conntrack_irc| nf_conntrack_pptp |
| nf_conntrack_proto_gre| nf_conntrack_sip| nf_conntrack_tftp| nf_nat          | nf_nat_ftp       |
| nf_nat_h323     | nf_nat_irc      | nf_nat_pptp     | nf_nat_proto_gre| nf_nat_sip       |
| nf_nat_tftp     | output          | serio_raw       | snd_hda_codec   | snd_hda_codec_realtek |
| snd_hda_intel   | snd_hwdep       | snd_rawmidi     | snd_seq_device  | snd_seq_dummy    |
| snd_seq_midi    | snd_seq_oss     | softcursor      | tileblit        | vga16fb          |
| vgastate        | video           | wl              | xt_state        | xt_tcpudp        |
==================================================================================================================
*** cat /etc/network/interfaces
--- /etc/network/interfaces
auto lo
iface lo inet loopback
==================================================================================================================
*** iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      IEEE 802.11bg  ESSID:"§§§§§§§§2"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: ##:##:##:##:##:#3   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-57 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
==================================================================================================================
*** Actual date for bias of following greps
15:55:12 2010-06-02
==================================================================================================================
*** grep -i radio /var/log/messages* | tail -n 5
May 31 05:49:54 yoshi-laptop kernel: [    7.487455] Registered led device: b43-phy0::radio
May 31 05:51:16 yoshi-laptop kernel: [    8.193571] Registered led device: b43-phy0::radio
May 31 10:30:00 yoshi-laptop kernel: [   10.373002] Registered led device: b43-phy0::radio
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
| atmel_at76c506.bin      | atmsar11.fw             | av7110                  | bnx2                     |
| bnx2x-e1-4.8.53.0.fw    | bnx2x-e1-5.2.7.0.fw     | bnx2x-e1h-4.8.53.0.fw   | bnx2x-e1h-5.2.7.0.fw     |
| cis                     | cpia2                   | cxgb3                   | dabusb                   |
| dsp56k                  | dvb-fe-xc5000-1.6.114.fw| dvb-usb-dib0700-1.20.fw | e100                     |
| ea                      | edgeport                | emi26                   | emi62                    |
| ess                     | i2400m-fw-usb-1.3.sbcf  | i2400m-fw-usb-1.4.sbcf  | intelliport2.bin         |
| ipw2100-1.3.fw          | ipw2100-1.3-i.fw        | ipw2100-1.3-p.fw        | ipw2200-bss.fw           |
| ipw2200-ibss.fw         | ipw2200-sniffer.fw      | iwlwifi-1000-3.ucode    | iwlwifi-3945-2.ucode     |
| iwlwifi-4965-2.ucode    | iwlwifi-5000-1.ucode    | iwlwifi-5000-2.ucode    | iwlwifi-5150-2.ucode     |
| iwlwifi-6000-4.ucode    | kaweth                  | keyspan                 | keyspan_pda              |
| korg                    | libertas                | matrox                  | mts_cdma.fw              |
| mts_edge.fw             | mts_gsm.fw              | mwl8k                   | myricom                  |
| NPE-B                   | NPE-C                   | ositech                 | ql2100_fw.bin            |
| ql2200_fw.bin           | ql2300_fw.bin           | ql2322_fw.bin           | ql2400_fw.bin            |
| ql2500_fw.bin           | qlogic                  | r128                    | radeon                   |
| rt2561.bin              | rt2561s.bin             | rt2661.bin              | rt2860.bin               |
| rt2870.bin              | rt73.bin                | RTL8192SE               | sb16                     |
| scripts                 | slicoss                 | sun                     | sxg                      |
| tehuti                  | ti_3410.fw              | ti_5052.fw              | tigon                    |
| tr_smctr.bin            | ttusb-budget            | usbdux                  | usbduxfast_firmware.bin  |
| usbdux_firmware.bin     | v4l-cx231xx-avcore-01.fw| v4l-cx23418-apu.fw      | v4l-cx23418-cpu.fw       |
| v4l-cx23418-dig.fw      | v4l-cx2341x-dec.fw      | v4l-cx2341x-enc.fw      | v4l-cx2341x-init.mpg     |
| v4l-cx23885-avcore-01.fw| v4l-cx23885-enc.fw      | v4l-cx25840.fw          | v4l-pvrusb2-24xxx-01.fw  |
| v4l-pvrusb2-29xxx-01.fw | vicam                   | whiteheat.fw            | whiteheat_loader.fw      |
| yam                     | yamaha                  | zd1201-ap.fw            | zd1201.fw                |
| zd1211                  |
--- /lib/firmware
/lib/firmware/b43 not found
==================================================================================================================
*** ndiswrapper -l
No ndiswrapper module loaded
==================================================================================================================
*** Active processes
wpa_supplicant:YES knetworkmanager:NO nm-applet:YES
==================================================================================================================
*** grep 'eth|ath|wlan|ra' /etc/udev/rules.d/*net_persistent* /etc/udev/rules.d/*persistent-net*
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
==================================================================================================================
*** grep -r 'eth[0-10]|ath[0-10]|wlan[0-10]|ra[0-10]' /etc/modprobe.*
==================================================================================================================
*** iwlist scanning
                    ESSID:"§§§§§§§§2"
                    Quality:5/5  Signal level:-21 dBm  Noise level:-92 dBm
                    Encryption key:off
                    ESSID:"§§§§§§§§3"
                    Quality:1/5  Signal level:-84 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                    IE: WPA Version 1
                    Encryption key:on
                    ESSID:"§§§§§§§§4"
                    Quality:1/5  Signal level:-89 dBm  Noise level:-92 dBm
                    Encryption key:on
                    ESSID:"§§§§§§§§5"
                    Quality:1/5  Signal level:-84 dBm  Noise level:-92 dBm
                    Encryption key:on
==================================================================================================================
*** NWElizaStates
IF:eth0 IM:1 IF:eth1 IM:2 DI:2 AP:1 FALON:0 
[/code]

---

### Post by bkratz on 2010-06-02
I noticed this in the above

*** iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
eth1 IEEE 802.11bg ESSID:"§§§§§§§§2" 
Mode:Ad-Hoc Frequency:2.412 GHz Cell: ##:##:##:##:##:#3 
Bit Rate=54 Mb/s Tx-Power:24 dBm 


The mode Ad-hoc should show as managed.  See this posting about that subject.

[http://ubuntuforums.org/showpost.php?p=9276146&postcount=15](http://ubuntuforums.org/showpost.php?p=9276146&postcount=15)

Hopefully this may help you, good luck!


Yours is eth1 though, not wlan0 in the example.

---

### Post by Coastal on 2010-06-03
Thanks.  I did that, now in IWCONFIG it shows:

iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:199  Noise level:165
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.


What next ?

---

### Post by pdc on 2010-06-03
I am not clear if you have installed the broadcom sta driver as here

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

first set of instructions

---

### Post by Coastal on 2010-06-04
Yes I had the driver installed:  [IMG]file:///tmp/moz-screenshot-2.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG][IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by Coastal on 2010-06-07
Well, I just went ahead and removed Ubuntu and will reinstall to see if that works.  I'll try all of the basics again.  Thanks for your help

---

### Post by henyongadik01 on 2010-07-13
hi. my wireless lan is detected as eth1. it must be detected as wlan to be used in aircrack. what will i do? 

btw, even if you try live cd, and install the Broadcom STA, it is still detected as eth1. thanks.

here is my data:

```

collectNWData.sh V0.6.3.8-4 (Rev: 1.235, Build: 2010/07/11 17:49:05 UTC)
--- Which type of your network connection should be tested?
--- (2) Wireless connection (WLAN)
--- What's the type of networktopology?
--- (2) WLAN HW router <---> LinuxClient
--- On which host is the script executed?
--- (1) LinuxClient
--- WLAN SSID to connect to: §§§§§§§§1

--- NWEliza is analyzing the system for common network configuration errors ...

!!! CND0450W: WLAN key masquerading is not fully tested on this distribution. Please check output file collectNWData.txt for visible WLAN keys and masquerade them manually

--- Go to http://www.linux-tips-and-tricks.de/CND#English to get more detailed instructions 
--- about the error/warning messages and how to fix the problems on your own.

--- If you are unsuccessful then place the contents of file collectNWData.txt in the net
--- (see http://www.linux-tips-and-tricks.de/CND_UPL#English for links) 
--- and then paste the nopaste link on your favorite Linux forum.

==================================================================================================================
==================================================================================================================
*** uname -a
Linux computer99 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
==================================================================================================================
*** cat /etc/*[-_]release || cat /etc/*[-_]version
/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
==================================================================================================================
*** cat /etc/resolv | grep -i "nameserver"
nameserver 192.168.0.254
==================================================================================================================
*** cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    computer99
==================================================================================================================
*** route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 eth1
==================================================================================================================
*** ifconfig
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:#1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 Base address:0x4000 
eth1      Link encap:Ethernet  HWaddr ##:##:##:##:##:#2  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:fe67:ce2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1620 errors:0 dropped:0 overruns:0 frame:339
          TX packets:1786 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1628442 (1.6 MB)  TX bytes:250345 (250.3 KB)
          Interrupt:18 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5328 (5.3 KB)  TX bytes:5328 (5.3 KB)
==================================================================================================================
*** ping tests
Ping of 195.135.220.3 OK
Ping of www.suse.de OK
==================================================================================================================
*** lspci
09:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
==================================================================================================================
*** lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:c108 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
==================================================================================================================
*** lshw -C network (filtered)
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.0.103 latency=0 multicast=yes wireless=IEEE 802.11bg
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
==================================================================================================================
*** lsmod # (filtered)
| ahci            | arc4            | binfmt_misc     | bitblit         | bnep             |
| btusb           | edac_core       | edac_mce_amd    | fbcon           | fglrx            |
| font            | hid             | i2c_piix4       | jmb38x_ms       | l2cap            |
| led_class       | lib80211        | lirc_dev        | lirc_ene0100    | lp               |
| memstick        | michael_mic     | mii             | output          | ppdev            |
| r8169           | rfcomm          | sco             | sdhci           | sdhci_pci        |
| serio_raw       | shpchp          | softcursor      | stp             | tileblit         |
| v4l1_compat     | v4l2_compat_ioctl32| vga16fb         | vgastate        | wl               |
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
eth1      IEEE 802.11bg  ESSID:"§§§§§§§§1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: ##:##:##:##:##:#3   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-39 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
==================================================================================================================
*** Actual date for bias of following greps
21:39:00 2010-07-13
==================================================================================================================
*** grep -i radio /var/log/messages* | tail -n 5
==================================================================================================================
*** dmesg | grep -i radio | tail -n 5
==================================================================================================================
*** tail -n 300 /var/log/messages* | /bin/grep -i firmware | tail -n 5
Jul 13 21:14:05 computer99 kernel: [   19.403825] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
==================================================================================================================
*** ls /lib/firmware/*
| 2.6.32-21-generic       | 3com                    | acenic                  | adaptec                  |
| advansys                | agere_ap_fw.bin         | agere_sta_fw.bin        | aic94xx-seq.fw           |
| ar9170-1.fw             | ar9170-2.fw             | ar9170.fw               | ath3k-1.fw               |
| atmel_at76c502_3com.bin | atmel_at76c502.bin      | atmel_at76c502d.bin     | atmel_at76c502e.bin      |
| atmel_at76c504_2958.bin | atmel_at76c504a_2958.bin| atmel_at76c504.bin      | atmel_at76c506.bin       |
| atmsar11.fw             | av7110                  | bnx2                    | bnx2x-e1-4.8.53.0.fw     |
| bnx2x-e1-5.2.7.0.fw     | bnx2x-e1h-4.8.53.0.fw   | bnx2x-e1h-5.2.7.0.fw    | cis                      |
| cpia2                   | cxgb3                   | dabusb                  | dsp56k                   |
| dvb-fe-xc5000-1.6.114.fw| dvb-usb-dib0700-1.20.fw | e100                    | ea                       |
| edgeport                | emi26                   | emi62                   | ess                      |
| i2400m-fw-usb-1.3.sbcf  | i2400m-fw-usb-1.4.sbcf  | intelliport2.bin        | ipw2100-1.3.fw           |
| ipw2100-1.3-i.fw        | ipw2100-1.3-p.fw        | ipw2200-bss.fw          | ipw2200-ibss.fw          |
| ipw2200-sniffer.fw      | iwlwifi-1000-3.ucode    | iwlwifi-3945-2.ucode    | iwlwifi-4965-2.ucode     |
| iwlwifi-5000-1.ucode    | iwlwifi-5000-2.ucode    | iwlwifi-5150-2.ucode    | iwlwifi-6000-4.ucode     |
| kaweth                  | keyspan                 | keyspan_pda             | korg                     |
| libertas                | matrox                  | mts_cdma.fw             | mts_edge.fw              |
| mts_gsm.fw              | mwl8k                   | myricom                 | NPE-B                    |
| NPE-C                   | ositech                 | ql2100_fw.bin           | ql2200_fw.bin            |
| ql2300_fw.bin           | ql2322_fw.bin           | ql2400_fw.bin           | ql2500_fw.bin            |
| qlogic                  | r128                    | radeon                  | rt2561.bin               |
| rt2561s.bin             | rt2661.bin              | rt2860.bin              | rt2870.bin               |
| rt73.bin                | RTL8192SE               | sb16                    | scripts                  |
| slicoss                 | sun                     | sxg                     | tehuti                   |
| ti_3410.fw              | ti_5052.fw              | tigon                   | tr_smctr.bin             |
| ttusb-budget            | usbdux                  | usbduxfast_firmware.bin | usbdux_firmware.bin      |
| v4l-cx231xx-avcore-01.fw| v4l-cx23418-apu.fw      | v4l-cx23418-cpu.fw      | v4l-cx23418-dig.fw       |
| v4l-cx2341x-dec.fw      | v4l-cx2341x-enc.fw      | v4l-cx2341x-init.mpg    | v4l-cx23885-avcore-01.fw |
| v4l-cx23885-enc.fw      | v4l-cx25840.fw          | v4l-pvrusb2-24xxx-01.fw | v4l-pvrusb2-29xxx-01.fw  |
| vicam                   | whiteheat.fw            | whiteheat_loader.fw     | yam                      |
| yamaha                  | zd1201-ap.fw            | zd1201.fw               | zd1211                   |
--- /lib/firmware
/lib/firmware/b43 not found
==================================================================================================================
*** ndiswrapper -l
No ndiswrapper module loaded
==================================================================================================================
*** Active processes
wpa_supplicant:YES knetworkmanager:NO nm-applet:YES
==================================================================================================================
*** grep 'eth|ath|wlan|ra' /etc/udev/rules.d/*net_persistent* /etc/udev/rules.d/*persistent-net*
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
==================================================================================================================
*** grep -r 'eth[0-10]|ath[0-10]|wlan[0-10]|ra[0-10]' /etc/modprobe.*
==================================================================================================================
*** iwlist scanning
                    ESSID:"§§§§§§§§1"
                    Quality:5/5  Signal level:-36 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                    IE: WPA Version 1
                    Encryption key:on
                    ESSID:"§§§§§§§§2"
                    Quality:1/5  Signal level:-88 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                    Encryption key:on
==================================================================================================================
*** NWElizaStates V0.6.3.8-4
IF:eth0 IM:1 IF:eth1 IM:2 DI:2 AP:1 FALON:1 NIC:0 cNiC:2:0 NI:0 cNI:0 PNG:0 DNS:0 MTU:1 NISS:0 IP6:0 WLW:0 RTDT:debian 

```

---

### Post by bkratz on 2010-07-13
> **henyongadik01 said:**
> hi. my wireless lan is detected as eth1. it must be detected as wlan to be used in aircrack. what will i do? 

btw, even if you try live cd, and install the Broadcom STA, it is still detected as eth1. thanks.

here is my data:

```

collectNWData.sh V0.6.3.8-4 (Rev: 1.235, Build: 2010/07/11 17:49:05 UTC)
--- Which type of your network connection should be tested?
--- (2) Wireless connection (WLAN)
--- What's the type of networktopology?
--- (2) WLAN HW router <---> LinuxClient
--- On which host is the script executed?
--- (1) LinuxClient
--- WLAN SSID to connect to: §§§§§§§§1

--- NWEliza is analyzing the system for common network configuration errors ...

!!! CND0450W: WLAN key masquerading is not fully tested on this distribution. Please check output file collectNWData.txt for visible WLAN keys and masquerade them manually

--- Go to http://www.linux-tips-and-tricks.de/CND#English to get more detailed instructions 
--- about the error/warning messages and how to fix the problems on your own.

--- If you are unsuccessful then place the contents of file collectNWData.txt in the net
--- (see http://www.linux-tips-and-tricks.de/CND_UPL#English for links) 
--- and then paste the nopaste link on your favorite Linux forum.

==================================================================================================================
==================================================================================================================
*** uname -a
Linux computer99 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
==================================================================================================================
*** cat /etc/*[-_]release || cat /etc/*[-_]version
/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
==================================================================================================================
*** cat /etc/resolv | grep -i "nameserver"
nameserver 192.168.0.254
==================================================================================================================
*** cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    computer99
==================================================================================================================
*** route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 eth1
==================================================================================================================
*** ifconfig
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:#1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 Base address:0x4000 
eth1      Link encap:Ethernet  HWaddr ##:##:##:##:##:#2  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:fe67:ce2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1620 errors:0 dropped:0 overruns:0 frame:339
          TX packets:1786 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1628442 (1.6 MB)  TX bytes:250345 (250.3 KB)
          Interrupt:18 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5328 (5.3 KB)  TX bytes:5328 (5.3 KB)
==================================================================================================================
*** ping tests
Ping of 195.135.220.3 OK
Ping of www.suse.de OK
==================================================================================================================
*** lspci
09:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
==================================================================================================================
*** lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:c108 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
==================================================================================================================
*** lshw -C network (filtered)
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.0.103 latency=0 multicast=yes wireless=IEEE 802.11bg
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
==================================================================================================================
*** lsmod # (filtered)
| ahci            | arc4            | binfmt_misc     | bitblit         | bnep             |
| btusb           | edac_core       | edac_mce_amd    | fbcon           | fglrx            |
| font            | hid             | i2c_piix4       | jmb38x_ms       | l2cap            |
| led_class       | lib80211        | lirc_dev        | lirc_ene0100    | lp               |
| memstick        | michael_mic     | mii             | output          | ppdev            |
| r8169           | rfcomm          | sco             | sdhci           | sdhci_pci        |
| serio_raw       | shpchp          | softcursor      | stp             | tileblit         |
| v4l1_compat     | v4l2_compat_ioctl32| vga16fb         | vgastate        | wl               |
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
eth1      IEEE 802.11bg  ESSID:"§§§§§§§§1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: ##:##:##:##:##:#3   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-39 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
==================================================================================================================
*** Actual date for bias of following greps
21:39:00 2010-07-13
==================================================================================================================
*** grep -i radio /var/log/messages* | tail -n 5
==================================================================================================================
*** dmesg | grep -i radio | tail -n 5
==================================================================================================================
*** tail -n 300 /var/log/messages* | /bin/grep -i firmware | tail -n 5
Jul 13 21:14:05 computer99 kernel: [   19.403825] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
==================================================================================================================
*** ls /lib/firmware/*
| 2.6.32-21-generic       | 3com                    | acenic                  | adaptec                  |
| advansys                | agere_ap_fw.bin         | agere_sta_fw.bin        | aic94xx-seq.fw           |
| ar9170-1.fw             | ar9170-2.fw             | ar9170.fw               | ath3k-1.fw               |
| atmel_at76c502_3com.bin | atmel_at76c502.bin      | atmel_at76c502d.bin     | atmel_at76c502e.bin      |
| atmel_at76c504_2958.bin | atmel_at76c504a_2958.bin| atmel_at76c504.bin      | atmel_at76c506.bin       |
| atmsar11.fw             | av7110                  | bnx2                    | bnx2x-e1-4.8.53.0.fw     |
| bnx2x-e1-5.2.7.0.fw     | bnx2x-e1h-4.8.53.0.fw   | bnx2x-e1h-5.2.7.0.fw    | cis                      |
| cpia2                   | cxgb3                   | dabusb                  | dsp56k                   |
| dvb-fe-xc5000-1.6.114.fw| dvb-usb-dib0700-1.20.fw | e100                    | ea                       |
| edgeport                | emi26                   | emi62                   | ess                      |
| i2400m-fw-usb-1.3.sbcf  | i2400m-fw-usb-1.4.sbcf  | intelliport2.bin        | ipw2100-1.3.fw           |
| ipw2100-1.3-i.fw        | ipw2100-1.3-p.fw        | ipw2200-bss.fw          | ipw2200-ibss.fw          |
| ipw2200-sniffer.fw      | iwlwifi-1000-3.ucode    | iwlwifi-3945-2.ucode    | iwlwifi-4965-2.ucode     |
| iwlwifi-5000-1.ucode    | iwlwifi-5000-2.ucode    | iwlwifi-5150-2.ucode    | iwlwifi-6000-4.ucode     |
| kaweth                  | keyspan                 | keyspan_pda             | korg                     |
| libertas                | matrox                  | mts_cdma.fw             | mts_edge.fw              |
| mts_gsm.fw              | mwl8k                   | myricom                 | NPE-B                    |
| NPE-C                   | ositech                 | ql2100_fw.bin           | ql2200_fw.bin            |
| ql2300_fw.bin           | ql2322_fw.bin           | ql2400_fw.bin           | ql2500_fw.bin            |
| qlogic                  | r128                    | radeon                  | rt2561.bin               |
| rt2561s.bin             | rt2661.bin              | rt2860.bin              | rt2870.bin               |
| rt73.bin                | RTL8192SE               | sb16                    | scripts                  |
| slicoss                 | sun                     | sxg                     | tehuti                   |
| ti_3410.fw              | ti_5052.fw              | tigon                   | tr_smctr.bin             |
| ttusb-budget            | usbdux                  | usbduxfast_firmware.bin | usbdux_firmware.bin      |
| v4l-cx231xx-avcore-01.fw| v4l-cx23418-apu.fw      | v4l-cx23418-cpu.fw      | v4l-cx23418-dig.fw       |
| v4l-cx2341x-dec.fw      | v4l-cx2341x-enc.fw      | v4l-cx2341x-init.mpg    | v4l-cx23885-avcore-01.fw |
| v4l-cx23885-enc.fw      | v4l-cx25840.fw          | v4l-pvrusb2-24xxx-01.fw | v4l-pvrusb2-29xxx-01.fw  |
| vicam                   | whiteheat.fw            | whiteheat_loader.fw     | yam                      |
| yamaha                  | zd1201-ap.fw            | zd1201.fw               | zd1211                   |
--- /lib/firmware
/lib/firmware/b43 not found
==================================================================================================================
*** ndiswrapper -l
No ndiswrapper module loaded
==================================================================================================================
*** Active processes
wpa_supplicant:YES knetworkmanager:NO nm-applet:YES
==================================================================================================================
*** grep 'eth|ath|wlan|ra' /etc/udev/rules.d/*net_persistent* /etc/udev/rules.d/*persistent-net*
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
==================================================================================================================
*** grep -r 'eth[0-10]|ath[0-10]|wlan[0-10]|ra[0-10]' /etc/modprobe.*
==================================================================================================================
*** iwlist scanning
                    ESSID:"§§§§§§§§1"
                    Quality:5/5  Signal level:-36 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                    IE: WPA Version 1
                    Encryption key:on
                    ESSID:"§§§§§§§§2"
                    Quality:1/5  Signal level:-88 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                    Encryption key:on
==================================================================================================================
*** NWElizaStates V0.6.3.8-4
IF:eth0 IM:1 IF:eth1 IM:2 DI:2 AP:1 FALON:1 NIC:0 cNiC:2:0 NI:0 cNI:0 PNG:0 DNS:0 MTU:1 NISS:0 IP6:0 WLW:0 RTDT:debian 

```



Not an expert by any means! but I believe you can't use the monitor mode with the STA driver, only the B43.  From the aircrack website
```

Users whom use broadcom linux_sta driver (otherwise known as wl) should note that there are no monitor/injection modes with such driver. Broadcom deliberately removed the functionality out of their proprietary binary blob. Read here for more info: http://seclists.org/fulldisclosure/2008/Nov/506. Also b43 supports less than a handful of chipsets, take note on which ones are unsupported and see if yours fall into that category: b43

```
[http://www.aircrack-ng.org/doku.php?id=compatibility_drivers](http://www.aircrack-ng.org/doku.php?id=compatibility_drivers)

---

### Post by henyongadik01 on 2010-07-13
hi. here is my new data. right now, my wireless is detected as wlan, not eth.

```

collectNWData.sh V0.6.3.8-4 (Rev: 1.235, Build: 2010/07/11 17:49:05 UTC)
--- Which type of your network connection should be tested?
--- (2) Wireless connection (WLAN)
--- What's the type of networktopology?
--- (2) WLAN HW router <---> LinuxClient
--- On which host is the script executed?
--- (1) LinuxClient
--- WLAN SSID to connect to: §§§§§§§§1

--- NWEliza is analyzing the system for common network configuration errors ...

!!! CND0450W: WLAN key masquerading is not fully tested on this distribution. Please check output file collectNWData.txt for visible WLAN keys and masquerade them manually

--- Go to http://www.linux-tips-and-tricks.de/CND#English to get more detailed instructions 
--- about the error/warning messages and how to fix the problems on your own.

--- If you are unsuccessful then place the contents of file collectNWData.txt in the net
--- (see http://www.linux-tips-and-tricks.de/CND_UPL#English for links) 
--- and then paste the nopaste link on your favorite Linux forum.

==================================================================================================================
==================================================================================================================
*** uname -a
Linux computer99 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
==================================================================================================================
*** cat /etc/*[-_]release || cat /etc/*[-_]version
/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
==================================================================================================================
*** cat /etc/resolv | grep -i "nameserver"
nameserver 192.168.0.254
==================================================================================================================
*** cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    computer99
==================================================================================================================
*** route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 wlan0
==================================================================================================================
*** ifconfig
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:#1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 Base address:0xa000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
wlan0     Link encap:Ethernet  HWaddr ##:##:##:##:##:#2  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:fe67:ce2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:461 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:761273 (761.2 KB)  TX bytes:55019 (55.0 KB)
==================================================================================================================
*** ping tests
Ping of 195.135.220.3 OK
Ping of www.suse.de OK
==================================================================================================================
*** lspci
09:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
==================================================================================================================
*** lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:c108 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
==================================================================================================================
*** lshw -C network (filtered)
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.103 multicast=yes wireless=IEEE 802.11bg
==================================================================================================================
*** lsmod # (filtered)
| aes_generic     | aes_x86_64      | ahci            | arc4            | b43              |
| binfmt_misc     | bitblit         | bnep            | btusb           | cfg80211         |
| edac_core       | edac_mce_amd    | fbcon           | fglrx           | font             |
| hid             | i2c_piix4       | jmb38x_ms       | l2cap           | led_class        |
| lirc_dev        | lirc_ene0100    | lp              | mac80211        | memstick         |
| mii             | output          | ppdev           | r8169           | rfcomm           |
| sco             | sdhci           | sdhci_pci       | serio_raw       | shpchp           |
| softcursor      | ssb             | stp             | tileblit        | v4l1_compat      |
| v4l2_compat_ioctl32| vga16fb         | vgastate        |
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
wlan0     IEEE 802.11bg  ESSID:"§§§§§§§§1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: ##:##:##:##:##:#3   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-26 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
==================================================================================================================
*** Actual date for bias of following greps
05:39:40 2010-07-14
==================================================================================================================
*** grep -i radio /var/log/messages* | tail -n 5
Jul 14 05:37:58 computer99 kernel: [   20.041684] Registered led device: b43-phy0::radio
==================================================================================================================
*** dmesg | grep -i radio | tail -n 5
[   20.041684] Registered led device: b43-phy0::radio
==================================================================================================================
*** tail -n 300 /var/log/messages* | /bin/grep -i firmware | tail -n 5
Jul 14 05:37:58 computer99 kernel: [   20.041780] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
Jul 14 05:37:58 computer99 kernel: [   20.150191] b43 ssb0:0: firmware: requesting b43/ucode15.fw
Jul 14 05:37:58 computer99 kernel: [   20.485999] b43 ssb0:0: firmware: requesting b43/lp0initvals15.fw
Jul 14 05:37:58 computer99 kernel: [   20.512723] b43 ssb0:0: firmware: requesting b43/lp0bsinitvals15.fw
Jul 14 05:37:59 computer99 kernel: [   20.670210] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
==================================================================================================================
*** ls /lib/firmware/*
| 2.6.32-21-generic       | 3com                    | acenic                  | adaptec                  |
| advansys                | agere_ap_fw.bin         | agere_sta_fw.bin        | aic94xx-seq.fw           |
| ar9170-1.fw             | ar9170-2.fw             | ar9170.fw               | ath3k-1.fw               |
| atmel_at76c502_3com.bin | atmel_at76c502.bin      | atmel_at76c502d.bin     | atmel_at76c502e.bin      |
| atmel_at76c504_2958.bin | atmel_at76c504a_2958.bin| atmel_at76c504.bin      | atmel_at76c506.bin       |
| atmsar11.fw             | av7110                  | b43                     | b43legacy                |
| bnx2                    | bnx2x-e1-4.8.53.0.fw    | bnx2x-e1-5.2.7.0.fw     | bnx2x-e1h-4.8.53.0.fw    |
| bnx2x-e1h-5.2.7.0.fw    | cis                     | cpia2                   | cxgb3                    |
| dabusb                  | dsp56k                  | dvb-fe-xc5000-1.6.114.fw| dvb-usb-dib0700-1.20.fw  |
| e100                    | ea                      | edgeport                | emi26                    |
| emi62                   | ess                     | i2400m-fw-usb-1.3.sbcf  | i2400m-fw-usb-1.4.sbcf   |
| intelliport2.bin        | ipw2100-1.3.fw          | ipw2100-1.3-i.fw        | ipw2100-1.3-p.fw         |
| ipw2200-bss.fw          | ipw2200-ibss.fw         | ipw2200-sniffer.fw      | iwlwifi-1000-3.ucode     |
| iwlwifi-3945-2.ucode    | iwlwifi-4965-2.ucode    | iwlwifi-5000-1.ucode    | iwlwifi-5000-2.ucode     |
| iwlwifi-5150-2.ucode    | iwlwifi-6000-4.ucode    | kaweth                  | keyspan                  |
| keyspan_pda             | korg                    | libertas                | matrox                   |
| mts_cdma.fw             | mts_edge.fw             | mts_gsm.fw              | mwl8k                    |
| myricom                 | NPE-B                   | NPE-C                   | ositech                  |
| ql2100_fw.bin           | ql2200_fw.bin           | ql2300_fw.bin           | ql2322_fw.bin            |
| ql2400_fw.bin           | ql2500_fw.bin           | qlogic                  | r128                     |
| radeon                  | rt2561.bin              | rt2561s.bin             | rt2661.bin               |
| rt2860.bin              | rt2870.bin              | rt73.bin                | RTL8192SE                |
| sb16                    | scripts                 | slicoss                 | sun                      |
| sxg                     | tehuti                  | ti_3410.fw              | ti_5052.fw               |
| tigon                   | tr_smctr.bin            | ttusb-budget            | usbdux                   |
| usbduxfast_firmware.bin | usbdux_firmware.bin     | v4l-cx231xx-avcore-01.fw| v4l-cx23418-apu.fw       |
| v4l-cx23418-cpu.fw      | v4l-cx23418-dig.fw      | v4l-cx2341x-dec.fw      | v4l-cx2341x-enc.fw       |
| v4l-cx2341x-init.mpg    | v4l-cx23885-avcore-01.fw| v4l-cx23885-enc.fw      | v4l-cx25840.fw           |
| v4l-pvrusb2-24xxx-01.fw | v4l-pvrusb2-29xxx-01.fw | vicam                   | whiteheat.fw             |
| whiteheat_loader.fw     | yam                     | yamaha                  | zd1201-ap.fw             |
| zd1201.fw               | zd1211                  |
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
wpa_supplicant:YES knetworkmanager:NO nm-applet:YES
==================================================================================================================
*** grep 'eth|ath|wlan|ra' /etc/udev/rules.d/*net_persistent* /etc/udev/rules.d/*persistent-net*
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
==================================================================================================================
*** grep -r 'eth[0-10]|ath[0-10]|wlan[0-10]|ra[0-10]' /etc/modprobe.*
==================================================================================================================
*** iwlist scanning
                    Channel:11
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"§§§§§§§§1"
                    IE: IEEE 802.11i/WPA2 Version 1
                    IE: WPA Version 1
==================================================================================================================
*** NWElizaStates V0.6.3.8-4
IF:eth0 IM:1 IF:wlan0 IM:2 DI:2 AP:1 FALON:1 NIC:0 cNiC:2:0 NI:0 cNI:0 PNG:0 DNS:0 MTU:1 NISS:0 IP6:0 WLW:0 RTDT:debian 

```

ok. so here's what i did. 

1) i uninstalled the broadcom STA in the System > Administration > Hardware Drivers
2) Then i install the b43-fwcutter
3) Download and Extract the firmware
4) Restart.
5) now, my wireless is detected as wlan, not eth

thanks.

---

