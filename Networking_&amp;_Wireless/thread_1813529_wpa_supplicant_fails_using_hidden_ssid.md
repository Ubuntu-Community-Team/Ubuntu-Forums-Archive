---
title: "wpa_supplicant fails using hidden ssid"
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by haleleonj on 2011-07-27
I have a broadcom internal wireless adapter, Ubuntu 10.04, and a Linksys WRT54GL router.  I have made slight modifications to my wpa_supplicant.conf file I copied from the example the man pages pointed to.  Basically this is it:

network={
        ssid="snatch"
        scan_ssid=1
        #psk="[hidden]"
        proto=WPA
        key_mgmt=WPA-PSK
        psk=[hidden]
}

My ssid is not broadcasted.  The real psk was obtained from wpa_passphrase.  I have attached an error file.  I can connect to the internet using gnome, but I have had a dream, ever since I first learned about Linux, that one day I would be able to connect to a WPA protected network from the console.  Can you help me get free from the chains of the excessive resource consumption of Gnome and KDE?

---

