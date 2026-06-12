---
title: "Stuck on 'waiting for network configuration'"
date: 2012-05-14
forum: Networking &amp; Wireless
---

### Post by sandyd on 2012-05-14
I currently own an entire /27 block ([http://whois.arin.net/rest/net/NET-63-141-254-0-1.html](http://whois.arin.net/rest/net/NET-63-141-254-0-1.html))

I'm having a bit of trouble assigning ip aliases to my interface.

Each time I add the alias, the boot pauses on
'Waiting for network configuration. . .'
'Waiting up to 60 seconds for network configuration'
'Booting system without full network configuration'

[COLOR="Magenta"]/etc/network/interfaces[/COLOR]
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 63.141.254.29
	netmask 255.255.255.224
	network 63.141.254.0
	broadcast 63.141.254.31
	gateway 63.141.254.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 208.67.222.222 208.67.220.220

auto eth0:0
iface eth0:0 inet static
	address 63.141.254.28
	netmask 255.255.255.224
#	network 63.141.254.0
#	broadcast 63.141.254.31
	gateway 63.141.254.1
#	dns-nameservers 208.67.222.222 208.67.220.220

```
The IP itself binds fine, I think, because I can ping it.

Binding the aliased ip on its own is not a problem, so it isn't the ip address either.

---

### Post by roelforg on 2012-05-14
The 
```

auto eth0:0

```part, i've never seen that before...
But it's configuring the nic twice, so remove one entry (the last one as i suspect it's wrong) and it should be fine.

BTW,
Why did you get that anyways?

---

### Post by matt_symes on 2012-05-14
Hi


> **roelforg said:**
> The 
```

auto eth0:0

```part, i've never seen that before...
But it's configuring the nic twice, so remove one entry (the last one as i suspect it's wrong) and it should be fine.

BTW,
Why did you get that anyways?

It's aliasing the card with multiple ip addresses. That is fine.


SandyD. 


What version of Ubuntu are you using ? 


Kind regards

---

