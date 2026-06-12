---
title: "Ubuntu DHCP server?"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by McRat on 2010-05-19
I have a small network with about 10-15 devices using it, some are Linux, most are Windows.  The fileserver is a Ubuntu 10-04 32bit  machine.

How do I make the Ubuntu the DHCP server?

Is there such a thing as a backup DHCP server?  In other words, could there be a device or machine that takes over the DHCP duties if the primary fails?


Last, if I were a masochist...  

Could I turn off all DHCP services and use fixed local IP's?

---

### Post by BoneKracker on 2010-05-19
You install and configure a dhcp server (e.g. ISC DHCP).

However, I think the best option for a small network is dnsmasq, which functions as a dhcp server and a dns server integrated together in one.  The upshot of this is that you get dynamic dns (you get name resolution on your local network, without having to clog your network and bloat your machines with ridiculous and insecure "zeroconf" stuff like noisy Avahi.  All the machines on your network, including Widnows, use DNS for name resolution.  Windows also uses WINS for some of it's Windowsy stuff (file and printer sharing), and you can tie that into your dns name resolution by running Samba and having it act as a WINS proxy (it's a one-line entry in Samba).

One school of thought is that zero-configuration networking (like Avahi) is the way of the future as more and more devices become mobile, etc..  Another school of thought is that it's insecure, inefficient, and forgoes the opportunities for centralized management provided by dhcp/dns servers.

Yes, you can have a backup dhcp server, but the complexity of doing so makes it atypical for a small network.  More common (and pretty easy) is to configure the clients themselves to "fall back" to using the dhcp lease they have, then fall back to a predetermined static address or an APIPA address (which is good enough for internal networking).

Yes, you could easily use static addresses for all your machines. You provide name resolution by putting the hostname-to-address mapping in the /etc/hosts file of each computer.  There's a similar file on Windows but I forget what it's called.  Using static addresses might be a good place for you to start learning about networking, if you're very unfamiliar with it, before delving into dhcp and dns.

But dnsmasq is great for a small network and you might just want to try it.

---

### Post by bab1 on 2010-05-19
> **McRat said:**
> I have a small network with about 10-15 devices using it, some are Linux, most are Windows.  The fileserver is a Ubuntu 10-04 32bit  machine.

How do I make the Ubuntu the DHCP server?

Like [**_this _**]("http://www.madboa.com/geek/dhcp-failover/")if it is a ISC DHCP3 Server.> 

Is there such a thing as a backup DHCP server?  In other words, could there be a device or machine that takes over the DHCP duties if the primary fails?

Yes, the above explains that too.> 

Last, if I were a masochist...  

Could I turn off all DHCP services and use fixed local IP's?

If you are the admin and the hosts don't move out of the LAN this is the most stable method.  Set it once and never think about it.  On the other hand if you have laptops and other devices then you will have to use DHCP or heaven forbid; rely on Avahi.

---

### Post by McRat on 2010-05-19
Thank you!  Now I know where to start.:)

---

