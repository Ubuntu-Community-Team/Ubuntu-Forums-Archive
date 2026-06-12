---
title: "Unable to connect to 802.11n router using ubuntu 10.10, madwifi,and ar5212"
date: 2011-04-02
forum: Networking &amp; Wireless
---

### Post by ffan on 2011-04-02
Hi,

I've tried to connect to my new router using my thinkpad r61 with an ar5212 wireless card.  It's in g/n mode.  I am able to connect to it when I boot into windows, but can't in ubuntu 10.10.

I am able to connect to my old router g in ubuntu.

I've followed the instructions on 
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)
for madwif and ath_pci, but it seems like the DHCP request times out.

I've attached the diagnostics and syslog.

my wpa_supplicant conf is


ctrl_interface=/var/run/wpa_supplicant
#ctrl_interface_group=network
#update_config=1
ap_scan=2
network={
        ssid="mywlan"
        #psk="mypwd"
        proto=WPA
        key_mgmt=WPA-PSK
        psk=76537b9b8f3824e7ab8a4dd8aa745bf053eec18e35de4b433b1db92234e85742
}

---

