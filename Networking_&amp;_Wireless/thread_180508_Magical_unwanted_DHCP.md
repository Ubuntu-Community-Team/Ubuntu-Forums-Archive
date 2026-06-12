---
title: "Magical unwanted DHCP"
date: 2006-05-22
forum: Networking &amp; Wireless
---

### Post by voodooconstant on 2006-05-22
I know just enough to be dangerous with this stuff so please be kind.

I have a Breezy install (I used a server package I found somewhere on the ubuntu site).  I installed a second NIC.  Ubuntu hasn't had any trouble using it.

My issue is that even though I feel I've set it up for a static IP, it still pulls a DHCP address every once and a while. 

To set my static IP, I modified /etc/networking/interfaces to look like:

```
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet static
        address 172.19.16.10
        netmask 255.255.240.0
        network 172.19.16.0
        broadcast 172.19.31.255
        gateway 0.0.0.0

auto eth1
iface eth1 inet static
        address 192.168.100.235
        netmask 255.255.255.0
        network 192.168.100.0
        broadcast 192.168.100.255
        gateway 192.168.100.254
```

I've performed many /etc/init.d/networking restart's.  When I do this, the networking settings I've specified in the interfaces config file are applied.  However, I'll come back the next day and it will have pulled an IP.  

I had problems with my DNS being changed as well, but I feel as though the root issue is the DHCP.  Can anyone tell me why this is happening?  If there is any other information that would be helpful to post here, let me know and I'll edit my question accordingly.

Thanks in advance.

---

### Post by fulfordrg1 on 2006-05-22
Hello, I am also having problems with my DNS settings being changed all the time. I have tried some of the fixes in the forums but the it still changes. I have a NetComm  NBS ADSL-2 modem. This is the first time I have tried Dapper and am very happy with it (except this dns S*#T). Dont know what else to do, any more ideas?

---

### Post by dmizer on 2006-05-22
have you tried disabling ipv6? [https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28ipv6%29](https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28ipv6%29)

this always wreaks havoc on my network settings.

---

### Post by voodooconstant on 2006-05-24
I have tried out your suggestions.  I'll let you know in a day or so if it works out!

Thanks!

---

### Post by voodooconstant on 2006-05-25
Ok, one day and still ok.  that seems to have fixed it.  Anyone know why ipv6 would cause my box to behave like this?  Seems a bit wierd to me...

---

### Post by dmizer on 2006-05-26
i believe it's related to a firefox bug.  but don't quote me on that.

more generally though it's just that your hardware won't work on ipv6 (which is a server protocol)

on a related note, shouldn't ipv6 be disabled by default?  it seems to be an issue often enough.  but perhaps i just don't fully understand the problem (which is also quite likely).

---

