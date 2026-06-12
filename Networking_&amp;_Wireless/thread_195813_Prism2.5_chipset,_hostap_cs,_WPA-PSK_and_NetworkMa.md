---
title: "Prism2.5 chipset, hostap_cs, WPA-PSK and NetworkManager"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by jlgijsbers on 2006-06-13
I've been trying to get my wireless to work on a home network using WPA-PSK. I disabled the standard orinoco driver, which does not support WPA-PSK. Instead I am using hostap, which does support it. The card is recognized and, according to the HAL Device Manager, running under the hostap driver.

From the NetworkManager applet, I try to 'Connect to other Wireless Network', fill in the ESSID, choose WPA Personal as the security, fill in the passphrase, choose TKIP (the password type - as used in a successful connection on Windows) and connect. After a while, NetworkManager reverts to my wired connection without any message, probably because it can't connect to the network. However, I don't understand why it can't connect.

Maybe the following logs from my last try to connect are helpful.

dmesg:

```
[4296554.767000] wifi0: LinkStatus=2 (Disconnected)
[4296554.767000] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[4296558.827000] wifi0: LinkStatus=2 (Disconnected)
[4296558.827000] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[4296558.844000] wifi0: LinkStatus=2 (Disconnected)
[4296558.844000] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[4296558.854000] wifi0: CMD=0x0121 => res=0x7f, resp0=0x0004
[4296558.854000] wifi0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc48, len=26)
[4296558.855000] wifi0: LinkStatus=2 (Disconnected)
[4296558.856000] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[4296558.866000] wlan0: Trying to join BSSID 00:00:00:00:00:00
[4296558.980000] wifi0: LinkStatus=6 (Association failed)
[4296558.980000] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[4296618.882000] wifi0: hfa384x_cmd: interrupted; err=-4
[4296618.882000] wifi0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=-4, rid=fc2a, len=2)
[4296618.882000] wifi0: cnfAuthentication setting to 0x1 failed
[4296618.883000] wifi0: LinkStatus=2 (Disconnected)
[4296618.884000] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[4296618.894000] wifi0: CMD=0x0121 => res=0x7f, resp0=0x0004
[4296618.894000] wifi0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc48, len=26)
[4296618.895000] wifi0: LinkStatus=2 (Disconnected)
[4296618.895000] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[4296618.906000] wlan0: Trying to join BSSID 00:00:00:00:00:00
[4296618.919000] wifi0: CMD=0x0121 => res=0x7f, resp0=0x0004
[4296618.919000] wifi0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc48, len=2)
[4296618.928000] wifi0: LinkStatus=2 (Disconnected)
[4296618.928000] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[4296618.939000] wlan0: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
[4296630.424000] ADDRCONF(NETDEV_UP): wifi0: link is not ready
[4296630.424000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[4296634.667000] eth0: no IPv6 routers present

```

daemon.log (I removed information pertaining to reactivation of wired connection)

