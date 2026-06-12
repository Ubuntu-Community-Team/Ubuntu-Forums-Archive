---
title: "Networking without NetworkManager"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by bmachia on 2009-11-13
Folks,
There use to be a Sticky here that described how to startup Networking and attach to the Wireless Router without the need of NetworkManager or WICD.

Can anyone point me to that posting or tell me the file to edit where I can assign things like ESSID, WPA, DHCP vs Static, and dhclient?

Bill

---

### Post by doas777 on 2009-11-13
[http://nixcraft.com/ubuntu-debian/13278-etc-network-interfaces-wireless-wifi-example.html](http://nixcraft.com/ubuntu-debian/13278-etc-network-interfaces-wireless-wifi-example.html)

[http://ubuntuforums.org/showthread.php?t=12045](http://ubuntuforums.org/showthread.php?t=12045)

dhcp and static are standards for the /etc/network/interfaces file. the other wifi stuff may take some googling

---

### Post by seeker5528 on 2009-11-13
These work for me with a WEP key.

Using WPA supplicant

```
iface eth1 inet static
address 192.168.1.11
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 68.87.85.98 68.87.69.146

wpa-ssid your-ssid
wpa-key-mgmt NONE
wpa-wep-key0 your-hex-or-text-WEP-key
```

Using iwconfig

```
iface eth1 inet static
address 192.168.1.11
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 68.87.85.98 68.87.69.146

wireless-mode Managed
wireless-chanel 11
wireless-essid your-ssid 
wireless-key your-hex-or-text-WEP-key
```

You need resolvconf installed for the dns-namservers line to work.

If you want to do WPA the first example is the one that is of interest to you, with a little research should be able to figure out the rest. Documentation for WPA supplicant is in /usr/share/doc/wpasupplicant.

From the command line:

```
zless /usr/share/doc/wpasupplicant/README.Debian.gz
```

Also for security purposes, if you are going to have your key in the interfaces file you should change the permissions so it is not readable by everyone.

```
sudo chmod 0600 /etc/network/interfaces
```

Later, Seeker

---

