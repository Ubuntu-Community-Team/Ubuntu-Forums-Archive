---
title: "Lan works but no wan"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by mattlech on 2010-12-14
Hello,  I'm a new member and it seems I'm having a problem,  but hello my name is Matthew L and I run a website called [http://matt-cast.com](http://matt-cast.com),  about a week ago I setup Ubuntu at my job (system's admin) to allow my staff to access our servers from there homes (we live in Iowa and its winter so kind of need it with the snow and all),  anyways I have it setup with a static static ip address and it does talk to the local network drives

example:
192.168.1.345

But I can't get it to access wan,  I have looked over and over to figure out why its not working?  Is this enough information?

Ps.  Thank you in advance!

---

### Post by furlabs on 2010-12-15
When you set the static IP address I presume you gave it a gateway? Eg
```
auto eth0
iface eth0 inet static
        address 192.168.1.10
        netmask 255.255.255.0
        gateway 192.168.1.254

```

Use the **route** command to confirm it got added to your routes. Your gateway is the line with 'default' in it, eg:
```
default         192.168.1.254    0.0.0.0         UG    100    0        0 eth0
```

Also, make sure you can ping the gateway.

---

### Post by Geared on 2010-12-15
Have you considered IP Masquerade / NAT?

---

### Post by mattlech on 2010-12-15
Hello and thank you for your replies,  I have went ahead and entered in that gateway number and ran that route and I got more then one line and because this is the first time that I've had to do this manually can you please tell me if this information is right?  Something has to be off on here:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
174.16.86.1     *               255.255.255.255 UH    0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         174.16.86.1     0.0.0.0         UG    0      0        0 eth0

I also noticed that the default Genmask is blank,  would that a fix in the advance tab under the wired part?  (do note I did change some of the numbers)

---

### Post by furlabs on 2010-12-19
Looks a little strange to me, I'm not sure you should have two IPs going out eth0 like that. Can you show us your /etc/network/interfaces file?

---

### Post by mattlech on 2011-01-02
Hello,  I got it to work again,  I just switched it over to automatic again and then wrote down the numbers and then just entered them in manually,  Thank you every much for all your work help :)

---

