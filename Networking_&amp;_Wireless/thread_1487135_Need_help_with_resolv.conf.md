---
title: "Need help with resolv.conf"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by baytownl on 2010-05-18
I searched all over the forums and cant find what I need. I am running HyperV and have Ubuntu 10.04 LTS installed. I am logged in using ssh. The server is configured using Static IP.

# The loopback network interface
auto lo
iface lo inet loopback

auto seth0
iface seth0 inet static
address 192.168.219.25
netmask 255.255.255.0
gateway 192.168.1.1

**My problem is when I try to update apt (sudo apt-get update) i get:**

Err [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
  Temporary failure resolving 'archive.canonical.com'
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
  Temporary failure resolving 'archive.canonical.com'

So I figured it was a DNS problem, I did some reaserch and came to the conclusion that I needed to update the /etc/resolv.conf so i type in "vi /etc/resolv.conf" to add my ISP's nameserver and the file does not exist. I did not install DNS when I installed this server. 

Any Ideas?

---

### Post by chili555 on 2010-05-18
> auto seth0
iface seth0 inet static
address 192.168.219.25
netmask 255.255.255.0
gateway 192.168.1.1First, I doubt that your ethernet interface is seth0. It is more likely eth0. Did you make a typographical error?

Next, if your gateway is 192.68.1.1, then I believe you want an address in the same network, perhaps 192.168.1.25?

Finally, when vi opens a new file for /etc/resolv.conf. just add a single line:```
nameserver 192.168.1.1
```Restart networking or reboot after these changes and test with:```
ping -c3 192.168.1.1
ping -c3 www.google.com
```

---

### Post by baytownl on 2010-05-18
The gateway was wrong it was 192.168.219.1, as for the seth 0. It is not a typing error, take a look at this: [http://fawzi.wordpress.com/2010/05/03/ubuntu-server-10-4-in-hyper-v/](http://fawzi.wordpress.com/2010/05/03/ubuntu-server-10-4-in-hyper-v/)

. I set the adapter to DHCP and it is working fine now. I will set back to static tomorrow and post results. Thanks for the input though.

---

### Post by chili555 on 2010-05-18
> as for the seth 0. It is not a typing errorI learned something! Thanks for the information.

---

### Post by baytownl on 2010-05-21
I set it back to static and it worked fine once the gateway was corrected although there is a new problem. I have created a new thread as it is not related to this issue.

[http://ubuntuforums.org/showthread.php?t=1489690](http://ubuntuforums.org/showthread.php?t=1489690)

Thanks for your help!

---

