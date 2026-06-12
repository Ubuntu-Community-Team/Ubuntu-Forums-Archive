---
title: "How to make changes stick to /etc/resolv.conf ..."
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by grndslm on 2009-02-08
How do I do it?  resolv.conf keeps getting written over by NetworkManager I think, telling my desktop that the router is the dns server.  How can I do it the "old fashioned way".

---

### Post by punx45 on 2009-02-08
> **grndslm said:**
> How do I do it?  resolv.conf keeps getting written over by NetworkManager I think, telling my desktop that the router is the dns server.  How can I do it the "old fashioned way".

are you getting an IP through DHCP?   it is probably overwriting the settings every time it leases an IP from the router.

also, is this giving you problems?   i have my router set as my nameserver on my system and it works fine.   it just uses the DNS settings in the router.

---

### Post by grndslm on 2009-02-08
Yes, my router sends me the DNS server of my choice, but I want all of the Ubuntu builds I create in the future to look at only OpenDNS servers -- 208.67.222.222 && 208.67.220.220.

Is it that simple to set my resolv.conf file and have it stick?!  Shouldn't it be very simple?!?

---

### Post by punx45 on 2009-02-08
you will probably have to give each system a static ip then.

---

### Post by yknivag on 2009-02-08
Could you configure your router to forward DNS to the OpenDNS servers (as opposed to those supplied by your ISP)?  Then DHCP would provide your router address for DNS which would in turn forward to OpenDNS...

---

### Post by ciscosurfer on 2009-02-08
Go here: [http://www.opendns.com/select_network_type.php?p=start](http://www.opendns.com/select_network_type.php?p=start)

---

### Post by grndslm on 2009-02-08
> **ciscosurfer said:**
> Go here: [http://www.opendns.com/select_network_type.php?p=start](http://www.opendns.com/select_network_type.php?p=start)

Muchos gracias, senor!  I will definitely try those suggestions when i return to mi casa.

---

### Post by punx45 on 2009-02-08
yeah you can do that to.   for some reason i was thinking that you wanted the ISP DNS on the router, and Open DNS on the Ubuntu machines... hah.:biggrin:

---

### Post by HermanAB on 2009-02-08
Note that the resolvconf daemon can also overwrite the resolv.conf file.  So, while you are at it, stop the resolvconf and avahi-daemon servers if they are running.

Cheers,

Herman

---

### Post by grndslm on 2009-02-08
> **HermanAB said:**
> So, while you are at it, stop the resolvconf and avahi-daemon servers if they are running.
Care to explain what these 2 daemons do??  avahi doesn't have any other purpose?

---

### Post by grndslm on 2009-02-09
Buuummp.

---

### Post by Iowan on 2009-02-10
**man** pages can provide some information, 
Wikipedia has descriptions, too. 
[http://en.wikipedia.org/wiki/Resolvconf]("http://en.wikipedia.org/wiki/Resolvconf")
[http://en.wikipedia.org/wiki/Avahi_(software)]("http://en.wikipedia.org/wiki/Avahi_(software)")
[http://www.noah.org/wiki/Resolv.conf]("http://www.noah.org/wiki/Resolv.conf")

---

### Post by puppywhacker on 2009-02-10
and to make the changes stick, you can probably get away with setting the file rights to read-only. Preventing anything to overwrite the file

sudo chmod a-x /etc/resolv.conf

---

