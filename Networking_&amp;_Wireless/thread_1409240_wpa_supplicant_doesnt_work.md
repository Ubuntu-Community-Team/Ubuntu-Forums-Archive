---
title: "wpa_supplicant doesnt work :/"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by -glow- on 2010-02-17
Hi there, i hope someone here can help me

right now im using the nm-applet but i dont like it. it produces lags. i think the periodical ssid/broadcast check might be the cause :/
it lags every minute or so...in games and skype it is very annoying! if there is a possibily to disable these scans in nm-applet it would be fine too.

for the moment im "using" this wpa_supplicant config:

```

ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1    # ap_scan=2 was the one for me you may try 0 or 1 indstead of 2

network={
        ssid="NET"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP
        psk="hfjkas456!!fjpajsimpsufpw9458r99=asd"
}

```and im testing the code with: wpa_supplicant -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -d

the card: usb RTL 8187

everything works except of wpa_config... i bet theres some minor problem...but i cant find it :(


thanks in advance

---

### Post by -glow- on 2010-02-17
i tried another wlan card (PRISM 2 based using the hostap drivers)

but it doesnt work either :/

---

