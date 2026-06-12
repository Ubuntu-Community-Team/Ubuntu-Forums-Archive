---
title: "What's the default network interface configuration file?"
date: 2013-05-15
forum: Networking &amp; Wireless
---

### Post by macarthor on 2013-05-15
Hi all,

I'd like to know which file is the default one to save the network interface configuration, just after system installation, but before any configuration?
 
I noticed "/etc/NetworkManager/system-connections/" folder contains interface configuration files if NetworkManager is used. But if I do not use NetworkManager, such files do not exist at all!

What I want to search is a configuration file that contains configuration for an interface, i.e., MAC bind, IPv4, IPv6.

---

### Post by steeldriver on 2013-05-15
If you don't use NetworkManager at all, then your system is probably using the older networking service with its interfaces defined the file /etc/network/interfaces

---

### Post by SeijiSensei on 2013-05-15
[https://help.ubuntu.com/12.04/serverguide/network-configuration.html#ip-addressing](https://help.ubuntu.com/12.04/serverguide/network-configuration.html#ip-addressing)

Read the section on static addressing.

---

### Post by macarthor on 2013-05-15
> **steeldriver said:**
> If you don't use NetworkManager at all, then your system is probably using the older networking service with its interfaces defined the file /etc/network/interfaces

The "/etc/network/interfaces" file does not contain MAC binding, IPv4/IPv6 DHCP settings right after system installation. So it's not what I want.

I wonder if I've made my requirement clear... What I want to find is a configuration file that contains MAC address, IPv4 settings, etc., RIGHT AFTER system installation, WITHOUT making any system modifications.

---

### Post by macarthor on 2013-05-15
> **SeijiSensei said:**
> [https://help.ubuntu.com/12.04/serverguide/network-configuration.html#ip-addressing](https://help.ubuntu.com/12.04/serverguide/network-configuration.html#ip-addressing)

Read the section on static addressing.

Thanks for reply. Please refer to #4. Waiting further help.

---

### Post by steeldriver on 2013-05-16
Well the MAC is probed from hardware - you will find it in the relevant udev rules file after boot e.g. /etc/udev/rules.d/70-persistent-net.rules

If it's a DHCP connection then you could look in /var/lib/dhcp/dhclient.leases for the IP settings

But why cant you just use the ifconfig command? what exactly are you trying to do?

---

### Post by redmk2 on 2013-05-16
> **macarthor said:**
> The "/etc/network/interfaces" file does not contain MAC binding, IPv4/IPv6 DHCP settings right after system installation. So it's not what I want.

I wonder if I've made my requirement clear... What I want to find is a configuration file that contains MAC address, IPv4 settings, etc., RIGHT AFTER system installation, WITHOUT making any system modifications.

The default file(s) for *configuring *IP networking don't have the MAC address in them.  The MAC address used is the one scanned by the networking module (driver) off the NIC itself.  You can *see * the parameters with the command ```
ifconfig -a| grep HWaddr
```. 

To modify these see the details at ```
man ifconfig
```

---

