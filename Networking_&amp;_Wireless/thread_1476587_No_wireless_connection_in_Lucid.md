---
title: "No wireless connection in Lucid"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by fallenwattle on 2010-05-08
I have a Dell Studio XPS desktop too difficult to reach with cable. Instead I connect through a Dell Wireless 1500 Draft 802.11n WLAN Mini-card which works great with 64 bit Windows 7.

Installed Ubuntu 10.4 yesterday (wubi) but no wireless activity! Despite Googling extensively and reading through Ubuntu Forums I've not been able to find a solution so far.

Can anyone assist? ](*,)

---

### Post by pdc on 2010-05-08
[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English)

this a diagnostic script for wireless; used a lot on the OpenSuse forum;

download it and run it

diagnoses; makes suggestions; if not enough, post all the results back here for further help

---

### Post by fallenwattle on 2010-05-08
Thanks pdc... I downloaded the script in Win7 then rebooted into Ubuntu and ran it. Here's the result:

--- Which type of your network connection should be tested?
--- (2) Wireless connection (WLAN)
--- What's the type of networktopology?
--- (1) WLAN access point <---> LinuxClient
--- On which host is the script executed?
--- (1) LinuxClient
--- WLAN SSID to connect to: s#g#r#y#n#t#o#k

--- NWEliza is analyzing the system for common network configuration errors ...

!!! CND0110E: For the selected connection type there was no active network interface found on your system
!!! CND0450W: WLAN key masquerading is not fully tested on this distribution. Please check output file collectNWData.txt for visible WLAN keys and masquerade them manually

