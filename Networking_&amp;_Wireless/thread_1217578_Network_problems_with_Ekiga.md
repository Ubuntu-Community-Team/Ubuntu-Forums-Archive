---
title: "Network problems with Ekiga"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by cknight on 2009-07-19
Starting Ekiga gives me the following error message:
```
Ekiga did not manage to configure your network settings automatically. You can still use it, but you need to configure your network settings manually.Please see http://wiki.ekiga.org/index.php/Enable_port_forwarding_manually for instructions
```

Following this link, it suggests that I check with PortForward.com to see how to forward ports for my router.  [This section of the site]("http://portforward.com/english/routers/port_forwarding/3com/3CRWDR101A-75/Ekiga.htm"), based on my router, has the following text:
```
The 3CRWDR101A-75 will not allow you to forward enough ports, to run Ekiga. You should try using the DMZ portion of this router if it is available. Alternatively you can try switching the router to bridged mode. You will need to contact your ISP to switch to bridged mode, so they can make the required changed on their end.
```

Can someone explain to me in plain english what is going on?  I'm running 9.04 behind a 3-com DSL router.  The only DMZ option is "Enable 1-to-1 NAT" which, according to the help, completely exposes my computer to the web with no firewall.  I assume that this is a bad thing?  Changing to bridged mode sounds rather drastic to me (even if I even knew what it was!).

Is my router basically incapable of supporting Ekiga?

---

### Post by cknight on 2009-07-21
OK, if noone knows the answer, can anyone direct me to a decent site explaining routers, port forwarding, NAT and all the other obscure terminology that I need to get my head around?

---

### Post by martinbaselier on 2009-07-21
[http://en.wikipedia.org/wiki/Router](http://en.wikipedia.org/wiki/Router)
[http://en.wikipedia.org/wiki/Port_forwarding](http://en.wikipedia.org/wiki/Port_forwarding)
[http://en.wikipedia.org/wiki/Network_address_translation](http://en.wikipedia.org/wiki/Network_address_translation)

---

### Post by superprash2003 on 2009-07-21
you could enable NAT-DMZ and use firestarter on your ubuntu machine to block all traffic and allow only specific traffic

---

