---
title: "Network Configuration: no inet address"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by umeboshi80 on 2010-05-11
Hi,
I have installed the 10.4 server edition and i am connected to a LAN (DHCP server, getting ip automatically). First, during the installation process, the automatic network configuration did not work, so I decided to configure it manually later.

I followed other posts and the server guide and set in the interfaces file:
auto eth0 
iface eth0 inet

(and actually did the same with eth1, the second network card). When I do ifconfig -a I get the output that it seems to be connected but I only see an inet6 address and no inet address. I checked and I cannot ping anything.

I am out of ideas by now as to what needs to be changed to make the network work.

Thanks for any comments.
Hadassa

---

### Post by chili555 on 2010-05-11
> auto eth0
iface eth0 inetDoes the behavior improve if you change it to:```
auto eth0
iface eth0 inet [COLOR="Red"]dhcp[/COLOR]
```Then restart networking:```
sudo /etc/init.d/networking restart
```

---

### Post by umeboshi80 on 2010-05-11
Sorry, that was a typo. Of course I used dhcp in the file as well...
so the problem lies somewhere else.

Any help would be really appreciated...

---

### Post by umeboshi80 on 2010-05-11
That is, why does it get an ipv6 address and not an ipv4 address after specifying inet in the configuration file?

---

### Post by Iowan on 2010-05-11
Though I'm not really acquainted with the IPv6 process, the address seems to appear without a DHCP server. You might try: ```
sudo dhclient eth0
``` and post the results.

---

