---
title: "Can't get back my static ip settings"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by ravi.xolve on 2009-05-12
I had set static ip since kubuntu 7.04 and the distro upgrades never disturbed those settings.

But I thought that it might be a great idea to give network manager a try. I deleted my /etc/network/interfaces file and restarted my PC. I was able to get a dynamc ip by dhcp. Now i want to connect back using static ip but I cannot. I created the following interfaces file.

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        gateway 192.168.1.1

```It sets my static ip but I can't browse web anymore as it won't resolve the URLs anymore. :(
Please help.

---

### Post by ravi.xolve on 2009-05-12
I tried setting up static ip using nm-applet but it doesn't work.

And where is my eth0 device file?

---

### Post by zika on 2009-05-12
> **ravi.xolve said:**
> I had set static ip since kubuntu 7.04 and the distro upgrades never disturbed those settings.

But I thought that it might be a great idea to give network manager a try. I deleted my /etc/network/interfaces file and restarted my PC. I was able to get a dynamc ip by dhcp. Now i want to connect back using static ip but I cannot. I created the following interfaces file.

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        gateway 192.168.1.1

```It sets my static ip but I can't browse web anymore as it won't resolve the URLs anymore. :(
Please help.
You are probably missing /etc/resolv.conf file with Your DNS a and search server ... for example:```
search google.com
nameserver ***.***.***.***
nameserver ***.***.***.***
nameserver 208.67.220.220
nameserver 208.67.222.222
```

---

### Post by DGortze380 on 2009-05-12
> **ravi.xolve said:**
> I had set static ip since kubuntu 7.04 and the distro upgrades never disturbed those settings.

But I thought that it might be a great idea to give network manager a try. I deleted my /etc/network/interfaces file and restarted my PC. I was able to get a dynamc ip by dhcp. Now i want to connect back using static ip but I cannot. I created the following interfaces file.

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        gateway 192.168.1.1

```It sets my static ip but I can't browse web anymore as it won't resolve the URLs anymore. :(
Please help.

You are correct, that will not work.
You've assigned your machine the same IP as your router.

---

### Post by zika on 2009-05-12
> **DGortze380 said:**
> You are correct, that will not work.
You've assigned your machine the same IP as your router.
bingo! I did not look close enough, wasn't paying attention.

---

