---
title: "Able to connect via wifi, but can't use vsftpd"
date: 2013-07-10
forum: Networking &amp; Wireless
---

### Post by sixsupersonic on 2013-07-10
I wanted to setup a experimental local server on my laptop and wanted to use vsftpd, but when I try to connect to the server I get "no route to host" on my client.  It seems to work on ubuntu desktop, which is on the same laptop, but it doesn't work on Ubuntu server.
Here is my /etc/network/interface file

auto wlan0
iface wlan0 inet dhcp
    wpa-conf /etc/wpa_supplicant.conf

Here is my /etc/wpa_supplicant.conf file

network={
     ssid="MYSSID"
     scan_ssid=1
     key_mgmt=WPA-PSK
     psk="MYPASSKEY"
}

Im not sure what to do and I would like to get it working guite soon.

Thanks

---

