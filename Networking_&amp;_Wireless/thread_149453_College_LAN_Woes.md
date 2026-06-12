---
title: "College LAN Woes"
date: 2006-03-23
forum: Networking &amp; Wireless
---

### Post by fuddjaf on 2006-03-23
I just installed Breezy on my desktop here at school.  I open firefox and type in a url, and no matter what I put in I get the alert:  

"www.url.com could not be found.  Please check the name and try again."  

This was happening with SuSE also when I installed it but never with Fedora Core before that.
Right now I'm using my laptop with a Breezy Live CD and it works fine, when I first type in a URL it redirects me to a site where I log in to the school's network -- without going to that site I can't use the internet in anyway.  But for some reason my desktop won't send me to that site, I always get that same message.
My ethernet card is integrated on my nvidia motherboard; the ethernet connection is active, but that's the only indication that this isn't my hardware -- as I said, I can't use any internet applications until I get to that website.
I have switched the ethernet jacks between the two machines, the laptop always works and the desktop never does.
I know this isn't a Ubuntu specific problem but I really don't know where else to look for help, it's really just one of those pain in the butt things.  I've always found answers here so I came here first.  Help me get going in the right direction?

---

### Post by Qrk on 2006-03-23
I had the same or a similar problem (with the same symptoms, at least) with my school's network. I doubt that this fix will work for you, because its a very rare problem. 
Anyway, my problem was caused by the way the network handled the mac address for the connected computers... it would only allow one PC to be connected to the network with the same mac address.

Because my PC had the same mac address whether in Linux or Windows, somehow it confused the network that I had two PC's with the same Mac address. (I think that this was intentional) 

I fixed it by adding 
```

hwaddress ether *new:mac:address:*

auto eth0
```

to /etc/network/interfaces

(auto eth0 should be there, make sure you add the hwaddress line before it)

To find a good mac address, I'd find your old/windows mac address and add one to the last digit. You can find that by:

```
ifconfig
```

(look after hwaddr)

---

### Post by mips on 2006-03-24
[QUOTE=fuddjaf]I just installed Breezy on my desktop here at school.  I open firefox and type in a url, and no matter what I put in I get the alert:  

"www.url.com could not be found.  Please check the name and try again."  

This was happening with SuSE also when I installed it but never with Fedora Core before that.
Right now I'm using my laptop with a Breezy Live CD and it works fine, when I first type in a URL it redirects me to a site where I log in to the school's network -- without going to that site I can't use the internet in anyway.  But for some reason my desktop won't send me to that site, I always get that same message.
My ethernet card is integrated on my nvidia motherboard; the ethernet connection is active, but that's the only indication that this isn't my hardware -- as I said, I can't use any internet applications until I get to that website.
I have switched the ethernet jacks between the two machines, the laptop always works and the desktop never does.
I know this isn't a Ubuntu specific problem but I really don't know where else to look for help, it's really just one of those pain in the butt things.  I've always found answers here so I came here first.  Help me get going in the right direction?[/QUOTE]


Just some ideas:
Disable IPv6
Manually configure your IP settings
Manually configure your DNS settings
Configure your system to use the college proxy server

Can you ping anything on the college network ?
Can you manually connect to the college login page via it's IP address ?

1. Please disable IPv6 and reboot:
```
sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
sudo depmod -a
```
2. Please post output of **ifconfig eth1**
3. Please post output of **lspci | grep Eth**
4. Please post output of **route -n**
5. Please post output of **cat /etc/resolv.conf**
6. Please post output of **cat /etc/network/interfaces**
7. Please post output of **cat /etc/dhcp3/dhclient.conf**
8. Please copy **entire** output of Windows **ipconfig /all** command here

---