--- Go to [http://www.linux-tips-and-tricks.de/CND#English](http://www.linux-tips-and-tricks.de/CND#English) to get more detailed instructions 
--- about the error/warning messages and how to fix the problems on your own.

--- If you are unsuccessful then place the contents of file collectNWData.txt in the net
--- (see [http://www.linux-tips-and-tricks.de/CND_UPL#English](http://www.linux-tips-and-tricks.de/CND_UPL#English) for links) 
--- and then paste the nopaste link on your favorite Linux forum.

==================================================================================================================
==================================================================================================================
*** uname -a
Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
==================================================================================================================
*** cat /etc/*[-_]release || cat /etc/*[-_]version
/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
==================================================================================================================
*** cat /etc/resolv | grep -i "nameserver"
cat: /etc/resolv.conf: No such file or directory
==================================================================================================================
*** cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	ubuntu.ubuntu-domain	ubuntu
==================================================================================================================
*** route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
==================================================================================================================
*** ifconfig
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:#1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fb8c0000-fb8e0000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7768 (7.7 KB)  TX bytes:7768 (7.7 KB)
==================================================================================================================
*** ping tests
connect: Network is unreachable
Ping of 195.135.220.3 failed
ping: unknown host [www.suse.de](www.suse.de)
Ping of [www.suse.de](www.suse.de) failed
==================================================================================================================
*** lspci
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LF-2 Gigabit Network Connection [8086:10cd]
02:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
==================================================================================================================
*** lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 046d:c719 Logitech, Inc. 
Bus 004 Device 004: ID 046d:c718 Logitech, Inc. 
Bus 004 Device 003: ID 413c:8130 Dell Computer Corp. 
Bus 004 Device 002: ID 046d:0b05 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 008: ID 04ca:0027 Lite-On Technology Corp. 
Bus 002 Device 007: ID 046d:c063 Logitech, Inc. 
Bus 002 Device 006: ID 056a:0016 Wacom Co., Ltd 
Bus 002 Device 005: ID 046d:08c5 Logitech, Inc. QuickCam Pro 5000
Bus 002 Device 004: ID 04b4:9393 Cypress Semiconductor Corp. 
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0c76:0005 JMTek, LLC. Transcend Flash disk
Bus 001 Device 004: ID 1058:0705 Western Digital Technologies, Inc. 
Bus 001 Device 003: ID 0644:0201 TEAC Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
==================================================================================================================
*** lsmod # (filtered)
| binfmt_misc     | bitblit         | bluetooth       | bnep            | bridge           |
| btcx_risc       | btusb           | cx2341x         | cx23885         | dcdbas           |
| dell_wmi        | drm             | drm_kms_helper  | dvb_core        | e1000e           |
| fat             | fbcon           | font            | hid             | i2c_algo_bit     |
| ieee1394        | l2cap           | lp              | nls_cp437       | nls_iso8859_1    |
| ohci1394        | ppdev           | radeon          | rfcomm          | sco              |
| serio_raw       | snd_hda_codec   | snd_hda_codec_atihdmi| snd_hda_codec_realtek| snd_hda_intel    |
| snd_hwdep       | snd_rawmidi     | snd_seq_device  | snd_seq_dummy   | snd_seq_midi     |
| snd_seq_oss     | snd_usb_audio   | snd_usb_lib     | softcursor      | ssb              |
| stp             | tda10048        | tda18271        | tda8290         | tileblit         |
| ttm             | tveeprom        | usb_storage     | uvcvideo        | v4l1_compat      |
| v4l2_common     | v4l2_compat_ioctl32| vfat            | vga16fb         | vgastate         |
| videobuf_dma_sg | videobuf_dvb    | wacom           |
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
==================================================================================================================
*** Actual date for bias of following greps
14:58:14 2010-05-08
==================================================================================================================
*** grep -i radio /var/log/messages* | tail -n 5
May  7 07:39:00 ubuntu kernel: [    7.677918] tveeprom 0-0050: has no radio
May  7 08:38:03 ubuntu kernel: [   11.040543] tveeprom 2-0050: has no radio
May  8 14:42:28 ubuntu kernel: [   11.349758] tveeprom 2-0050: has no radio
==================================================================================================================
*** dmesg | grep -i radio | tail -n 5
[   11.349758] tveeprom 2-0050: has no radio
==================================================================================================================
*** tail -n 300 /var/log/messages* | /bin/grep -i firmware | tail -n 5
May  8 14:42:28 ubuntu kernel: [   11.175660] platform radeon_cp.0: firmware: requesting radeon/RV770_pfp.bin
May  8 14:42:28 ubuntu kernel: [   11.176892] platform radeon_cp.0: firmware: requesting radeon/RV770_me.bin
May  8 14:42:28 ubuntu kernel: [   11.178718] platform radeon_cp.0: firmware: requesting radeon/R700_rlc.bin
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
==================================================================================================================
*** grep -r 'eth[0-10]|ath[0-10]|wlan[0-10]|ra[0-10]' /etc/modprobe.*
==================================================================================================================
*** iwlist scanning
No WLANs found
==================================================================================================================
*** NWElizaStates
IF:eth0 IM:1 DI:1 AP:0 FALON:0 
[/code]

---

### Post by pdc on 2010-05-08
from here

> Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)

it seems you have the BCM4328

from here

[http://www.bluebottle.net.au/blog/2009/broadcom-bcm4328-on-ubuntu-904-jaunty](http://www.bluebottle.net.au/blog/2009/broadcom-bcm4328-on-ubuntu-904-jaunty)

and earlier posts

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

ubuntu appears to use the b43 method

described here

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

have a read at this

B43 is described

On OpenSuse they talk of using the broadcom wl-driver

.. so it appears to be the B43 you need, but you may wish to wait for a wireless expert to confirm this for you

I do note in the script that it says

> /lib/firmware/b43 not found so that seems to confirm the b43 is needed theory

(and if you google yourself on ubuntu Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03) yourself

---

### Post by bkratz on 2010-05-08
Not an expert by any means, but did a little "google-ing" and found the following links

This link
[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices) 
 says that b43 does not support that particular pci-id [14e4:4328].

This link
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

If you  look at the readme file says that it is supported by the STA driver (wl).

"4321 Dualband	    0x14e4	0x4328  	Dell 1500"

---

### Post by pdc on 2010-05-08
thanks bkratz very much for this; the use of the wl on suse (which is packaged as rpm on suse) made me feel the sta was the correct one, and the earlier ubuntu threads with b43 was in conflict with this;

it seems reasonable now fallenwattle to suggest you look at this thread

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

on how to install the sta driver;

with the usual reminder that linux is for adults, and its your system, and folks on the forum offer suggestions and do their best to assist ... and it is use puts software on your own system ..

---

### Post by fallenwattle on 2010-05-09
Many thanks for your help guys... I'm drawing a blank here. Tried your suggestions and still no joy. The adapter won't activate. Have ordered some cat6 cable and will test the wired connection when it arrives. If that works I feel I'll have a better chance of firing up the wireless. At the moment, with no internet link in Ubuntu, I'm constantly having to reboot into Win7 and back again - very time-consuming and frustrating. I'm very grateful for your interest...

---

