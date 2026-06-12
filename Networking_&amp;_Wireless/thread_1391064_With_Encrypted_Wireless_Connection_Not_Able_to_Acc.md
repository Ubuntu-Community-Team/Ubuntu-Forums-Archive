---
title: "With Encrypted Wireless Connection Not Able to Access Internet"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by lbjtemp on 2010-01-26
With Encrypted Wireless Connection Not Able to Access Internet - no pings, internet browsing, etc. However, without encryption I am able to browse the internet.  I need encryption ... please help .... 

I am pasting diagnostics collected by shell procedure collectNWdata.sh..

Please help.


[FONT="Arial"][FONT="Fixedsys"]```

collectNWData.sh V0.6.2.0 (Rev: 1.193, Build: 2010/01/20 21:22:30 UTC)
--- Which type of your network connection should be tested?
--- (2) Wireless connection (WLAN)
--- What's the type of networktopology?
--- (2) WLAN HW router <---> LinuxClient
--- On which host is the script executed?
--- (1) LinuxClient
!!! CND0180I: The system can't ping external IP address 195.135.220.3
!!! CND0150E: There might be problems with the default gateway definition 98.155.16.1 on interface wlan0
!!! CND0450W: WLAN key masquerading is not fully tested on this distribution. Please check output file collectNWData.txt for visible WLAN keys and masquerade them manually
--- Go to http://www.linux-tips-and-tricks.de/CND#English to get more detailed instructions about the error/warning messages and how to fix the problems on your own
--- Place the contents of file collectNWData.txt in the net (see http://www.linux-tips-and-tricks.de/CND_UPL#English for links) and then paste the nopaste link on your favorite Linux forum.
==================================================================================================================
==================================================================================================================
*** uname -a
Linux ubucomputer 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux
==================================================================================================================
*** cat /etc/*[-_]release || cat /etc/*[-_]version
/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
==================================================================================================================
*** cat /etc/resolv | grep -i "nameserver"
nameserver %%%.%%.%%.%1
nameserver %%%.%%.%%.%2
==================================================================================================================
*** cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 ubucomputer
==================================================================================================================
*** route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
%%.%%%.%%.3     0.0.0.0         255.255.255.255 UH    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         %%.%%%.%%.3     0.0.0.0         UG    0      0        0 wlan0
==================================================================================================================
*** ifconfig
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:#1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xd000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5467 (5.4 KB)  TX bytes:5467 (5.4 KB)
wlan0     Link encap:Ethernet  HWaddr ##:##:##:##:##:#2  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:25ff:fe12:833b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:337 (337.0 B)  TX bytes:7226 (7.2 KB)
          Interrupt:16 Memory:ef000000-ef002000 
==================================================================================================================
*** ping tests
Ping of 195.135.220.3 failed
ping: unknown host www.suse.de
Ping of www.suse.de failed
==================================================================================================================
*** lspci
00:08.0 Network controller [0280]: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller [14e4:4301] (rev 02)
00:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
==================================================================================================================
*** lsusb
Bus 004 Device 002: ID 04e6:0325 SCM Microsystems, Inc. eUSB ORCA Quad Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 002 Device 002: ID 045e:0053 Microsoft Corp. Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
==================================================================================================================
*** lsmod # (filtered)
| 8139cp          | 8139too         | ac97_bus        | agpgart         | binfmt_misc      |
| crc_ccitt       | drm             | floppy          | hid_microsoft   | i2c_viapro       |
| ieee1394        | irda            | lp              | mii             | ndiswrapper      |
| ohci1394        | ppdev           | savage          | serio_raw       | shpchp           |
| snd_ac97_codec  | snd_mpu401_uart | snd_rawmidi     | snd_seq_device  | snd_seq_dummy    |
| snd_seq_midi    | snd_seq_oss     | snd_via82xx     | usb_storage     | via_agp          |
| via_ircc        |
==================================================================================================================
*** cat /etc/network/interfaces | /bin/grep -v "^#\|^$"
auto lo
iface lo inet loopback
iface wlan0 inet static
address 192.168.1.1
netmask 255.255.255.0
gateway 98.155.16.1
wireless-key s:7#5#2#D#9#4#4#F#C#F#0#1#C#
wireless-essid C#8#B#1#N#8#1#0#1#E#E#8
auto wlan0
==================================================================================================================
*** iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11b  ESSID:"C#8#B#1#N#8#1#0#1#E#E#8"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: ##:##:##:##:##:#3   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:@@ @@@-@@@@-@@@@-@@@@-@@@@-@@@@@@@   Security mode:open
          Power Management:off
          Link Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
==================================================================================================================
*** Actual date for bias of following greps
08:13:42 2010-01-26
==================================================================================================================
*** grep -i radio /var/log/messages* | tail -n 5
/var/log/messages.1:Jan 22 14:23:22 ubucomputer kernel: [   19.740465] b43legacy-phy0: Radio hardware status changed to DISABLED
/var/log/messages.1:Jan 22 15:20:38 ubucomputer kernel: [   20.331356] b43legacy-phy0: Radio hardware status changed to DISABLED
/var/log/messages.1:Jan 22 18:50:18 ubucomputer kernel: [   19.688860] b43legacy-phy0: Radio hardware status changed to DISABLED
/var/log/messages.1:Jan 23 06:58:33 ubucomputer kernel: [   19.894087] b43legacy-phy0: Radio hardware status changed to DISABLED
/var/log/messages.1:Jan 23 07:14:25 ubucomputer kernel: [   19.668239] b43legacy-phy0: Radio hardware status changed to DISABLED
==================================================================================================================
*** dmesg | grep -i radio | tail -n 5
==================================================================================================================
*** tail -n 300 /var/log/messages* | /bin/grep -i firmware | tail -n 5
==================================================================================================================
*** ls /lib/firmware/*
| 2.6.31-14-generic       | 2.6.31-17-generic       | acx                     | aic94xx-seq.fw           |
| ar9170-1.fw             | ar9170-2.fw             | ar9170.fw               | atmel_at76c502_3com.bin  |
| atmel_at76c502_3com-wpa.bin| atmel_at76c502.bin      | atmel_at76c502d.bin     | atmel_at76c502d-wpa.bin  |
| atmel_at76c502e.bin     | atmel_at76c502e-wpa.bin | atmel_at76c502-wpa.bin  | atmel_at76c503-i3861.bin |
| atmel_at76c503-i3863.bin| atmel_at76c503-rfmd-0.90.2-140.bin| atmel_at76c503-rfmd-acc.bin| atmel_at76c503-rfmd.bin  |
| atmel_at76c504_2958-wpa.bin| atmel_at76c504a_2958-wpa.bin| atmel_at76c504.bin      | atmel_at76c504c-wpa.bin  |
| atmel_at76c505a-rfmd2958.bin| atmel_at76c505-rfmd2958.bin| atmel_at76c505-rfmd.bin | atmel_at76c506.bin       |
| atmel_at76c506-wpa.bin  | b43legacy               | BCM2033-FW.bin          | BCM2033-MD.bin           |
| bcm43xx_initval01.fw    | bcm43xx_initval02.fw    | bcm43xx_initval03.fw    | bcm43xx_initval04.fw     |
| bcm43xx_initval05.fw    | bcm43xx_initval06.fw    | bcm43xx_initval07.fw    | bcm43xx_initval08.fw     |
| bcm43xx_initval09.fw    | bcm43xx_initval10.fw    | bcm43xx_microcode11.fw  | bcm43xx_microcode2.fw    |
| bcm43xx_microcode4.fw   | bcm43xx_microcode5.fw   | bcm43xx_pcm4.fw         | bcm43xx_pcm5.fw          |
| dvb-fe-xc5000-1.6.114.fw| dvb-usb-dib0700-1.20.fw | i2400m-fw-usb-1.3.sbcf  | i2400m-fw-usb-1.4.sbcf   |
| ipw2100-1.3.fw          | ipw2100-1.3-i.fw        | ipw2100-1.3-p.fw        | ipw2200-bss.fw           |
| ipw2200-ibss.fw         | ipw2200-sniffer.fw      | isl3877                 | isl3886pci               |
| isl3886usb              | isl3887usb              | isl3890                 | iwlwifi-1000-3.ucode     |
| iwlwifi-3945-1.ucode    | iwlwifi-3945-2.ucode    | iwlwifi-4965-1.ucode    | iwlwifi-4965-2.ucode     |
| iwlwifi-5000-1.ucode    | iwlwifi-5000-2.ucode    | iwlwifi-5150-2.ucode    | iwlwifi-6000-4.ucode     |
| lbtf_usb.bin            | NPE-B                   | NPE-B.01020201          | NPE-C                    |
| NPE-C.02020201          | ql2100_fw.bin           | ql2200_fw.bin           | ql2300_fw.bin            |
| ql2322_fw.bin           | ql2400_fw.bin           | rt2561.bin              | rt2561s.bin              |
| rt2661.bin              | rt2860.bin              | rt2870.bin              | rt73.bin                 |
| ucode11.fw              | ucode2.fw               | ucode4.fw               | ucode5.fw                |
| v4l-cx23418-apu.fw      | v4l-cx23418-cpu.fw      | v4l-cx23418-dig.fw      | v4l-cx2341x-dec.fw       |
| v4l-cx2341x-enc.fw      | v4l-cx2341x-init.mpg    | v4l-cx23885-avcore-01.fw| v4l-cx23885-enc.fw       |
| v4l-cx25840.fw          | v4l-pvrusb2-24xxx-01.fw | v4l-pvrusb2-29xxx-01.fw | zd1201-ap.fw             |
| zd1201.fw               | zd1211                  |
--- /lib/firmware
/lib/firmware/b43 not found
--- /lib/firmware
/lib/firmware/bc43legacy not found
==================================================================================================================
*** ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wmp11v27 : driver installed
	device (14E4:4301:1737:4301) present (alternate driver: ssb)
	device (14E4:4301) present (alternate driver: ssb)
==================================================================================================================
*** Active processes
wpa_supplicant:YES knetworkmanager:NO nm-applet:YES
==================================================================================================================
*** grep 'eth|ath|wlan|ra' /etc/udev/rules.d/*net_persistent* /etc/udev/rules.d/*persistent-net*
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
==================================================================================================================
*** grep -r 'eth[0-10]|ath[0-10]|wlan[0-10]|ra[0-10]' /etc/modprobe.*
/etc/modprobe.d/ndiswrapper:alias wlan0 ndiswrapper
==================================================================================================================
*** iwlist scanning
                    ESSID:"C#8#B#1#N#8#1#0#1#E#E#8"
                    Quality:57/100  Signal level:-59 dBm  Noise level:-96 dBm
                    Encryption key:on
                    ESSID:"J#Y#w#r#l#s#"
                    Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
                    Encryption key:on
                    ESSID:"S#d#-#e#w#r#"
                    Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
                    Encryption key:off
                    ESSID:"2#I#E#3#"
                    Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
                    Encryption key:on
                    ESSID:"2#I#E#8#"
                    Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
                    Encryption key:on
==================================================================================================================
*** NWElizaStates
IF:eth0 IM:1 IF:wlan0 IM:2 DI:2 AP:1 dI:0 NIC:0 cNiC:2:0 NI:0 cNI:0 PNG:1 DR:1 MTU:0 NISS:0 IP6:0 WLW:0 RTDT:debian 

```
[/FONT][/FONT]

