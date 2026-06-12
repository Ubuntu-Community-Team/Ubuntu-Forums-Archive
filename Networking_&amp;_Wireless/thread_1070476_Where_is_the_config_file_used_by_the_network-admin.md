---
title: "Where is the config file used by the network-admin tool in Heron ?"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by joelgrrr on 2009-02-15
The new network configuration tool that 8.04 uses, network-admin, is pretty cool, but i'd like to know where it stores all the settings and changes that I make to it. For example, where does it store information such as WPA passwords that I have associated with each ssid? I don't see anything in /etc/network/interfaces

Also, is there a way of telling the roaming network manager which channel to listen to? Or does it scan all frequencies when showing you the list of available channels?

---

### Post by superprash2003 on 2009-02-15
by default scans all channels.. you could find keys by typing sudo iwlist key

---

### Post by joelgrrr on 2009-02-15
Where are the pass-phrases used for wep\wpa enabled networks stored?

---

### Post by Hemal on 2009-07-28
I need to know this as well as I have a problem with my wifi set up.

Essentially the wifi works with WPA but with DHCP.  I want to use STATIC ip address and when I do that via manually setting it in the Network Manager, I am not able to connect.  Ping to my gateway gives me network host unreachable.

So I am attempting to look at the settings / WPA pass key used by the Network manager and try to use that to manually connect using the wpa_supplicant!

Any help appreciated.

---

### Post by Roccasaurus on 2009-08-20
I'm not running a wireless NIC, but I found the network settings for my wired NICs at /etc/NetworkManager/system-connections

---

### Post by COKEDUDE on 2011-01-10
The user settings will be stored here. 

```
/home/userdirectory/.gconf/system/networking/connections
```

[http://www.arachnoid.com/linux/NetworkManager/](http://www.arachnoid.com/linux/NetworkManager/)

The System settings will be stored here. 


```
/etc/NetworkManager
```
```
/etc/NetworkManager/system-connections
```

---

