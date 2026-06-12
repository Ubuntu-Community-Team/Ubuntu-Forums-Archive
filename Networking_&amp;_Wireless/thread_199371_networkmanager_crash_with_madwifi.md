---
title: "networkmanager crash with madwifi"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by eyephisc on 2006-06-18
I'm using Ubuntu 6.06 and am very pleased overall.  My wireless *seems* to work out of the box with my WPA network after installing networkmanager.  However, network manager randomly crashes.  I fix the connection by running

```
sudo NetworkManager
```

from the console.  But sometimes the connection only lasts for 30 seconds before crashing again.  Sometimes NetworkManager goes 10 minutes without crashing...  I haven't seen anything on the forums about NetworkManager crashing, so I'd appreciate any help.

In windows, the connection worked fine.  Windows identified my card as an Atheros 5005 I believe.  dmesg indicates that madwifi thinks it's an Atheros 5212.  The supplied drivers are labeled 5211.inf, etc, so I don't really know.  The computer is a Toshiba Satellite m45-s165.

Here is the output from my /var/log/syslog at the time when the NetworkManager crash occurs:

```
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628):  00 00 00 00 00 00 bf 16 16 c9 dd be e7 33 5b 3b 6f 3a 98 93 af 3f 00 20 f6 cc 17 79 66 3d ff 90 8e 5a be c3 2e 40 e9 eb e5 dc 17 73 92 64 46 40 b5 93 86 13 b7 c7 42 6a 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): WPA: RX message 1 of Group Key Handshake from 00:13:46:16:8e:ac (ver=1) 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): WPA: Group Key - hexdump(len=32): [REMOVED] 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): WPA: Installing GTK to the driver (keyidx=1 tx=0). 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): WPA: RSC - hexdump(len=6): 00 00 00 00 00 00 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): wpa_driver_madwifi_set_key: alg=TKIP key_idx=1 set_tx=0 seq_len=6 key_len=32 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): WPA: Sending EAPOL-Key 2/2 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 11 00 20 00 00 00 00 00 00 00 03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 de 2b f0 1e de cf da 57 54 6c 44 66 3c 6e bb b9 00 00 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): WPA: Key negotiation completed with 00:13:46:16:8e:ac [PTK=TKIP GTK=TKIP] 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 36 36 31 35 2d 31 00 00 00 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): Cancelling authentication timeout 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): Removed BSSID 00:13:46:16:8e:ac from blacklist 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): State: GROUP_HANDSHAKE -> COMPLETED 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): CTRL-EVENT-CONNECTED - Connection to 00:13:46:16:8e:ac completed (reauth) 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 36 36 31 35 2d 31 00 00 00 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): EAPOL: External notification - portValid=1 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): EAPOL: External notification - EAP success=1 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): EAPOL: SUPP_PAE entering state AUTHENTICATING 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): EAPOL: SUPP_BE entering state SUCCESS 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): EAP: EAP entering state DISABLED 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): EAPOL: SUPP_PAE entering state AUTHENTICATED 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): EAPOL: SUPP_BE entering state IDLE 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): EAPOL: startWhen --> 0 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): Wireless event: cmd=0x8b15 len=20 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): Wireless event: new AP: 00:00:00:00:00:00 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): Setting scan request: 0 sec 100000 usec 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): Added BSSID 00:13:46:16:8e:ac into blacklist 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): State: COMPLETED -> DISCONNECTED 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): EAPOL: External notification - portEnabled=0 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): ONNECTED 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): EAPOL: SUPP_BE entering state INITIALIZE 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): EAPOL: External notification - portValid=0 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): EAPOL: External notification - EAP success=0 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 36 36 31 35 2d 31 00 00 00 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): wpa_driver_madwifi_del_key: keyidx=0 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): wpa_driver_madwifi_del_key: keyidx=1 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): wpa_driver_madwifi_del_key: keyidx=2 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): wpa_driver_madwifi_del_key: keyidx=3 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): wpa_driver_madwifi_del_key: keyidx=0 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): State: DISCONNECTED -> SCANNING 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): Starting AP scan (broadcast SSID) 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): Wireless event: cmd=0x8b1a len=8 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): Wireless event: cmd=0x8b19 len=8 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): Received 1605 bytes of scan results (8 BSSes) 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): Scan results: 8 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): Selecting BSS from priority group 0 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): 0: 00:11:50:5f:87:57 ssid='http://www.compuman.org' wpa_ie_len=24 rsn_ie_len=0 caps=0x11 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628):    skip - SSID mismatch 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): 1: 00:13:46:16:8e:ac ssid='wildboyz' wpa_ie_len=24 rsn_ie_len=0 caps=0x11 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): ted based on WPA IE 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): Trying to associate with 00:13:46:16:8e:ac (SSID='wildboyz' freq=2462 MHz) 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 36 36 31 35 2d 31 00 00 00 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): Cancelling scan request 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): WPA: clearing own WPA/RSN IE 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): Automatic auth_alg selection: 0x1 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): WPA: using IEEE 802.11i/D3.0 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): WPA: clearing AP RSN IE 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): WPA: using GTK TKIP 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): WPA: using PTK TKIP 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): WPA: using KEY_MGMT WPA-PSK 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): No keys have been configured - skip key clearing 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): wpa_driver_madwifi_set_drop_unencrypted: enabled=1 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): State: SCANNING -> ASSOCIATING 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): wpa_driver_madwifi_associate 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): Setting authentication timeout: 10 sec 0 usec 
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^Iwpa_supplicant(6628): EAPOL: External notification - EAP success=0 
Jun 18 13:30:25 ian-laptop NetworkManager: <WARNING>^I nm_signal_handler (): Caught signal 11.  Generating backtrace... 
Jun 18 13:30:25 ian-laptop NetworkManager: ******************* START **********************************
Jun 18 13:30:25 ian-laptop NetworkManager: (no debugging symbols found)
Jun 18 13:30:25 ian-laptop NetworkManager: Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Jun 18 13:30:25 ian-laptop NetworkManager: (no debugging symbols found)
Jun 18 13:30:25 ian-laptop last message repeated 5 times
Jun 18 13:30:25 ian-laptop NetworkManager: [Thread debugging using libthread_db enabled]
Jun 18 13:30:25 ian-laptop NetworkManager: [New Thread -1211922752 (LWP 6615)]
Jun 18 13:30:25 ian-laptop NetworkManager: [New Thread -1237103696 (LWP 7149)]
Jun 18 13:30:25 ian-laptop NetworkManager: [New Thread -1228710992 (LWP 6639)]
Jun 18 13:30:25 ian-laptop NetworkManager: [New Thread -1220318288 (LWP 6618)]
Jun 18 13:30:25 ian-laptop NetworkManager: [New Thread -1211925584 (LWP 6617)]
Jun 18 13:30:25 ian-laptop NetworkManager: (no debugging symbols found)
Jun 18 13:30:25 ian-laptop last message repeated 10 times
Jun 18 13:30:25 ian-laptop NetworkManager: 0xffffe410 in __kernel_vsyscall ()
Jun 18 13:30:25 ian-laptop NetworkManager: <information>^ISuccessfully reconnected to the system bus. 
Jun 18 13:30:25 ian-laptop NetworkManager: ******************* END **********************************

```

So I'm wondering if anyone has any ideas for troubleshooting this because I'm at the limits of my knowledge.  And also, could anyone walk me through uninstalling the madwifi drivers to try replacing them with the ndiswrapper?  Does ndiswrapper work with NetworkManager?

Thanks for any suggestions!

---

### Post by eyephisc on 2006-06-19
Upon further inspection, it looks like an issue with WPA_supplicant and madwifi.  There are several howtos describing installing the newest madwifi from source here.  Does anyone know how to just try loading the modules in /lib/modules/2.6.15-25-686/madwifi-ng/ rather than the old madwifi modules?  Or is source the best way to go?

---