```
Jun 13 17:12:30 surfboy NetworkManager: <information>^Imatch 
Jun 13 17:12:30 surfboy NetworkManager: <debug info>^I[1150211550.546559] nm_device_802_11_wireless_get_activation_ap (): Forcing AP 'SX551C0BD80' 
Jun 13 17:12:30 surfboy NetworkManager: <information>^IUser Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / SX551C0BD80 
Jun 13 17:12:30 surfboy NetworkManager: <information>^IDeactivating device wlan0. 
Jun 13 17:12:32 surfboy NetworkManager: <information>^IDevice wlan0 activation scheduled... 
Jun 13 17:12:32 surfboy NetworkManager: <information>^IDeactivating device eth0. 
Jun 13 17:12:32 surfboy dhclient: wifi0: unknown hardware address type 801
Jun 13 17:12:32 surfboy dhclient: wifi0: unknown hardware address type 801
Jun 13 17:12:32 surfboy dhclient: DHCPRELEASE on eth0 to 192.168.2.1 port 67
Jun 13 17:12:33 surfboy NetworkManager: <information>^IActivation (wlan0) started... 
Jun 13 17:12:33 surfboy NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 13 17:12:33 surfboy NetworkManager: <information>^Imatch 
Jun 13 17:12:33 surfboy NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jun 13 17:12:33 surfboy NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jun 13 17:12:33 surfboy NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jun 13 17:12:33 surfboy NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jun 13 17:12:33 surfboy NetworkManager: <information>^IActivation (wlan0/wireless): access point 'SX551C0BD80' is encrypted, and a key exists.  No new key needed. 
Jun 13 17:12:33 surfboy NetworkManager: <information>^Imatch 
Jun 13 17:12:33 surfboy last message repeated 7 times
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD wlan0^I^Ihostap^I/var/run/wpa_supplicant^I' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: response was 'OK' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: sending command 'AP_SCAN 2' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: response was 'OK' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: response was '0' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid 5358353531433042443830' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: response was 'OK' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 scan_ssid 1' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: response was 'OK' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 proto WPA' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: response was 'OK' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: response was 'OK' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 psk <key>' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: response was 'OK' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 pairwise TKIP' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: response was 'OK' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 group TKIP' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: response was 'OK' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^ISUP: response was 'OK' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): Global control interface '/var/run/wpa_supplicant-global' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): RX global ctrl_iface - hexdump_ascii(len=52): 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 77 6c   INTERFACE_ADD wl 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):      61 6e 30 09 09 68 6f 73 74 61 70 09 2f 76 61 72   an0__hostap_/var 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):      2f 72 75 6e 2f 77 70 61 5f 73 75 70 70 6c 69 63   /run/wpa_supplic 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):      61 6e 74 09                                       ant_             
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): CTRL_IFACE GLOBAL INTERFACE_ADD 'wlan0^I^Ihostap^I/var/run/wpa_supplicant^I' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): Initializing interface 'wlan0' conf 'N/A' driver 'hostap' ctrl_interface '/var/run/wpa_supplicant' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): Initializing interface (2) 'wlan0' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): EAPOL: SUPP_PAE entering state DISCONNECTED 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): EAPOL: KEY_RX entering state NO_KEY_RECEIVE 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): EAPOL: SUPP_BE entering state INITIALIZE 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): EAP: EAP entering state DISABLED 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): EAPOL: External notification - portEnabled=0 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): EAPOL: External notification - portValid=0 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):   capabilities: key_mgmt 0xf enc 0xf 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): Added alternative ifindex 3 (wifi0) for wireless events 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): x 3 (wifi0) for wireless events 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): Own MAC address: 00:02:6f:35:8c:2e 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): wpa_driver_hostap_set_wpa: enabled=1 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): Driver does not support WPA. 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): wpa_driver_hostap_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): wpa_driver_hostap_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): wpa_driver_hostap_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): wpa_driver_hostap_set_countermeasures: enabled=0 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): wpa_driver_hostap_set_drop_unencrypted: enabled=1 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): Setting scan request: 0 sec 100000 usec 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): Added interface wlan0 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): Wireless event: cmd=0x8b06 len=8 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): RX ctrl_iface - hexdump_ascii(len=9): 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):      41 50 5f 53 43 41 4e 20 32                        AP_SCAN 2        
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): RX ctrl_iface - hexdump_ascii(len=11): 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):      41 44 44 5f 4e 45 54 57 4f 52 4b                  ADD_NETWORK      
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): CTRL_IFACE: ADD_NETWORK 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): RX ctrl_iface - hexdump_ascii(len=41): 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 73 73   SET_NETWORK 0 ss 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):  31 34 33 33   id 5358353531433 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):      30 34 32 34 34 33 38 33 30                        042443830        
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): CTRL_IFACE: SET_NETWORK id=0 name='ssid' value='5358353531433042443830' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): ssid - hexdump_ascii(len=11): 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):      53 58 35 35 31 43 30 42 44 38 30                  SX551C0BD80      
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): RX ctrl_iface - hexdump_ascii(len=25): 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 73 63   SET_NETWORK 0 sc 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):      61 6e 5f 73 73 69 64 20 31                        an_ssid 1        
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): CTRL_IFACE: SET_NETWORK id=0 name='scan_ssid' value='1' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): scan_ssid=1 (0x1) 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): RX ctrl_iface - hexdump_ascii(len=23): 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 70 72   SET_NETWORK 0 pr 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):      6f 74 6f 20 57 50 41                              oto WPA          
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): CTRL_IFACE: SET_NETWORK id=0 name='proto' value='WPA' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): proto: 0x1 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): RX ctrl_iface - hexdump_ascii(len=30): 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 6b 65   SET_NETWORK 0 ke 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):      79 5f 6d 67 6d 74 20 57 50 41 2d 50 53 4b         y_mgmt WPA-PSK   
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): SK' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): key_mgmt: 0x2 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): RX ctrl_iface - hexdump_ascii(len=82): [REMOVED] 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): CTRL_IFACE: SET_NETWORK id=0 name='psk' value='4968b928c362db6a1bdb78ad72a3dca6614cc751263a83cd67d73bbd66f666aa' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): PSK - hexdump(len=32): [REMOVED] 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): RX ctrl_iface - hexdump_ascii(len=27): 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 70 61   SET_NETWORK 0 pa 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):      69 72 77 69 73 65 20 54 4b 49 50                  irwise TKIP      
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): CTRL_IFACE: SET_NETWORK id=0 name='pairwise' value='TKIP' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): pairwise: 0x8 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): RX ctrl_iface - hexdump_ascii(len=24): 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 67 72   SET_NETWORK 0 gr 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):      6f 75 70 20 54 4b 49 50                           oup TKIP         
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): CTRL_IFACE: SET_NETWORK id=0 name='group' value='TKIP' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): group: 0x8 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): RX ctrl_iface - hexdump_ascii(len=16): 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311):      45 4e 41 42 4c 45 5f 4e 45 54 57 4f 52 4b 20 30   ENABLE_NETWORK 0 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): CTRL_IFACE: ENABLE_NETWORK id=0 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): Setting scan request: 0 sec 0 usec 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): State: DISCONNECTED -> SCANNING 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): Trying to associate with SSID 'SX551C0BD80' 
Jun 13 17:12:34 surfboy NetworkManager: <information>^Iwpa_supplicant(10311): Cancelling scan request 
Jun 13 17:13:34 surfboy NetworkManager: <information>^IActivation (wlan0/wireless): association took too long (>60s), failing activation. 
Jun 13 17:13:34 surfboy NetworkManager: <information>^IActivation (wlan0) failure scheduled... 
Jun 13 17:13:34 surfboy NetworkManager: <information>^IActivation (wlan0) failed for access point (SX551C0BD80) 
Jun 13 17:13:34 surfboy NetworkManager: <information>^IActivation (wlan0) failed. 
Jun 13 17:13:34 surfboy NetworkManager: <information>^IDeactivating device wlan0. 
Jun 13 17:13:36 surfboy NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
```

