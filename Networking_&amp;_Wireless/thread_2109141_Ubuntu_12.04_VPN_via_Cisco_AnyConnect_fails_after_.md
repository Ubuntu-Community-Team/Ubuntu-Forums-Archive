---
title: "Ubuntu 12.04 VPN via Cisco AnyConnect fails after 2 minutes"
date: 2013-01-26
forum: Networking &amp; Wireless
---

### Post by jose madre on 2013-01-26
My employer is converting VPN access from Nortel VPN to Cisco AnyConnect. After installing the app, it launches and connects to the corporate network with no problem.

However, the connection consistently fails after ~2 minutes.

No error message is displayed, the status line in the gui simply changes from "connected" to reconnecting.

Even though the gui says "reconnecting" a new connection is not made. To re-connect, I must click on the "disconnect" button on the gui and repeat the connection sequence. 

Details:
[INDENT]ubuntu version: 12.04.1 LTS (64bit)
AnyConnect version: 3.1.00495
laptop: Toshiba Portege R935 P326
[/INDENT]

Previous VPN interface (using VPNC) worked fine - no issues with a dropped connection. Corporate IT helpdesk says "Linux is not supported - try it, but you are on your own". 

Thank you in advance for any troubleshooting or solution help.

jmr

---

### Post by jose madre on 2013-02-22
Ok - more troubleshooting results:

1 - upgrading to 12.10 (clean reload) did not help. I still see the same results.

2 - When connected via a wired connection, the connection is long lived and stable. No issues dropping the connection.

3 - switching wireless routers (Amped Wireless R10000G or linksys WRT54G) did not change the behavior.  Connection is still lost after ~2 minutes.

interface details:


```
lspci -v

04:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
	Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at e2400000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi

```

```
dmesg | grep iwl

[   14.343704] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   14.343707] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[   14.343808] iwlwifi 0000:04:00.0: pci_resource_len = 0x00002000
[   14.343811] iwlwifi 0000:04:00.0: pci_resource_base = ffffc900050b8000
[   14.343813] iwlwifi 0000:04:00.0: HW Revision ID = 0xC4
[   14.343946] iwlwifi 0000:04:00.0: irq 45 for MSI/MSI-X
[   14.351645] iwlwifi 0000:04:00.0: loaded firmware version 18.168.6.1
[   14.351934] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   14.351938] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   14.351940] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   14.351942] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   14.351944] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_P2P disabled
[   14.351947] iwlwifi 0000:04:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[   14.352064] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   14.359424] iwlwifi 0000:04:00.0: RF_KILL bit toggled to enable radio.
[   14.370681] iwlwifi 0000:04:00.0: device EEPROM VER=0x81c, CALIB=0x6
[   14.370687] iwlwifi 0000:04:00.0: Device SKU: 0x150
[   14.370690] iwlwifi 0000:04:00.0: Valid Tx ant: 0x3, Valid Rx ant: 0x3
[   14.370710] iwlwifi 0000:04:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   15.071802] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   15.078044] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   15.085426] iwlwifi 0000:04:00.0: Radio type=0x2-0x0-0x0
[   15.350193] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   15.357660] iwlwifi 0000:04:00.0: Radio type=0x2-0x0-0x0

```

```
rfkill list all

0: Toshiba Bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

```
iwconfig

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"montevelino"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: *:*:*:*:*   
          Bit Rate=150 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:12786  Invalid misc:165   Missed beacon:0


```

```
 locate 2030-6.ucode

/lib/firmware/iwlwifi-2030-6.ucode

```

Any additional pointers fr troubleshooting or solutions is greatly appreciated.

thanks - jmr

---

### Post by galfly on 2013-03-12
Hi Jose,

What do you see when you run

tail /var/log/syslog

---

### Post by jose madre on 2013-03-13
Galfly;

Here are the results of 

```

sudo tail /var/log/syslog

Mar 13 04:45:46 jo-mama-laptop acvpnagent[1079]: Function: OnTimerExpired File: ../../vpn/Common/IPC/SocketTransport.cpp Line: 1655 Invoked Function: CSocketTransport::postConnectProcessing Return Code: -31588316 (0xFE1E0024) Description: SOCKETTRANSPORT_ERROR_CONNECT_TIMEOUT 

Mar 13 04:45:50 jo-mama-laptop acvpnagent[1079]: Function: STLoadLibrary File: ../../vpn/Common/Utility/Win/HModuleMgr.cpp Line: 149 Invoked Function: dlopen Return Code: 0 (0x00000000) Description: libz.so: cannot open shared object file: No such file or directory 

Mar 13 04:45:50 jo-mama-laptop acvpnagent[1079]: Function: LoadLibrary File: ../../vpn/Agent/CZLib.cpp Line: 242 Invoked Function: CHModuleMgr::STLoadLibrary Return Code: -33554425 (0xFE000007) Description: GLOBAL_ERROR_NOT_INITIALIZED 

Mar 13 04:45:50 jo-mama-laptop acvpnagent[1079]: Function: CCstpProtocol File: ../../vpn/Agent/CstpProtocol.cpp Line: 309 Invoked Function: CZLib Return Code: -31981557 (0xFE18000B) Description: CZLIB_ERROR_LOAD_LIBRARY 

