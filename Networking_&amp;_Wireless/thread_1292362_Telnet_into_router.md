---
title: "Telnet into router"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by Yizi on 2009-10-15
Hi,

I'm trying to telnet into the router but it wont let me, it comes back with a error saying:

```
telnet: unable to connect to remote host: connection refused
```

Anyone has any idea why it came back with this error and how i can connect to the telnet, i used the normal telnet command:

```
telnet IP
```

---

### Post by diesch on 2009-10-15
For some reason the router refuses you to connect.

Are you sure that your router supports telnet login and allows it from the host you try it from and that you used the right IP address?

---

### Post by Yizi on 2009-10-15
No to be honest, good point, its a netgear DG834G

---

### Post by jonobr on 2009-10-15
Not sure of that model
but Im guessing remote telnet login is disabled or only uses something like ssh,
or only allows direct console access.

---

### Post by Yizi on 2009-10-15
Hmm, i'm gonna check on it later, found few websites, it defo has telnet working.

---

### Post by jonobr on 2009-10-15
hello

I found [This interesting link]("http://www.nat32.com/nat32e/htm/dg834g.htm") which discuss that router.

Heres the relevant piece opn telnet activation

> While no direct interaction with the OS of the device is officially supported, at least one enthusiast has discovered a way of gaining shell access via Telnet: 
Enable the Telnet server on the device by clicking this link: [http://192.168.0.1/setup.cgi?todo=debug](http://192.168.0.1/setup.cgi?todo=debug) 
Then start a Telnet client via this link: [telnet://192.168.0.1](telnet://192.168.0.1) 
You can then issue a small set of BusyBox commands to a shell. 
Further details about Embedded Linux running on the DG834G can be found here. 


---

### Post by Yizi on 2009-10-16
Very intresting stuff, this i found away around it from another place but this did the trick as well, thanks guys.

> **jonobr said:**
> hello

I found [This interesting link]("http://www.nat32.com/nat32e/htm/dg834g.htm") which discuss that router.

Heres the relevant piece opn telnet activation

---

