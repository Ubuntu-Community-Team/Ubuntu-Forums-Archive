---
title: "Wireless DHCP timeout (Intel 3945ABG / Lucid / Asus U1E)"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by shartem on 2010-10-24
DHCP times out intermittently. E.g. sometimes after reboot or waking up.
daemon.log excerpt

```

Oct 24 21:24:32 shiny NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Frontier'
Oct 24 21:24:32 shiny NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Oct 24 21:24:32 shiny NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 24 21:24:32 shiny NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 24 21:24:32 shiny NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 24 21:24:32 shiny NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 24 21:24:32 shiny NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 24 21:24:32 shiny NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Oct 24 21:24:32 shiny NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto Frontier' has security, but secrets are required.
Oct 24 21:24:32 shiny NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Oct 24 21:24:32 shiny NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 24 21:24:32 shiny NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 24 21:24:32 shiny NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 24 21:24:32 shiny NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Oct 24 21:24:32 shiny NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 24 21:24:32 shiny NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 24 21:24:32 shiny NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 24 21:24:32 shiny NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Oct 24 21:24:32 shiny NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Frontier' has security, and secrets exist.  No new secrets needed.
Oct 24 21:24:32 shiny NetworkManager: <info>  Config: added 'ssid' value 'Frontier'
Oct 24 21:24:32 shiny NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Oct 24 21:24:32 shiny NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Oct 24 21:24:32 shiny NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Oct 24 21:24:32 shiny NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct 24 21:24:32 shiny NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct 24 21:24:32 shiny NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 24 21:24:32 shiny NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Oct 24 21:24:32 shiny NetworkManager: <info>  Config: set interface ap_scan to 1
Oct 24 21:24:32 shiny NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Oct 24 21:24:35 shiny wpa_supplicant[1002]: WPS-AP-AVAILABLE 
Oct 24 21:24:35 shiny wpa_supplicant[1002]: Trying to associate with 00:90:d0:de:d2:7b (SSID='Frontier' freq=2432 MHz)
Oct 24 21:24:35 shiny NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Oct 24 21:24:35 shiny wpa_supplicant[1002]: WPS-AP-AVAILABLE 
Oct 24 21:24:35 shiny wpa_supplicant[1002]: Associated with 00:90:d0:de:d2:7b
Oct 24 21:24:35 shiny NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Oct 24 21:24:35 shiny NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Oct 24 21:24:35 shiny wpa_supplicant[1002]: WPA: Key negotiation completed with 00:90:d0:de:d2:7b [PTK=CCMP GTK=CCMP]
Oct 24 21:24:35 shiny wpa_supplicant[1002]: CTRL-EVENT-CONNECTED - Connection to 00:90:d0:de:d2:7b completed (reauth) [id=0 id_str=]
Oct 24 21:24:35 shiny NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Oct 24 21:24:35 shiny NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Oct 24 21:24:35 shiny NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Frontier'.
Oct 24 21:24:35 shiny NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 24 21:24:35 shiny NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Oct 24 21:24:35 shiny NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Oct 24 21:24:35 shiny NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Oct 24 21:24:35 shiny NetworkManager: <info>  dhclient started with pid 1586
Oct 24 21:24:35 shiny NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Oct 24 21:24:35 shiny NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Oct 24 21:24:35 shiny NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Oct 24 21:24:35 shiny NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Oct 24 21:24:35 shiny dhclient: Internet Systems Consortium DHCP Client V3.1.3
Oct 24 21:24:35 shiny dhclient: Copyright 2004-2009 Internet Systems Consortium.
Oct 24 21:24:35 shiny dhclient: All rights reserved.
Oct 24 21:24:35 shiny dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct 24 21:24:35 shiny dhclient: 
Oct 24 21:24:35 shiny NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Oct 24 21:24:35 shiny dhclient: Listening on LPF/wlan0/00:1b:77:bf:df:12
Oct 24 21:24:35 shiny dhclient: Sending on   LPF/wlan0/00:1b:77:bf:df:12
Oct 24 21:24:35 shiny dhclient: Sending on   Socket/fallback
Oct 24 21:24:38 shiny dhclient: DHCPREQUEST of 192.168.1.66 on wlan0 to 255.255.255.255 port 67
Oct 24 21:24:42 shiny dhclient: DHCPREQUEST of 192.168.1.66 on wlan0 to 255.255.255.255 port 67
Oct 24 21:24:53 shiny dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 24 21:24:56 shiny dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 24 21:25:04 shiny dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 24 21:25:13 shiny dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Oct 24 21:25:20 shiny NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Oct 24 21:25:20 shiny NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1586
Oct 24 21:25:20 shiny NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Oct 24 21:25:20 shiny NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Oct 24 21:25:20 shiny NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Oct 24 21:25:20 shiny NetworkManager: <info>  Activation (wlan0) failed for access point (Frontier)
Oct 24 21:25:20 shiny NetworkManager: <info>  Marking connection 'Auto Frontier' invalid.
Oct 24 21:25:20 shiny NetworkManager: <info>  Activation (wlan0) failed.
Oct 24 21:25:20 shiny NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Oct 24 21:25:20 shiny NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Oct 24 21:25:20 shiny NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Oct 24 21:25:20 shiny wpa_supplicant[1002]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

```

**Laptop model** Asus U1E
**Wireless Brand**
```
$ lspci -nn | grep Net
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)

```

```
$ iwconfig wlan0 
wlan0     IEEE 802.11abg  ESSID:"Frontier"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:90:D0:DE:D2:7B   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
$ lsmod | grep 3945
iwl3945                68727  0 
iwlcore               106050  1 iwl3945
mac80211              205402  2 iwl3945,iwlcore
led_class               2864  4 iwl3945,iwlcore,sdhci,asus_laptop
cfg80211              126528  3 iwl3945,iwlcore,mac80211

```

---

### Post by shartem on 2010-10-25
I will try installing linux-backports-modules-wireless-lucid-generic and see if it resolves the issue.

---

### Post by claracc on 2010-10-25
I have the same wifi card, and network manager always connects/disconnects constantly wifi, doing it unusable since karmic koala.

I have installed wicd to control the wifi instead of gnome network manager. It works better, at least the connection is more or less stable although since two days ago, my internet connection is very slow in ubuntu lucid, always less than 6 Mb reaching 0,5 Mb (speed tests)  when my isp gives me 12 Mb to download.

Doing speed tests with windows vista partition I have the 12 Mb.

Is there a drivers problem with this wifi card and ubuntu 10.04?

---

