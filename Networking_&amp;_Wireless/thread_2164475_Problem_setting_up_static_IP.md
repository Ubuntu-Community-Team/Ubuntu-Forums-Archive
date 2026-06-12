---
title: "Problem setting up static IP"
date: 2013-07-31
forum: Networking &amp; Wireless
---

### Post by 4TdpD3n on 2013-07-31
Ok, this is driving me crazy. I've set up a few terminals with static IP addresses without a hitch before, but I cannot get this to work.

I've installed a fresh copy of Ubuntu 13.04, no desktop.
It's set by default to DHCP, and the first thing I do (sanity check) is ping google.com. I get a response.
I ping my gateway, 192.168.2.1, again, a clean response.

Great. Time to set this up to use a static IP.
Type in "sudo nano /etc/network/interfaces" and edit it to match the following:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.4
        netmask 255.255.255.0
        gateway 192.168.2.1


# Example to keep MAC address between reboots
#hwaddress ether DE:AD:BE:EF:CA:FE


# WiFi Example
#auto wlan0
```

My router dishes out DHCP addresses on the 192.168.2.x range, so I don't believe I have a confliction using this address.

I restart.
First thing I do now is ping my gateway, 192.168.2.1, it returns:
"connect: Network is unreachable"
For kicks and giggles I ping google.com, it returns:
"ping: unknown host google.com" (Not surprising, I know)

This is all done with an Ethernet cable plugged directly into the router.

I'm sure I'm doing something idiotic, any notion what that might be?

---

### Post by praseodym on 2013-07-31
Shouldnt it read
```

        address 192.168.2.4
```
instead?

---

### Post by 4TdpD3n on 2013-07-31
Interesting, my understanding was that I wanted it to be outside the DHCP range, so that the router doesn't accidentally assign an IP to another device that matches the static IP. Is this not so?

Changing the IP to 192.168.2.4 allowed me to ping the router, and I was able to SSH to it from my computer. I'm unable to ping google from it however. That's actually ok, I only need LAN access.

Edit: Looks like it does have Internet access, it's just not resolving DNS, only mildly interested in solving that.

---

