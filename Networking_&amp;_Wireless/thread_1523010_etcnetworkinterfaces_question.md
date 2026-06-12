---
title: "/etc/network/interfaces question"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by sravi on 2010-07-02
Hi,

I'm on an embedded system that doesn't have Gnome, and I'm trying to startup networking automatically using /etc/network/interfaces.  Here's what I have.
```

cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf

``````

cat /etc/wpa_supplicant.conf
ctrl_interface_group=0
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1
fast_reauth=1
network={
        ssid="xxxx"
        key_mgmt=WPA-PSK
        psk="yyyy"
}
```eth0 comes up just fine.  wlan0 comes up, but it's unable to acquire a DHCP address.  I added the following lines to /etc/rc.local, and wlan0 comes up all the way, but I'm not too crazy about this hack.
```

cat /etc/rc.local
ifdown wlan0
ifup wlan0

```Anyone know what's wrong with the interfaces file?  Do I need to call dhclient somewhere, or does 'iface wlan0 inet dhcp' cause dhcp to be automatically called?  I'm also not sure who reads and processes the interfaces file.  If I could find out, maybe it would be possible to trace the problem.

---

### Post by quixote on 2010-07-05
The best thread I've found for this level of wireless interface info is this one: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)  It dates to 2008, but at the level of config files, not much has changed.  (I think??)

---

