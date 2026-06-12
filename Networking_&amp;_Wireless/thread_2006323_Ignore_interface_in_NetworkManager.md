---
title: "Ignore interface in NetworkManager"
date: 2012-06-19
forum: Networking &amp; Wireless
---

### Post by extradessert on 2012-06-19
I'm trying to get NetworkManager to ignore a ethernet interface (eth1) in 10.04, so that ignored interface could have a dhcp server sitting on it.

When I tried to specify the static IP for DHCP server use in /etc/network/interfaces, NM:
- forgot all the wired connection settings
- would not connect to the network (aka eth0 - the interface its supposed to use) with a connection specifying a MAC address
- and in the connection info menu NM thought it was connected via the interface supposed to be ignored (aka eth1), and the interface its supposed to use it was 'ignoring' (even though the net link was going through that interface - eth0)

OK I'm confused... help!

---

### Post by extradessert on 2012-06-19
bump....

---

### Post by steeldriver on 2012-06-20
do you have 

```
[ifupdown]
managed=false
```in your /etc/NetworkManager/NetworkManager.conf file? If that doesn't work, you can 'unmanage' a particular device by its MAC address (= the HWaddr shown by ifconfig):

```
[keyfile] 
unmanaged-devices=mac:XX:XX:XX:XX:XX:XX
```

---

### Post by extradessert on 2012-06-21
The unmanage line did the trick, Thanks for the help!

Edit: Forgot to mention in Lucid the NM setting configuration file is called "nm-system-settings.conf"

---

