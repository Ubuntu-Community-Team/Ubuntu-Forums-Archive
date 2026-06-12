---
title: "Ubuntu 13.04 Can't connect to Wifi 5GHz Channel 40 (Lenovo T410s - Intel Ult. 6300)0"
date: 2013-05-22
forum: Networking &amp; Wireless
---

### Post by tux20 on 2013-05-22
Hello folks,

i hope you can help me.
Last week we got a new router from Motorola.
The Wifi is operating at 5Ghz on channel 40.

I am able to connect to the Wifi from the bad operating system (windows).
But since i perfer to use Ubuntu i need to make this work.

_The problem:_

I can't connect to the WLAN. I find it with iwlist wlan0 scan (and ofc Network Manager does it as well).. but it is unlucky when it tries to connect.
This is my hardware: [http://www.thinkwiki.org/wiki/Intel_Centrino_Ultimate-N_6300](http://www.thinkwiki.org/wiki/Intel_Centrino_Ultimate-N_6300)

iwlist chan shows that the Frequency is available (5.2 Ghz)
I also tried it with an old 3.5 kernel.. same problem.
I tried it via adhoc mode.. same problem.
I cleaned the conf files of NM.. same problem

Now i have no idea left, but it seems more to be a problem with the dns or dhcp according to the log

Here is the log of my last try to connect:

```

May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) starting connection 'NELLIS01'
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0/wireless): access point 'NELLIS01' has security, but secrets are required.
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0/wireless): connection 'NELLIS01' has security, and secrets exist.  No new secrets needed.
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Config: added 'ssid' value 'NELLIS01'
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Config: added 'scan_ssid' value '1'
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Config: added 'auth_alg' value 'OPEN'
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Config: added 'psk' value '<omitted>'
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> Config: set interface ap_scan to 1
May 22 19:34:04 T410s-ubuntu NetworkManager[1173]: <info> (wlan0): supplicant interface state: disconnected -> scanning
May 22 19:34:06 T410s-ubuntu wpa_supplicant[1887]: wlan0: SME: Trying to authenticate with 20:10:7a:91:0c:28 (SSID='NELLIS01' freq=5200 MHz)
May 22 19:34:06 T410s-ubuntu kernel: [ 2102.570928] wlan0: authenticate with 20:10:7a:91:0c:28
May 22 19:34:06 T410s-ubuntu kernel: [ 2102.594008] wlan0: send auth to 20:10:7a:91:0c:28 (try 1/3)
May 22 19:34:06 T410s-ubuntu NetworkManager[1173]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May 22 19:34:06 T410s-ubuntu wpa_supplicant[1887]: wlan0: Trying to associate with 20:10:7a:91:0c:28 (SSID='NELLIS01' freq=5200 MHz)
May 22 19:34:06 T410s-ubuntu kernel: [ 2102.597473] wlan0: authenticated
May 22 19:34:06 T410s-ubuntu kernel: [ 2102.598654] wlan0: associate with 20:10:7a:91:0c:28 (try 1/3)
May 22 19:34:06 T410s-ubuntu kernel: [ 2102.599546] wlan0: RX AssocResp from 20:10:7a:91:0c:28 (capab=0x11 status=0 aid=3)
May 22 19:34:06 T410s-ubuntu NetworkManager[1173]: <info> (wlan0): supplicant interface state: authenticating -> associating
May 22 19:34:06 T410s-ubuntu wpa_supplicant[1887]: wlan0: Associated with 20:10:7a:91:0c:28
May 22 19:34:06 T410s-ubuntu kernel: [ 2102.603986] wlan0: associated
May 22 19:34:06 T410s-ubuntu NetworkManager[1173]: <info> (wlan0): supplicant interface state: associating -> associated
May 22 19:34:06 T410s-ubuntu NetworkManager[1173]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
May 22 19:34:06 T410s-ubuntu wpa_supplicant[1887]: wlan0: WPA: Key negotiation completed with 20:10:7a:91:0c:28 [PTK=CCMP GTK=TKIP]
May 22 19:34:06 T410s-ubuntu wpa_supplicant[1887]: wlan0: CTRL-EVENT-CONNECTED - Connection to 20:10:7a:91:0c:28 completed (reauth) [id=0 id_str=]
May 22 19:34:06 T410s-ubuntu NetworkManager[1173]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
May 22 19:34:06 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'NELLIS01'.
May 22 19:34:06 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
May 22 19:34:06 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
May 22 19:34:06 T410s-ubuntu NetworkManager[1173]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
May 22 19:34:06 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 22 19:34:06 T410s-ubuntu NetworkManager[1173]: <info> dhclient started with pid 3706
May 22 19:34:06 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Beginning IP6 addrconf.
May 22 19:34:06 T410s-ubuntu avahi-daemon[1184]: Withdrawing address record for fe80::224:d7ff:fe05:35b8 on wlan0.
May 22 19:34:06 T410s-ubuntu acvpnagent[1592]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1681 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
May 22 19:34:06 T410s-ubuntu avahi-daemon[1184]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::224:d7ff:fe05:35b8.
May 22 19:34:06 T410s-ubuntu avahi-daemon[1184]: Interface wlan0.IPv6 no longer relevant for mDNS.
May 22 19:34:06 T410s-ubuntu acvpnagent[1592]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1681 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
May 22 19:34:06 T410s-ubuntu acvpnagent[1592]: A new network interface has been detected.
May 22 19:34:06 T410s-ubuntu acvpnagent[1592]: Function: logInterfaces File: RouteMgr.cpp Line: 2063 Invoked Function: logInterfaces Return Code: 0 (0x00000000) Description: IP Address Interface List: FE80:0:0:0:224:D7FF:FE05:35B8  
May 22 19:34:06 T410s-ubuntu acvpnagent[1592]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1681 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
May 22 19:34:06 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
May 22 19:34:06 T410s-ubuntu dhclient: Internet Systems Consortium DHCP Client 4.2.4
May 22 19:34:06 T410s-ubuntu dhclient: Copyright 2004-2012 Internet Systems Consortium.
May 22 19:34:06 T410s-ubuntu dhclient: All rights reserved.
May 22 19:34:06 T410s-ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
May 22 19:34:06 T410s-ubuntu dhclient: 
May 22 19:34:07 T410s-ubuntu dhclient: Listening on LPF/wlan0/00:24:d7:05:35:b8
May 22 19:34:07 T410s-ubuntu dhclient: Sending on   LPF/wlan0/00:24:d7:05:35:b8
May 22 19:34:07 T410s-ubuntu dhclient: Sending on   Socket/fallback
May 22 19:34:07 T410s-ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x7cb3ce4c)
May 22 19:34:07 T410s-ubuntu NetworkManager[1173]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
May 22 19:34:08 T410s-ubuntu avahi-daemon[1184]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::224:d7ff:fe05:35b8.
May 22 19:34:08 T410s-ubuntu acvpnagent[1592]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1681 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
May 22 19:34:08 T410s-ubuntu avahi-daemon[1184]: New relevant interface wlan0.IPv6 for mDNS.
May 22 19:34:08 T410s-ubuntu avahi-daemon[1184]: Registering new address record for fe80::224:d7ff:fe05:35b8 on wlan0.*.
May 22 19:34:08 T410s-ubuntu acvpnagent[1592]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1681 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
May 22 19:34:09 T410s-ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5 (xid=0x7cb3ce4c)
May 22 19:34:14 T410s-ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x7cb3ce4c)
May 22 19:34:26 T410s-ubuntu NetworkManager[1173]: <info> (wlan0): IP6 addrconf timed out or failed.
May 22 19:34:26 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May 22 19:34:26 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May 22 19:34:26 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May 22 19:34:27 T410s-ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20 (xid=0x7cb3ce4c)
May 22 19:34:47 T410s-ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20 (xid=0x7cb3ce4c)
May 22 19:34:51 T410s-ubuntu NetworkManager[1173]: <warn> (wlan0): DHCPv4 request timed out.
May 22 19:34:52 T410s-ubuntu NetworkManager[1173]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 3706
May 22 19:34:52 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
May 22 19:34:52 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
May 22 19:34:52 T410s-ubuntu NetworkManager[1173]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
May 22 19:34:52 T410s-ubuntu NetworkManager[1173]: <info> Marking connection 'NELLIS01' invalid.
May 22 19:34:52 T410s-ubuntu NetworkManager[1173]: <warn> Activation (wlan0) failed for connection 'NELLIS01'
May 22 19:34:52 T410s-ubuntu NetworkManager[1173]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
May 22 19:34:52 T410s-ubuntu NetworkManager[1173]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 22 19:34:52 T410s-ubuntu NetworkManager[1173]: <info> (wlan0): deactivating device (reason 'none') [0]
May 22 19:34:52 T410s-ubuntu avahi-daemon[1184]: Withdrawing address record for fe80::224:d7ff:fe05:35b8 on wlan0.
May 22 19:34:52 T410s-ubuntu avahi-daemon[1184]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::224:d7ff:fe05:35b8.
May 22 19:34:52 T410s-ubuntu avahi-daemon[1184]: Interface wlan0.IPv6 no longer relevant for mDNS.
May 22 19:34:52 T410s-ubuntu acvpnagent[1592]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1681 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
May 22 19:34:52 T410s-ubuntu kernel: [ 2147.674913] wlan0: deauthenticating from 20:10:7a:91:0c:28 by local choice (reason=3)
May 22 19:34:52 T410s-ubuntu acvpnagent[1592]: A network interface has gone down.
May 22 19:34:52 T410s-ubuntu acvpnagent[1592]: Function: logInterfaces File: RouteMgr.cpp Line: 2063 Invoked Function: logInterfaces Return Code: 0 (0x00000000) Description: IP Address Interface List:  
May 22 19:34:52 T410s-ubuntu NetworkManager[1173]: <info> (wlan0): supplicant interface state: completed -> disconnected
May 22 19:34:52 T410s-ubuntu kernel: [ 2147.710475] cfg80211: Calling CRDA to update world regulatory domain
May 22 19:34:52 T410s-ubuntu wpa_supplicant[1887]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
May 22 19:34:52 T410s-ubuntu kernel: [ 2147.724109] cfg80211: World regulatory domain updated:
May 22 19:34:52 T410s-ubuntu kernel: [ 2147.724115] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 22 19:34:52 T410s-ubuntu kernel: [ 2147.724118] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 22 19:34:52 T410s-ubuntu kernel: [ 2147.724119] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 22 19:34:52 T410s-ubuntu kernel: [ 2147.724121] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 22 19:34:52 T410s-ubuntu kernel: [ 2147.724123] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 22 19:34:52 T410s-ubuntu kernel: [ 2147.724125] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 22 19:34:52 T410s-ubuntu kernel: [ 2147.724586] cfg80211: Calling CRDA for country: US
May 22 19:34:52 T410s-ubuntu kernel: [ 2147.730399] cfg80211: Regulatory domain changed to country: US
May 22 19:34:52 T410s-ubuntu kernel: [ 2147.730405] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 22 19:34:52 T410s-ubuntu kernel: [ 2147.730408] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
May 22 19:34:52 T410s-ubuntu kernel: [ 2147.730410] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
May 22 19:34:52 T410s-ubuntu kernel: [ 2147.730412] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 22 19:34:52 T410s-ubuntu kernel: [ 2147.730414] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 22 19:34:52 T410s-ubuntu kernel: [ 2147.730417] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 22 19:34:52 T410s-ubuntu kernel: [ 2147.730418] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109297] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109305] iwlwifi 0000:03:00.0: CSR values:
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109308] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109315] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X0048d304
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109341] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X0000ff40
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109366] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109392] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109417] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109443] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X0000000f
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109468] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109493] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109518] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X00000074
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109544] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X99f00ffd
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109569] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109594] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X00030401
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109620] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080042
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109645] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00004e25
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109670] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109695] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109721] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109745] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000058
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109771] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X8812f8cd
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109796] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109822] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109847] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109872] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109875] iwlwifi 0000:03:00.0: FH register values:
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109913] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X12ed1600
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109949] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X012e8af0
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.109985] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000b8
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110021] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80811114
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110057] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110092] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110128] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110164] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110200] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110206] iwlwifi 0000:03:00.0: Loaded firmware version: 9.221.4.1 build 25532
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110354] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110358] iwlwifi 0000:03:00.0: Status: 0x000022CC, count: 5
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110361] iwlwifi 0000:03:00.0: 0x00000005 | SYSASSERT                   
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110364] iwlwifi 0000:03:00.0: 0x000222EC | uPc
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110367] iwlwifi 0000:03:00.0: 0x00022258 | branchlink1
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110370] iwlwifi 0000:03:00.0: 0x00022258 | branchlink2
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110373] iwlwifi 0000:03:00.0: 0x00001532 | interruptlink1
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110375] iwlwifi 0000:03:00.0: 0x00000000 | interruptlink2
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110378] iwlwifi 0000:03:00.0: 0x00000078 | data1
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110381] iwlwifi 0000:03:00.0: 0x00000031 | data2
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110384] iwlwifi 0000:03:00.0: 0x00000237 | line
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110387] iwlwifi 0000:03:00.0: 0x00C05F92 | beacon time
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110389] iwlwifi 0000:03:00.0: 0x0005E06E | tsf low
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110392] iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110395] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110398] iwlwifi 0000:03:00.0: 0x0497CA2E | time gp2
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110400] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110403] iwlwifi 0000:03:00.0: 0x000109DD | uCode version
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110406] iwlwifi 0000:03:00.0: 0x00000074 | hw version
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110409] iwlwifi 0000:03:00.0: 0x0048D304 | board version
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110411] iwlwifi 0000:03:00.0: 0x049F0080 | hcmd
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110414] iwlwifi 0000:03:00.0: 0x00022080 | isr0
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110417] iwlwifi 0000:03:00.0: 0x0103E000 | isr1
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110420] iwlwifi 0000:03:00.0: 0x00000017 | isr2
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110423] iwlwifi 0000:03:00.0: 0x0141FCC0 | isr3
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110425] iwlwifi 0000:03:00.0: 0x00000000 | isr4
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110428] iwlwifi 0000:03:00.0: 0x01000112 | isr_pref
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110431] iwlwifi 0000:03:00.0: 0x0001536C | wait_event
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110434] iwlwifi 0000:03:00.0: 0x00000080 | l2p_control
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110437] iwlwifi 0000:03:00.0: 0x00000000 | l2p_duration
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110439] iwlwifi 0000:03:00.0: 0x0000003F | l2p_mhvalid
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110442] iwlwifi 0000:03:00.0: 0x00200200 | l2p_addr_match
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110445] iwlwifi 0000:03:00.0: 0x00000005 | lmpm_pmg_sel
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110448] iwlwifi 0000:03:00.0: 0x02061043 | timestamp
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110451] iwlwifi 0000:03:00.0: 0x0000B8C0 | flow_handler
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110530] iwlwifi 0000:03:00.0: Log capacity 1024 is bogus, limit to 512 entries
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110533] iwlwifi 0000:03:00.0: Start IWL Event Log Dump: display last 20 entries
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110574] iwlwifi 0000:03:00.0: EVT_LOGT:0077054530:0x01489000:1334
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110606] iwlwifi 0000:03:00.0: EVT_LOGT:0077054535:0x001e0000:1334
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110638] iwlwifi 0000:03:00.0: EVT_LOGT:0077054538:0x00000052:1334
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110670] iwlwifi 0000:03:00.0: EVT_LOGT:0077054539:0x01489000:1334
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110702] iwlwifi 0000:03:00.0: EVT_LOGT:0077054540:0x00000018:0484
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110734] iwlwifi 0000:03:00.0: EVT_LOGT:0077054553:0x00000019:0484
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110765] iwlwifi 0000:03:00.0: EVT_LOGT:0077054567:0x00000259:1108
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110797] iwlwifi 0000:03:00.0: EVT_LOGT:0077054567:0x00000024:1108
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110829] iwlwifi 0000:03:00.0: EVT_LOGT:0077054568:0x00000001:1108
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110860] iwlwifi 0000:03:00.0: EVT_LOGT:0077054568:0x00000033:1108
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110892] iwlwifi 0000:03:00.0: EVT_LOGT:0077054573:0x00000028:0460
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110924] iwlwifi 0000:03:00.0: EVT_LOGT:0077054575:0x00000028:0462
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110956] iwlwifi 0000:03:00.0: EVT_LOGT:0077054601:0x00000001:1575
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.110987] iwlwifi 0000:03:00.0: EVT_LOGT:0077056298:0x000001b4:0602
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.111019] iwlwifi 0000:03:00.0: EVT_LOGT:0077056301:0x000000df:0002
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.111051] iwlwifi 0000:03:00.0: EVT_LOGT:0077056511:0x049f0080:0401
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.111083] iwlwifi 0000:03:00.0: EVT_LOGT:0077056512:0x049f0080:0700
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.111114] iwlwifi 0000:03:00.0: EVT_LOGT:0077056513:0x00000000:0706
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.111147] iwlwifi 0000:03:00.0: EVT_LOGT:0077056541:0x00000018:0452
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.111178] iwlwifi 0000:03:00.0: EVT_LOGT:0077056581:0x00000000:0125
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.111217] iwlwifi 0000:03:00.0: FW error in SYNC CMD REPLY_SCAN_CMD
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.111624] ieee80211 phy0: Hardware restart was requested
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.112124] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
May 22 19:34:52 T410s-ubuntu kernel: [ 2148.118953] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
May 22 19:34:53 T410s-ubuntu acvpnagent[1592]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1681 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
May 22 19:34:53 T410s-ubuntu avahi-daemon[1184]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::224:d7ff:fe05:35b8.
May 22 19:34:53 T410s-ubuntu avahi-daemon[1184]: New relevant interface wlan0.IPv6 for mDNS.
May 22 19:34:53 T410s-ubuntu avahi-daemon[1184]: Registering new address record for fe80::224:d7ff:fe05:35b8 on wlan0.*.
May 22 19:34:53 T410s-ubuntu acvpnagent[1592]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1681 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
May 22 19:35:01 T410s-ubuntu CRON[3725]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)

```

Thanks in advance :D

---

