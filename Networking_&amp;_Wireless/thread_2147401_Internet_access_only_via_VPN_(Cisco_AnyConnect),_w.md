---
title: "Internet access only via VPN (Cisco AnyConnect), when VPN off - DNS look-up fails"
date: 2013-05-21
forum: Networking &amp; Wireless
---

### Post by ad05bzag on 2013-05-21
I am using Ubuntu 12.04. After installing VPN client and using it for couple of months normally, something happened. After one more package/program update I stopped being able to connect to Internet without the VPN client - ie I have to be connected through my university VPN even with my home Wifi connection. On Windows XP machine (dual-boot on the same laptop) and android phone everything works just fine.

What to do?

---

### Post by cipherboy_loc on 2013-05-21
If you can ping something on your local network, double check your DNS server settings. It is a possibility that you only have DNS servers available via VPN in use, which would cause you to be unable to access the internet except via internet. To test whether this is the case, try pinging an external IP address (8.8.8.8--google's DNS server). If that goes through without the VPN, this is likely the case. Then you could add a DNS server to your DNS settings (google's or usually your router has a DNS server associated with it too). 


Thanks,
Cipherboy

---

### Post by sanderj on 2013-05-22
when DNS does not work, what is the output of:

```
cat /etc/resolv.conf
```

---

### Post by ad05bzag on 2013-05-22
As you have suggested I pinged google (8.8.8.8) and it was just fine. Then I did the following to allow dynamic update of resolv.conf
```

sudo dpkg-reconfigure resolvconf

```
then manually updated etc/resolvconf/resolv.conf.d/head with google's nameservers (8.8.8.8 and 8.8.4.4) and then
```

sudo resolvconf -u
```


Now it all works fine

Thanks!

---

