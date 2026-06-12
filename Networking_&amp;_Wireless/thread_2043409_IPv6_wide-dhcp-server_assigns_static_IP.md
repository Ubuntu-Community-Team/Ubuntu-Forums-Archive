---
title: "IPv6 wide-dhcp-server assigns static IP"
date: 2012-08-16
forum: Networking &amp; Wireless
---

### Post by MaOs on 2012-08-16
Hi all,

I am currently playing around with an IPv6 DHCP server (wide-dhcp-server).
I got it to work without any problems and seems to function.

However, here is the part that I don't understand.
I get the same IP assigned every single time and I am not sure why.
My server config is as follows:

```

interface eth0{
        address-pool pool1 3600;
};

pool pool1 {
        range 2607:f740:0070:000f:0000:0000:0000:0000 to 2607:f740:0070:000f:ffff:ffff:ffff:ffff;
};
```

and the wide-dhcp-client receives this from the server:

```

Aug/16/2012 10:24:30: copyin_option:   IA_NA address: 2607:f740:70:f:: pltime=3600 vltime=3600
Aug/16/2012 10:24:30: client6_recvreply: executes /etc/wide-dhcpv6/dhcp6c-script
Aug/16/2012 10:24:30: client6_script: script "/etc/wide-dhcpv6/dhcp6c-script" terminated
Aug/16/2012 10:24:30: get_ia: make an IA: NA-0
Aug/16/2012 10:24:30: update_address: create an address 2607:f740:70:f:: pltime=3600, vltime=3600
```

I am wondering if this is even a valid IPv6. I am really new to the v6 business so excuse my lack of knowledge. 

Anyone have an explanation for this?

Thanks!

---

### Post by MaOs on 2012-08-16
A quick update.

I also tried now isc-dhcp-server with the same result. I get the same IP assigned over and over again.

However, the IPv6 from wide-dhcp-server != IPv6 from isc-dhcp-server. Their behavior is just the same.

That leads me to the suspicion that IPv6's default behavior is differently than IPv4? Anyone has some insights on this?

---

### Post by hawkmage on 2012-08-16
I have not played with IPv6 DHCP much but in general a DHCP client will usually cache the info it got last time and try to renew the lease on it and a DHCP server will honnor the request if the address has not been given to annother system.

---

### Post by MaOs on 2012-08-17
Yes, I figured out that for example isc-dhcp-server keeps a log file.

In /var/lib/dhcp/dhcp6.leases, clients are listed together with the IP they had (and presumably should be assigned to if possible).

---