---

### Post by lbjtemp on 2010-01-26
From /var/log/syslog I notice ....
Jan 26 08:32:13 ubucomputer kernel: [ 1331.615222] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 1 failed (00010003)
Jan 26 08:32:13 ubucomputer kernel: [ 1331.615229] ndiswrapper (remove_key:897): changing encr status failed (FFFFFFA1)
Jan 26 08:32:18 ubucomputer kernel: [ 1336.676556] ndiswrapper (iw_set_auth:1602): invalid cmd 12
Jan 26 08:32:18 ubucomputer kernel: [ 1336.676583] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 1 failed (00010003)
Jan 26 08:32:44 ubucomputer kernel: [ 1363.191008] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 1 failed (00010003)
Jan 26 08:33:14 ubucomputer kernel: [ 1393.292648] ndiswrapper (iw_set_auth:1602): invalid cmd 12
Jan 26 08:33:14 ubucomputer kernel: [ 1393.292674] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 0 failed (00010003)
Jan 26 08:33:38 ubucomputer kernel: [ 1416.992076] usb 2-1: USB disconnect, address 6
Jan 26 08:33:38 ubucomputer kernel: [ 1417.120058] usb 2-2: USB disconnect, address 7

---

### Post by chili555 on 2010-01-26
> address 192.168.1.1
netmask 255.255.255.0
gateway 98.155.16.1
I don't believe that gateway is going to allow a 192.168.x address. Are you behind a router? Isn't the router's address 192.168.1.1? Doesn't the router get the address from the outside world, in your case, RoadRunner?

