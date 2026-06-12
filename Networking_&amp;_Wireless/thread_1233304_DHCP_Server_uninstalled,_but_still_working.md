---
title: "DHCP Server uninstalled, but still working"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by Vitani on 2009-08-06
I was having some trouble setting up my DHCP server (it was failing to restart - "Can't bind to dhcp address: Address already in use") on my Mythbuntu server, so with the intention of starting over I did

```
sudo aptitude remove dhcp3-server
```

then disabled a client PCs ethernet card, re-enabled it, to make sure DHCP was not working. However it still got an IP address! I had disabled the DHCP server on my router, so I have no idea where the client got it's IP from, but my guess is there is another DHCP server running on my Mythbuntu Server.

Anyway, I'm pretty much at a loss as to move forward now, so I'm hoping one of you lovely people can point me in the right direction.

---

### Post by Iowan on 2009-08-06
If the client is Ubuntu, you can try **sudo dhclient <iface>** from a terminal... that should let you see if the DHCP server is responding - or if machine is just keeping previous address.  You can also check **ps -ef |grep dhcp*** on the DHCP server to verify that */usr/sbin/dhcpd3* is not running.

---

### Post by cariboo on 2009-08-07
Make sure the dhcp server is not running:

```
sudo /etc/init.d/dhcp3-server stop
```

Then completely remove it:

```
sudo apt-get purge dhcp3-server
```

---

