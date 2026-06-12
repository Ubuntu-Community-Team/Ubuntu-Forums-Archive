---
title: "manage with networkmanager"
date: 2011-11-11
forum: Networking &amp; Wireless
---

### Post by spezticle on 2011-11-11
i'm using ubuntu 11.04 i386 Classic.

I did a clean install on a system connected to a router that does not have a DHCP server using an 11.04 i386 Alternate CD. During installation i set a static IP address.

Installation finished fine and I have connectivity with my static IP on eth0, but networkmanager isn't managing the connection and I don't remember where the settings are to switch ip managment back to networkmanager.

---

### Post by spezticle on 2011-11-11
it's late, i'm tired. took me a minute to figure it out.

edit /etc/network/interfaces

comment out, or remove the lines
```

# The primary network interface
#auto eth0
#iface eth0 inet static
#	address 192.168.1.2
#	netmask 255.255.255.0
#	network 192.168.1.0
#	broadcast 192.168.1.255
#	gateway 192.168.1.1
#	# dns-* options are implemented by the resolvconf package, if installed
#	dns-nameservers 8.8.8.8 8.8.4.4 192.168.1.1

```

then
```

sudo /etc/init.d/network-manager restart

```

one thing i'm not sure about though,
/etc/NetworkManager/NetworkManager.conf

the line:
[ifupdown]
managed=true

switching it from true to false seems to have no effect on anything....
anybody know why this is? Just curious

```

# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
# 
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

```

---

