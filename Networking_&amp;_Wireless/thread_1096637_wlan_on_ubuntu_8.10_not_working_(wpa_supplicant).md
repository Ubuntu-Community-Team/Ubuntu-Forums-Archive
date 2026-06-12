---
title: "wlan on ubuntu 8.10 not working (wpa_supplicant)"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by blood_on_ice on 2009-03-15
Hello!

sudo iwlist scanning reports the following:

```
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:CC:E3:BD:5C
                    ESSID:""
                    Mode:Master
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=97/100  Signal level:-29 dBm  Noise level=-96 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000000288b349236
                    Extra: Last beacon: 152ms a go
```

sudo vi /etc/wpa_supplicant/wpa_supplicant.conf:
```
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1

#home network
network={
      ssid="ssid-name"
      scan_ssid=1
      proto=WPA
      key_mgmt=WPA-PSK
      pairwise=TKIP
      group=TKIP
      psk="password"
}
```

sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -Dwext:

```
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWENCODEEXT]: No such file or directory
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWENCODEEXT]: No such file or directory
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWENCODEEXT]: No such file or directory
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWENCODEEXT]: No such file or directory
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWENCODEEXT]: No such file or directory
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWENCODEEXT]: No such file or directory
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWENCODEEXT]: No such file or directory
Associated with 00:0f:cc:e3:bd:5c
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
**WPA: 4-Way Handshake failed - pre-shared key may be incorrect**
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

```

So it seems to be a problem with the authentification...but the ssid and the key are correct...

iwconfig:

```
wlan0     IEEE 802.11abg  ESSID:"Office.70731220"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

What could be the problem?

Thanks for an answer!

Kind regards,
Peter

---

### Post by blood_on_ice on 2009-03-17
hello,

any suggestions on this?

Kind regards,
Peter

---

### Post by blood_on_ice on 2009-03-19
it works...i've used really the wrong password, unbelievable...sorry guys for wasting your time;)

Kind regards,
Peter

---

