---
title: "Could not resolve hostname"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by B34N on 2010-04-29
I'm having an issue where some of my machines hostnames are no longer able to be resolved after setting up a mythbuntu backend to allow netboot. Also it seems that which machines hostnames get resolved is not consistent. (ie sometimes one gets resolved and sometimes it doesn't) I suspect that it has something to do with the changes I made to "/etc/ltsp/dhcpd.conf" to get the netboot running.

I have a Verizon DSL modem/router as 192.168.1.1. Up until playing with the "/etc/ltsp/dhcpd.conf" I saw hostnames of all of my machines show up in its network map. Now, some of my machines still get network access but their hostnames are no longer resolved. What did I do wrong?

Here is my dhcpd.conf file:
```
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.2 192.168.1.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.1.1;
    option broadcast-address 192.168.1.255;
    option routers 192.168.1.1;
#    next-server 192.168.1.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}

```

Thank you!

---

### Post by B34N on 2010-04-29
I'm also noticing that the systems whose hostnames I am not able to resolve are assigned static IP addresses (according to the DSL modem/router). Does this mean that the mythbuntu backend is assigning some IP addresses? If so, how do I stop that?

---

### Post by Iowan on 2010-04-29
**dhcpd.conf** sounds like a DHCP Server configuration file. Are the DSL modem/router and mythbuntu both acting as DHCP servers? (probably not a good thing). Check **sudo ps -ef |grep dhcp** to see what processes may be running.

---

### Post by B34N on 2010-05-07
> **Iowan said:**
> **dhcpd.conf** sounds like a DHCP Server configuration file. Are the DSL modem/router and mythbuntu both acting as DHCP servers? (probably not a good thing).

That's the problem. I have my Mythbuntu running DHCP so that I can netboot and I have my DSL modem/router also handling DHCP for the rest of my machines. Can I netboot without having DHCP running on my mythbuntu backend?

---

### Post by B34N on 2010-05-07
I have a Verizon DSL Router/Modem (Westell a90). I was going to disable DHCP on the mythbuntu backend but I don't see how I can tell my router/modem to forward any PXEboot requests to the backend. I'm guessing it does not support it, that is unless I can set it up through port forwarding/triggering. Can I?

Another option is to just run DHCP on my backend and disable it on the router/modem. Unfortunately when I do that it does not assign the computer hostnames. I would prefer not to have to set them up manually since I ahve over a dozen devices on the network. How can I have DHCP use the computer names as the hostnames?

---

