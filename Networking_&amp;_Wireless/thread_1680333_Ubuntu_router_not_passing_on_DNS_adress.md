---
title: "Ubuntu router not passing on DNS adress"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by marcusklaas on 2011-02-02
Sup guys,

I'm using an ubuntu machine to route internet to my main PC. I think I finally got it working with DHCP and all, but there's still a slight problem. DNS does not work! My /etc/dhcp3/dhcpd.conf file contains the following lines: 

```
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.0.255;
option routers 192.168.0.1;
option domain-name-servers 192.87.36.36, 192.87.106.106;
option domain-name "marcusklaas.nl";

subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.10 192.168.0.200;
}

```

I am currently only able to post on this forum because I copied /etc/resolv.conf from my server to my main machine. Now DNS is working. But it should update automatically, right? Currently, this isn't working. 

Anyone got any ideas? If possible, I'd like it most if I wouldn't have to hardcode the DNS servers in /etc/dhcp3/dhcpd.conf either, but that the server would just relay the DNS adress it has gotten itself!

Thanks!

---

### Post by Kirboosy on 2011-02-02
After you modified your networking config did you restart networking or dhcp?
```

sudo /etc/init.d/networking restart
```

---

### Post by marcusklaas on 2011-02-02
Yes. I restarted both networking and dhcp3-server several times after the changes, but doesn't seem to change anything :(

---

### Post by Kirboosy on 2011-02-02
Have you looked [here]("https://help.ubuntu.com/community/dhcp3-server") at the community documentation?

Or maybe you need to setup a [BIND9 Server]("https://help.ubuntu.com/community/BIND9ServerHowto")

---

### Post by marcusklaas on 2011-02-02
Yes, the community docs were the thing that got me this far in the first place :p Maybe a bind9 server is required, but it seems silly. All the server needs to do is relay the DNS address, not actually host a dns-service.

---

### Post by Kirboosy on 2011-02-02
I think this is wrong...
```

option domain-name-servers 192.87.36.36, 192.87.106.106;
```I'm not sure how to fix it though. It just doesn't make sense to me. All the tutorials at least use the same subnet...

I'm guessing you have your server on its own?


Try telling it to use Google's Public DNS Servers [link]("http://code.google.com/speed/public-dns/")

---

### Post by marcusklaas on 2011-02-02
Sup mate. I got it working by adding the DNS servers not just as a general setting, but as a subnet setting. Thanks for the help!

---

### Post by Kirboosy on 2011-02-03
Glad it was a semi easy fix.


Now you can mark this thread as solved. :)

---

