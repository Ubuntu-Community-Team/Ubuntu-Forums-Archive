---
title: "/etc/dnsmasq.conf doesn't exist?"
date: 2011-03-11
forum: Networking &amp; Wireless
---

### Post by mvmacd on 2011-03-11
```

matt: / $ cat /etc/dnsmasq.conf
cat: /etc/dnsmasq.conf: No such file or directory

```

Back when I was on OpenSuSE, I had a /etc/dnsmasq.conf. I never checked it though, so it could have been empty.. but, anyway, **sometimes** I have issues with getting correct IP addresses from Routers. Even when I use "dhclient".. Like, it will get a 10.x.x.x IP when I want a 192.x.x.x. So, just a little bit ago, I typed ```
ps -ef|grep masq
``` and it showed dnsmasq was running. I don't remember the full command, but it had parameters, like the starting IP [10.42.1.x] and ending IP, so, where is it's configuration? Can I just disable dnsmasq altogether? Or do I need it for something. I often make AdHoc networks to connect to my iPod (For OpenSSH), and I understand it's a DHCP/DNS server? so do I need it? 

Thanks
Matt

---

### Post by alSee on 2011-08-08
It is likely you haven't installed 'dnsmasq' package. Try:
```
sudo apt-get install dnsmasq
```
If it's already in your system then post here the output of:
```
dpkg -L dnsmasq
```

---

### Post by capscrew on 2011-08-08
> **mvmacd said:**
> ```

matt: / $ cat /etc/dnsmasq.conf
cat: /etc/dnsmasq.conf: No such file or directory

```

Back when I was on OpenSuSE, I had a /etc/dnsmasq.conf. I never checked it though, so it could have been empty.. but, anyway, **sometimes** I have issues with getting correct IP addresses from Routers. Even when I use "dhclient".. Like, it will get a 10.x.x.x IP when I want a 192.x.x.x. So, just a little bit ago, I typed ```
ps -ef|grep masq
``` and it showed dnsmasq was running. I don't remember the full command, but it had parameters, like the starting IP [10.42.1.x] and ending IP, so, where is it's configuration? Can I just disable dnsmasq altogether? Or do I need it for something. I often make AdHoc networks to connect to my iPod (For OpenSSH), and I understand it's a DHCP/DNS server? so do I need it? 

Thanks
Matt

Network Manager uses dnsmasq libs to provide some services.  I'll bet you are using Network Manager for Internet Connection Sharing.  There is no config file in this situation.  The config is hard coded in Network Manager.

---

