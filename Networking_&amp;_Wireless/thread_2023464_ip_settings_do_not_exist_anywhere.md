---
title: "ip settings do not exist anywhere"
date: 2012-07-12
forum: Networking &amp; Wireless
---

### Post by jdieter on 2012-07-12
ip settings cannot be found anywhere

I run ifconfig and see my static ip setup nicely. it works fine. Has been working for months. time comes that i need to change my ip, and i find it is not in the interfaces file. interfaces is setup as dhcp. there is no networkmanager installed, no wicd, and a grep -R for my ip address finds NOTHING except settings in exim4.
Where the hell is this ip configuration being stored! 12.04 with no desktop installed.

---

### Post by rukiaEnix on 2012-07-12
If you are running Ubuntu with graphic mode check for this directory:

```

ls /etc/NetworkManager/system-connections/

```

---

### Post by bab1 on 2012-07-12
> **jdieter said:**
> ip settings cannot be found anywhere

I run ifconfig and see my static ip setup nicely. it works fine. Has been working for months.
The command ifconfig shows the currently configured interface (eth0 or whatever).  This doesn't have to be a statically configured IP address.  DHCP can supply it also.> 

time comes that i need to change my ip, and i find it is not in the interfaces file. interfaces is setup as dhcp.
It probably something like this ```
auto eth0
iface eth0 inet dhcp
```> 
 there is no networkmanager installed, no wicd, and a grep -R for my ip address finds NOTHING except settings in exim4.
Where the hell is this ip configuration being stored! 12.04 with no desktop installed.
The configuration is requested by *dhclient*.  You will find the leases at ```
/var/lib/dhcp3/dhclient.leases
```  The dhclient requests the IP address (lease) and I assume your router has been the DHCP server, supplying the address from its the dhcp pool.

This should not stop you from reconfiguring the eth0 interface to a statically configured state.  You can use the traditional /etc/network/interfaces file.  You should configure the dns servers there too.  Ubuntu 12.04 server now uses /etc/[COLOR="Blue"]resolvconf[/COLOR] instead of /etc/[COLOR="DarkGreen"]**resolv.conf**[/COLOR].

---

