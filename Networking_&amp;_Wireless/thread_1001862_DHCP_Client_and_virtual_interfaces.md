---
title: "DHCP Client and virtual interfaces"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by azzid on 2008-12-04
Hi,

I have a little issue I cannot wrap my head around.
I started looking at this quite some time ago, that generated the thread found here: [http://ubuntuforums.org/showthread.php?t=483375]("http://ubuntuforums.org/showthread.php?t=483375").

I never finished that, but today the problem reappeared in my mind and I started looking at it again.

I no longer beleive that the problem is getting the DHCP server to server out more addresses, the problem is assigning them to the virtual interface.

If I give eth2 a static address and then try to give eth2:0 an address via DHCP it fails with the same error: ```
Bind socket to interface: No such device
```

It seems that the virtual interface does not exist when the system tries to assign the address it receives from the DHCP.

Can anyone explain this?

Sincerely,
Mattias

---

### Post by Iowan on 2008-12-05
Interesting problem... Did you try using two "sub-interfaces" eth2:0 and eth2:1?> **netztier said:**
> Give it a try: define two subinterfaces with each a client-identifier of their own - and don't give an IP address to the "mother" interface at all.

---

### Post by azzid on 2008-12-09
I can assign eth2 a dhcp-address, but I cannot assign eth2:0.
I can give eth2 a static address, but still not assign eth2:0 by dhcp.
If I don't activate eth2, eth2:0 (or eth2:1) won't work.

So I don't really understand your question, could you please explain again, in greater detail, what you think I should test?

Sincerely,
Mattias

---

### Post by azzid on 2008-12-09
With the following in my **/etc/network/interfaces**:
```

# The primary internet network interface (WAN)
#auto eth2
iface eth2 inet static
        address 10.0.0.50
        netmask 255.255.255.0
        broadcast 10.0.0.255
        network 10.0.0.0

auto eth2:0
iface eth2:0 inet dhcp

auto eth2:1
iface eth2:1 inet dhcp

```

Note that eth2 is turned off.

The result of a **/etc/init.d/networking restart** is
```

SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
Bind socket to interface: No such device
Failed to bring up eth2:0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
Bind socket to interface: No such device
Failed to bring up eth2:1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

```

If I configure any other nic, like eth0 to receive an address from dhcp it works fine.
With the following in my **/etc/network/interfaces**:
```

auto eth0
iface eth0 inet dhcp

```

The result of doing **/etc/init.d/networking restart** is:
```

 * Reconfiguring network interfaces...                                          
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:0c:29:08:ba:54
Sending on   LPF/eth0/00:0c:29:08:ba:54
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.0.0.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:0c:29:08:ba:54
Sending on   LPF/eth0/00:0c:29:08:ba:54
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 10.0.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.0.0.1
bound to 10.0.0.64 -- renewal in 252 seconds.

```

The problem must be within the specific combination 'logical nic'+'dhcp' and I cannot understand why.

---

### Post by Iowan on 2008-12-09
> **azzid said:**
> I can assign eth2 a dhcp-address, but I cannot assign eth2:0.
I can give eth2 a static address, but still not assign eth2:0 by dhcp.
If I don't activate eth2, eth2:0 (or eth2:1) won't work.

So I don't really understand your question, could you please explain again, in greater detail, what you think I should test?

Sincerely,
MattiasYou answered my question - you tried assigning eth2:0 and eth2:1 (sub-interfaces) without assigning the "mother" interface (eth2).  Apparently it doesn't work...

---

### Post by azzid on 2008-12-10
Yeah, odd, isn't it?

I read somewhere that the "mother-nic" must be active for the sub-nic's to work. Based on that I think the following should work as long as the dhcp is just kind enough to deliver more than one ip:

```

# The primary internet network interface (WAN)
auto eth2 eth2:0 eth2:1
iface eth2 inet dhcp

iface eth2:0 inet dhcp

iface eth2:1 inet dhcp

```

But still I get the same results:
```

 * Reconfiguring network interfaces...                                          
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth2/00:0c:29:08:ba:68
Sending on   LPF/eth2/00:0c:29:08:ba:68
Sending on   Socket/fallback
DHCPRELEASE on eth2 to 10.0.0.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth2/00:0c:29:08:ba:68
Sending on   LPF/eth2/00:0c:29:08:ba:68
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 10.0.0.1
DHCPREQUEST on eth2 to 255.255.255.255 port 67
DHCPACK from 10.0.0.1
bound to 10.0.0.61 -- renewal in 248 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
Bind socket to interface: No such device
Failed to bring up eth2:0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
Bind socket to interface: No such device
Failed to bring up eth2:1.
                                                                         [ ok ]

```

Seems, as the dhcp-client is unable to find the virtual/logical nic. Is there any way to force the virtual nic active even though it has yet to receive an address?

---

