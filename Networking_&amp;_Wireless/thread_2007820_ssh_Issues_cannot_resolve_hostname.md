---
title: "ssh Issues: cannot resolve hostname"
date: 2012-06-21
forum: Networking &amp; Wireless
---

### Post by akkarris on 2012-06-21
There are 3 computers in my work space: 
Castor: Ubuntu
Pollux: Ubuntu
Andromeda: Fedora
I am having trouble connecting from Andromeda to the other two ubuntu computers, Castor and Pollux, using ssh. I can connect from the two Ubuntu computers to Fedora without any trouble using ssh hostname.local. I am able to connect to the Ubuntu computers from the Fedora computer using the Ip addresses however since the Ip address's change I want to be able to use hostname.local instead. Any tips/possible solutions?

---

### Post by lukeiamyourfather on 2012-06-21
If the network is static and has no DNS you can use the /etc/hosts file to associate hostnames with IP addresses.

---

### Post by papibe on 2012-06-21
Hi akkarris.

I'm not well verse in Fedora issues, but this is the process that I would follow.

In order for the zero configuration works (.local), you need make sure that:
[LIST]
[*]The service is broadcasting its own address, and
[*]The zero conf addresses have priority in the process of resolving a name.
[/LIST].
To make sure the process is running in Ubuntu:
```
ps aux | grep avahi
```
you should see the avahi-daemon running.

To check that the zero configuration has priority over dns when resolving names check the file: /etc/nsswitch.conf

It should have a line like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

```
That means that zero conf (mdns4_minimal) is check before consulting your DNS.

I imagine that there should be equivalent to this process on Fedora.

I hope that helps,
Regards.

---

### Post by akkarris on 2012-06-25
Thank you guys for the help all of the ssh programs were running i just needed to edit the hosts file.

---