Any other information that would be helpful?

Thanks for any help!

---

### Post by helmut_hed on 2006-08-13
I have a similar setup.  For me, getting an updated version of the firmware was crucial for WPA (this despite the fact that WPA worked perfectly under Windows).

Can you give this a try:

sudo hostap_diag wlan0

I have the following output:
Host AP driver diagnostics information for 'wlan0'

NICID: id=0x8013 v1.0.0 (PRISM II (2.5) Mini-PCI (SST parallel flash))
PRIID: id=0x0015 v1.1.0
STAID: id=0x001f v1.7.4 (station firmware)

The 1.7.4 version, or later, of the station firmware is necessary for WPA support.  I followed the directions on this web site to get them:

[http://linux.junsun.net/intersil-prism/](http://linux.junsun.net/intersil-prism/)

Good luck,
Jeff

---

### Post by jlgijsbers on 2006-08-13
Hey Jeff, 

thanks for the reply! I'd already found I needed to update the firmware, and my wireless has been working well for a while. Thanks anyway. :)

Johannes

---

### Post by parktownprawn on 2006-08-19
thanks

thanks to this thread i finally got wpa working with my  prism 2.5 card - i hadn't realised that i need to update the firmware

---

### Post by pinoyboyf4i on 2008-01-23
Thanks for the link helmut_hed.  I was able to get WPA working on my Netgear MA401 PCMCIA card running in Thinkpad T21.  It took me a while to digest all the info.  I found prism2_srec in my /usr/sbin directory.

---

