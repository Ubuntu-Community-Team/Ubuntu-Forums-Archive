---
title: "Unable to connect with ndiswrapper and  bcm4318"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by frmontoya on 2009-05-15
I have been trying to connect my wireless for several days. I am using a HP Pavilion ze2000 with a broadcom 4318 wireless card. I tried just downloading the driver  (using System > Administration > Hardware Drivers)  this didn't work. I then tried the ndiswrapper and still cannot get my wireless started. Everthing seems to be inplace except that the connection fails. My guess is that I am not getting the key information for connection correct. I am getting this idea for the** SYSLOG** below. If this is the case, How do I correct this? Please let me know if there is something else I could try. Thank you. 

Below are my results:

Computer: HP Pavilion ze2000 
Wireless Card: Broadcom 4318

**$ lspci**
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
**05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)**
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller

**$ ndiswrapper -l**
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
[B]bcmwl5 : driver installed
    device (14E4:4318) present (alternate driver: ssb)[/B]


**$lshw -C Network**
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:c9:0d:55
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.72 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
      [B] product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation[/B]
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:13:24:d0
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical wireless
       **configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.54+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g**
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e6:e6:cc:0b:50:bc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

**$ dmesg | grep -e ndis -e wlan**
[   14.123486] ndiswrapper version 1.54 loaded (smp=yes, preempt=no)
[   14.164381] usbcore: registered new interface driver ndiswrapper
[   18.015377] usbcore: deregistering interface driver ndiswrapper
[   18.026769] ndiswrapper version 1.54 loaded (smp=yes, preempt=no)
[   18.091450] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   18.091738] ndiswrapper 0000:05:02.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   18.101144] ndiswrapper: using IRQ 20
[   18.308767] wlan0: ethernet device 00:14:a5:13:24:d0 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[   18.308858] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   18.308947] usbcore: registered new interface driver ndiswrapper
[   24.680469] ADDRCONF(NETDEV_UP): wlan0: link is not ready

**SYSLOG**
May 15 10:26:35 frmontoya-Ubuntu syslogd 1.5.0#5ubuntu3: restart.
May 15 10:26:35 frmontoya-Ubuntu anacron[2702]: Job `cron.daily' terminated
May 15 10:26:35 frmontoya-Ubuntu anacron[2702]: Normal exit (1 job run)
May 15 10:29:59 frmontoya-Ubuntu NetworkManager: <info>  Activation (wlan0) starting connection '2WIRE372' 
May 15 10:29:59 frmontoya-Ubuntu NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
May 15 10:29:59 frmontoya-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May 15 10:29:59 frmontoya-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May 15 10:29:59 frmontoya-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May 15 10:29:59 frmontoya-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May 15 10:29:59 frmontoya-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May 15 10:29:59 frmontoya-Ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
May 15 10:29:59 frmontoya-Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point '2WIRE372' has security, but secrets are required. 
May 15 10:29:59 frmontoya-Ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
May 15 10:29:59 frmontoya-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May 15 10:30:00 frmontoya-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May 15 10:30:00 frmontoya-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May 15 10:30:00 frmontoya-Ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
May 15 10:30:00 frmontoya-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May 15 10:30:00 frmontoya-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May 15 10:30:00 frmontoya-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May 15 10:30:00 frmontoya-Ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
May 15 10:30:00 frmontoya-Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): connection '2WIRE372' has security, and secrets exist.  No new secrets needed. 
May 15 10:30:00 frmontoya-Ubuntu NetworkManager: <info>  Config: added 'ssid' value '2WIRE372' 
May 15 10:30:00 frmontoya-Ubuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
**May 15 10:30:00 frmontoya-Ubuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' **
May 15 10:30:00 frmontoya-Ubuntu NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
May 15 10:30:00 frmontoya-Ubuntu NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
May 15 10:30:00 frmontoya-Ubuntu NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
**May 15 10:30:00 frmontoya-Ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed**
May 15 10:30:00 frmontoya-Ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 15 10:30:00 frmontoya-Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May 15 10:30:00 frmontoya-Ubuntu NetworkManager: <info>  Config: set interface ap_scan to 2 
May 15 10:30:00 frmontoya-Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected 
May 15 10:30:00 frmontoya-Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
May 15 10:30:00 frmontoya-Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
May 15 10:30:01 frmontoya-Ubuntu /USR/SBIN/CRON[5428]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May 15 10:30:14 frmontoya-Ubuntu NetworkManager: <info>  wlan0: link timed out. 
May 15 10:31:00 frmontoya-Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): association took too long. 
May 15 10:31:00 frmontoya-Ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
May 15 10:31:00 frmontoya-Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets 
May 15 10:31:00 frmontoya-Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected 
May 15 10:31:09 frmontoya-Ubuntu NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1539 (get_secrets_dialog_response_cb): canceled. 
May 15 10:31:09 frmontoya-Ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 9 
May 15 10:31:09 frmontoya-Ubuntu NetworkManager: <info>  Activation (wlan0) failed for access point (2WIRE372) 
May 15 10:31:09 frmontoya-Ubuntu NetworkManager: <info>  Marking connection '2WIRE372' invalid. 
May 15 10:31:09 frmontoya-Ubuntu NetworkManager: <info>  Activation (wlan0) failed. 
May 15 10:31:09 frmontoya-Ubuntu NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
May 15 10:31:09 frmontoya-Ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 0). sudo

---

### Post by j_hawker on 2009-05-15
Here is how i got my broadcom 4318 wireless to work (after a lot of tearing my hair out).

I started with a clean install of 9.04 (64 bit).

you will need two files

bcm43xx-fwcutter_006-3_amd64.deb (available in synaptic package manager)
hpsp33008.tar.gz  [http://fedoramobile.org/fc-wireless/hpsp33008.tar.gz/view](http://fedoramobile.org/fc-wireless/hpsp33008.tar.gz/view)

install bcm43xx-fwcutter_006-3_amd64 package

extract hpsp33008.tar.gz to desktop

open terminal

type
bcm43xx-fwcutter ~/Desktop/bcmwl5.sys

go into System -> Administration -> Hardware Drivers

Broadcom B43 wireless driver should be listed, enable it and you should be good

---

### Post by 73ckn797 on 2009-05-15
In Synaptic find "ndisgtk". If you have the Windows disk with the drivers you then copy those (likely for Windows XP) to a directory in Ubuntu. Run "ndisgtk" which after being installed will be under System/Administration at the bottom "Wireless Drivers". Install via that and see what happens. Make sure to uninstall the drivers you previousely installed before using this procedure.

See what happens.

---

