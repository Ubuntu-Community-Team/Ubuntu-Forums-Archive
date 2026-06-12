---
title: "How to specify a proxy for Update Manager"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by Vincoor on 2009-03-09
I use a proxy for web surfing and I'd like to specify that Ubuntu's Update Manager use it also. How do I accomplish this?

Thanks in advance.

---

### Post by kestrel1 on 2009-03-09
If you set up the proxy setting under System -> Preferences -> Network Proxy It should work with Update Manager.

---

### Post by Vincoor on 2009-03-09
Thanks!

I used to manually specify the proxy for Firefox in its preferences, but I now see that I can also simply specify that FF use the system proxy.

It then occured to me that since FF doesn't default to the system proxy, like Update Manager does, there might be other programs that also default to a direct connection in spite of the system proxy setting.

Is there a way to absolutely prevent any and all connections that don't want to go through the system proxy (hopefully with a usefull error message if one tries)?

I'm thinking in terms of preventing all potential clever "man-in-the-middle" type exploits.

---

### Post by Woodsyx on 2009-03-09
> **Vincoor said:**
> Thanks!

I used to manually specify the proxy for Firefox in its preferences, but I now see that I can also simply specify that FF use the system proxy.

It then occured to me that since FF doesn't default to the system proxy, like Update Manager does, there might be other programs that also default to a direct connection in spite of the system proxy setting.

Is there a way to absolutely prevent any and all connections that don't want to go through the system proxy (hopefully with a usefull error message if one tries)?

I'm thinking in terms of preventing all potential clever "man-in-the-middle" type exploits.


Firestarter is a firewall app in the repos that allows you to set up custom policy's for in and out connections.

MoBlock is another program you could try, it's designed to blacklist ip's for torrenting but could work for you too since it allows custom black lists. Also has a .deb. [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

---

### Post by kestrel1 on 2009-03-10
Firestarter is just a GUI for the built in iptables firewall, but is useful for setting up the firewall.

---

