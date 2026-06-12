---
title: "strange issue with wpa_supplicant and madwifi-ng"
date: 2006-02-17
forum: Networking &amp; Wireless
---

### Post by supermihi on 2006-02-17
Hi,

I got a new IBM/Lenovo z60t yesterday. It has an atheros wifi card that doesn't work with the driver provided by ubuntu, but according to some howtos in the web I installed the svn verison of madwifi-ng that works fine. Also, because I have a WPA enabled network at home, I needed to compile a newer version of wpa_supplicant with support for madwifi-ng.  This was also succesfull and I could connect. Now, I wanted to activate the network at boot time, so I made the changes in /etc/default/wpasupplicant and added the lines "iface ath0 inet dhcp" and "auto ath0" to /etc/network/interfaces.
However, if I now boot ubuntu (it is kubuntu, but that souldn't matter), there is no connection established, instead I see with iwconfig that the frequency changes every second or so. When I then do a /etc/init.d/networking restart, it works in most cases, but also the connection gets lost sometime.
Am I doing anything wrong? Any hints? Is there a more comfortable way of managing wifi with wpa?

---

### Post by klepto on 2006-02-17
here's what you need to put in /etc/network/interfaces

iface ath0 inet dhcp
pre-up  /sbin/ifconfig ath0 192.168.1.101 netmask 255.255.255.0
pre-up  /usr/local/sbin/wpa_supplicant -D ndiswrapper -iath0 -c/etc/wpa_supplicant.conf -Bwd
pre-up  /sbin/dhclient ath0
pre-up sleep 5

Edit this to your own specific tastes.
Also make sure that you compiled the madwifi drivers in wpasupplicant.

ifup ath0 will connect if you have done everything else right.

---

### Post by supermihi on 2006-02-18
I tried that, but the problem still remains.

---

### Post by klepto on 2006-02-18
Ok..

The easiest way to tell if one or the other isn't working is to enable more logging:

Try: wlanconfig ath0 create wlandev wifi0 wlanmode sta then..
/usr/local/sbin/wpa_supplicant -D ndiswrapper -iath0 -c/etc/wpa_supplicant.conf -Bwddd
and wpasupplicant will show exactly what is happening.

Did you use wpa_passphrase and enter your shared key then paste that info in /etc/wpa_supplicant.conf?

Example:

network={
        ssid="denied"
        psk=c6d69afc9731948793db97283436bb3fccfda5akah8ga5fdafafc
        key_mgmt=WPA-PSK
        proto=WPA
}

Message me if you need further help..

---

### Post by supermihi on 2006-02-18
I changed to using ndiswrapper and now it seems to wrok. Maybe madwifi is still to unstable with this particular NIC.

---

