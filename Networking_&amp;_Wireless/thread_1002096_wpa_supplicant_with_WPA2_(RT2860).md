---
title: "wpa_supplicant with WPA2 (RT2860)"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by dragonscum on 2008-12-04
Hi guys,

I am running the latest  Ubuntu 8.10 - the Intrepid Ibex but I am stumped by the configuration of my wireless card. I am using a RT2860 wireless card. I downloaded the driver and installed it. I am pretty certain it is installed correctly because if I set my router to use no security I can connect to it and surf the internet.

But when I enable security things get jiggy. No matter how I configure my wireless card (by editing /etc/Wireless/RT2860STA/RT2860STA.dat) and wpa_supplicant, I cant connect.

I want to connect using WPA2. I have configured my router to WPA-PSK-AUTO. This is my /etc/wpa_supplicant/sup.conf:

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=0

network={
        ssid="myssid"
        scan_ssid=1
        proto=RSN WPA
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP WEP104 WEP40
        psk=pskkey
}

this is what i get when doing iwlist scan:

Cell 02 - Address: 00:19:5B:95:4A:B0
                    ESSID:"myssid"
                    Mode:Managed
                    Channel:1
                    Quality:76/100  Signal level:-60 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

This is the authentication part of my wireless card:

AuthMode=WPA2PSK
EncrypType=AES
WPAPSK=mykey

Other configurations have already been tried

Any help would be appreciated

PS: I am pretty much a linux newbie

---

### Post by kevdog on 2008-12-05
What commands are you using to connect?

---

### Post by HubertK on 2008-12-06
Please test this
rt2860-dkms_1.7.1.1_all.deb
He is on [www.array.org](www.array.org)
[http://www.array.org/ubuntu/dists/intrepid/eeepc/binary-i386/](http://www.array.org/ubuntu/dists/intrepid/eeepc/binary-i386/)
The driver works this wpa2, no problem.

---