Mar 13 04:45:50 jo-mama-laptop acvpnagent[1079]: Function: STLoadLibrary File: ../../vpn/Common/Utility/Win/HModuleMgr.cpp Line: 149 Invoked Function: dlopen Return Code: 0 (0x00000000) Description: /usr/lib/firefox/libnss3.so: wrong ELF class: ELFCLASS64 

Mar 13 04:45:50 jo-mama-laptop acvpnagent[1079]: Function: loadLibs File: ../../vpn/CommonCrypt/Certificates/NSSCertUtils.cpp Line: 1422 Invoked Function: CHModuleMgr::STLoadLibrary Return Code: -33554425 (0xFE000007) Description: GLOBAL_ERROR_NOT_INITIALIZED Could not load: /usr/lib/firefox/libnss3.so

Mar 13 04:45:50 jo-mama-laptop acvpnagent[1079]: Function: CNSSCertUtils File: ../../vpn/CommonCrypt/Certificates/NSSCertUtils.cpp Line: 305 Invoked Function: CNSSCertUtils::loadLibs Return Code: -33554425 (0xFE000007) Description: GLOBAL_ERROR_NOT_INITIALIZED 

Mar 13 04:45:50 jo-mama-laptop acvpnagent[1079]: Function: CNSSCertStore File: ../../vpn/CommonCrypt/Certificates/NSSCertStore.cpp Line: 57 Invoked Function: CNSSCertUtils Return Code: -33554425 (0xFE000007) Description: GLOBAL_ERROR_NOT_INITIALIZED 

Mar 13 04:45:50 jo-mama-laptop acvpnagent[1079]: Function: addNSSStore File: ../../vpn/CommonCrypt/Certificates/CollectiveCertStore.cpp Line: 1722 Invoked Function: CNSSCertStore::CNSSCertStore Return Code: -33554425 (0xFE000007) Description: GLOBAL_ERROR_NOT_INITIALIZED 

Mar 13 04:45:50 jo-mama-laptop acvpnagent[1079]: Function: OpenStores File: ../../vpn/CommonCrypt/Certificates/CollectiveCertStore.cpp Line: 415 Invoked Function: CCollectiveCertStore::addNSSStore Return Code: -33554425 (0xFE000007) Description: GLOBAL_ERROR_NOT_INITIALIZED

```

I have looked for the file:
[INDENT]/usr/lib/firefox/libnss3.so[/INDENT]
and it is present. I have also tried:
1 - completely remove the AnyConnect Software
2 - install the 32 bit librarires (sudo apt-get install ia32-libs)
3 - re-install the AnyConnect software

still no change in behavior.

thanks - jmr

---

### Post by jose madre on 2013-05-07
OK - more information on this problem:

I visited my brother in-law over the weekend and tried to use his wireless to connect via VPN to my corp network. It worked - no problems keeping the connection active, and the connection was repeatable. Not just a one time fluke. The WIFI I connected to was completely open - no security, encryption or MAC address filtering. I was on to a good solid clue...

When I returned home, I confidently reset my WIFI to mimic the settings that worked - no security, SSID broadcast on, no encryption, no MAC address filtering. This did not fix my issue - the VPN connection still dies after ~ 2 minutes.

I pulled out the old Linksys router and duplicated the setup - no security, SSID broadcast on, no encryption, no MAC address filtering. Still no joy - VPN dies after ~ 2 minutes.

My next steps are to try a different cable modem, then troubleshooting with my ISP.

Any better ideas out there - let me know as I would love to fix this issue.

thanks in advance - jmr

---

### Post by oiad on 2013-06-23
The problem is probably due to a conflicting route being obtained from the ASA.  When connected to the VPN look at the routing table and see if there are 192 routes being obtained for your vpn virtual adapter.  I assume there is.  It probably worked at your brothers house because of the IPs he is using.  

Try setting your home router to an IP that is not common, so not 172.*, 10.*, and especially not 192.* then try to connect.

---

### Post by philip14 on 2013-09-19
Am I correct in guessing this did not solve your problem? When I search for this same issue I'm having using only error codes, I come up with a thread about the same distribution of Linux I'm having the problem with. This tells me it is Distro-Specific to a certain degree perhaps? Further research about this issue reveals information about dead peer and ssl keepalive configurations on the ASA side. My error is "SOCKETTRANSPORT_ERROR_CONNECT_TIMEOUT" which i'm guessing is either related to the IPV6 route being removed when ASA connects or due to the "Processing CSTL header           line: 'X-DTLS-Accept-Encoding: lzs'" directive which is missing the libz.so file on my box, and apparently also on yours. 

I'm wondering if the tunnel is unable to establish because of a secure handshake being incomplete, and it says peer is dead and reconnects. It is worth trying that tomorrow.

---

### Post by jose madre on 2013-10-15
This has been solved by updating my Anyconnect client to the latest 64bit version from Cisco.

the *anyconnect-linux-64-3.1.04066-k9.pkg * version installed without trouble and has worked with no issues in connecting to my employers VPN server.

Thanks to all for your troubleshooting assistance.

jmr

---