Just guessing, I'd think this is more correct:```
address 192.168.1.115
netmask 255.255.255.0
gateway 192.168.1.1
```

---

### Post by bkratz on 2010-01-26
Sorry to interject, but there is a whole thread and a bug regarding this 

Jan 26 08:33:14 ubucomputer kernel: [ 1393.292648] ndiswrapper (iw_set_auth:1602): invalid cmd 12

Here is the bug listing
[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716)

I will find the thread and post that too.

---

### Post by bkratz on 2010-01-26
And here is the thread

[http://ubuntuforums.org/showthread.php?t=1343847&highlight=1602](http://ubuntuforums.org/showthread.php?t=1343847&highlight=1602)

---

### Post by lbjtemp on 2010-01-26
Thank you.

In thread listed and bug ... I could not find a solution ... or a procedure?  

Again, thank you for your help.

---

### Post by bkratz on 2010-01-26
First, I did do the procedure in step 1 ( first time I tried to compile) and it did get rid of the error message. Unfortunately, I was still unable to connect in 9.10. Some have reported success by adding the step found in post 7. That didn't work for me either. I did download and try the next LTS version (10.04) and my wireless went back to working with encryption. Since this is not a good solution I have reloaded 9.04 and will wait until the release candidate is completed (with eager anticipation!).

---

### Post by bkratz on 2010-01-26
Look all the way down to post 35 and on. It appears that the solution is going to a different kernel 2.6.32

I think I'll just wait though

---

### Post by lbjtemp on 2010-01-26
Thank you to all that helped me - I appreciate your help.

At the end, I ended regressing to 9.04 .. and with that release I am now able to use wireless in encrypted mode.

Again, thanks a million.

---

