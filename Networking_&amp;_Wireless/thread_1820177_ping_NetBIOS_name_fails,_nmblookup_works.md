---
title: "ping NetBIOS name fails, nmblookup works"
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by fela on 2011-08-07
Hi

I have a server running Debian 5, but I shouldn't imagine things are too different from an Ubuntu Server. I also have three Windows 7 client PCs as well as an Ubuntu 10.10 client netbook.

All machines are running Samba/Windows file sharing and are joined to the Samba workgroup named WORKGROUP (and of course are part of the same internal network with addresses beginning with 192.168.0).

From any of the Windows 7 machines I can see and access every other machine on the network via its NetBIOS name. That means I can ```
ping netbios_name
``` successfully. In fact, when doing so, an IPv6 address is always returned, something that might be interesting.

However, from the Debian server, findsmb only finds the server and the netbook (the only two Linux machines on the network).

From the netbook, findsmb only displays it and the server, however using nautilus it is possible to access all the machines on the network.

On both Linux machines, nmblookup netbios_name is always successful, however ping netbios_name always fails.

Here is the server's nsswitch.conf hosts line:

```
hosts: files dns wins
```

And here is the netbook's:

```
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4 wins
```

Any idea what the matter could be?

---

### Post by UncleBoxy on 2012-02-18
> **fela said:**
> 
```
hosts: files dns wins
```And here is the netbook's:

```
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4 wins
```Any idea what the matter could be?

Remember that the order matters.  I usually put the 'wins' setting immediately after the 'files' setting.

To mirror your example, I'd set up the configs like so:

```
hosts: files wins dns
``````
hosts: files wins mdsn4_minimal [NOTFOUND=return] dns mdns4
```

Hope that helps.

---

### Post by fela on 2012-02-18
For some reason the issue has fixed itself, even though I didn't change anything. Thanks anyway though.

---

