---
title: "Encryption key turns to off after some time of use with wpa_supplicant"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by thomer on 2009-01-22
Hi

We are using Ubuntu 7.10 with wpa_supplicant and ndiswrapper 1.53. The wireless network on our HP Compaq nx7300 laptops connects just fine to a Cisco access point, but after some time of use, like 30 minutes, encryption key turns to "off" according to iwconfig and the network is lost.

Our wpa_supplicant.conf looks like this:

eapol_version=1
ap_scan=1
fast_reauth=1
network={
        ssid="network_name"
        scan_ssid=1
        key_mgmt=WPA-EAP
        eap=PEAP
        phase2="autheap=MSCHAPV2"
        anonymous_identity="uid@our.dept"
        identity="our-dept-wavelanxx/ppp"
        password="xxxxxxxxxx"
        priority=10
        ca_cert="/etc/ssl/pcacert.crt"
}

When the network is working iwconfig says:

wlan0     IEEE 802.11g  ESSID:"network_name"
          Mode:Managed  Frequency:2.412 GHz  Access Point: AA:BB:CC:DD:EE:FF
          Bit Rate=54 Mb/s   Tx-Power:14 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XXXX   Security mode:restricted
          Power Management:off
          Link Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

When the network is lost the line with "Encryption key:XXXX-XXXX-..." turns to "Encryption key:off".

When the network is working "arp -n" says:

Address                  HWtype  HWaddress           Flags Mask Iface
WW.XX.YY.ZZ              ether   FF:EE:DD:CC:BB:AA   C wlan0

When the network is lost "arp -n" says:

Address                  HWtype  HWaddress           Flags Mask Iface
WW.XX.YY.ZZ                     (incomplete) wlan0

Thanks for any input of what might be wrong here or a possible workaround without turning the encryption off!

---

### Post by thomer on 2009-01-22
I would like to add that we are using kernel 2.6.22-15-generic (Ubuntu 7.10).

---

### Post by kevdog on 2009-01-22
Very interesting problem you pose here, and not sure if I have an answer.  Just taking a stab to make sure its not kernel related, do more modern versions of Ubuntu do the same thing?  Also have you tried compiling wpa_supplicant from source?  Are you able to use wpa_supplicant with other access points (possibly a home access point) and are the results similar?

---

### Post by thomer on 2009-01-22
We have not tried more recent versions of Ubuntu yet, but we tried compiling wpa_supplicant from source. We have tried both wpa_supplicant + fwcutter and also tried wpa_supplicant + ndiswrapper. But in both cases the network gets lost after about 15-60 minutes.

We have tried moving the laptop to a building where there is only one access point (AP) available and then the network seems to not get lost. I suppose either there is a problem with some of the AP's in the building or there is a problem when the laptop of some reason choses to jump from one AP to another AP.

---

### Post by kevdog on 2009-01-22
I would assume you are correct.  Not knowing the wpa algorithm all that well, I don't know when and how frequently the client has to update its credentials.  This may be the problem.

---

