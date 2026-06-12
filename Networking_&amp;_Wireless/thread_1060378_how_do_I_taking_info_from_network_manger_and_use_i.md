---
title: "how do I taking info from network manger and use it to interfaces file"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by sam1948 on 2009-02-04
or resolve.conf file
or any other files that are required to set the network

---

### Post by Iowan on 2009-02-04
Network Manager essentially bypasses (and ignores) /etc/network/interfaces.  If you use DHCP, it can affect what is in /etc/resolv.conf.  Another recent "discovery" is [here]("http://http://ubuntuforums.org/showthread.php?t=971064").

---

### Post by sam1948 on 2009-02-05
i know it does but it must be using some setting that i can use 
if i choose not use network manager 
i would like to collect that data 
is there any good way to do that?

---

### Post by Iowan on 2009-02-05
**ifconfig** should provide most information. **route** will let you decode the gateway.  As you mentioned, **resolv.conf** will show DNS server(s). What other info would you like?

---

### Post by sam1948 on 2009-02-06
i want the setting for a wireless connection in my university
it's a dynamic wep with peap version 0 and so on 
the nm-manger resets every time it is shut down and i would like 
to write every thing into static files

---

