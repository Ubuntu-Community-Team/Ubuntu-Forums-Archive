---
title: "how do I change static IP?"
date: 2013-04-07
forum: Networking &amp; Wireless
---

### Post by user201304 on 2013-04-07
I did this on my Ubuntu Server box a while ago but forgot how to do it. 

The machine was assigned a static IP 192.168.2.x.
Then I got a new modem/router and it now uses 192.168.1.y for the network.

How do I assign a new static IP to my Ubuntu Server?

---

### Post by SeijiSensei on 2013-04-07
Edit /etc/network/interfaces.

---

### Post by papibe on 2013-04-07
Hi user201304. Welcome to the forums ):P

In the Ubuntu server edition you edit the file /etc/network/interfaces

Let us know if you need more help with that.

Come here often and have fun.
Regards.

---

### Post by Iowan on 2013-04-07
That'd be one advantage of using a static *lease* (on the DHCP server - AKA router) - but you'd still end up editing files...

---

### Post by user201304 on 2013-04-07
Ok I'm connected again, thanks!

> **Iowan said:**
> That'd be one advantage of using a static *lease* (on the DHCP server - AKA router) - but you'd still end up editing files...

How does the static lease work? I used a static IP because it's easier to work with that locally instead of having to find the new IP every now and then.

By the way, would you happen to  know how to change the port number for Apache? Last time I also  changed the port number on the web server, so that in order to access it  I have to type [http://address:1234](http://address:1234) instead of just [http://address](http://address) (and again I've forgotten how to do it)

---

### Post by Iowan on 2013-04-07
> **user201304 said:**
> 
How does the static lease work?Many (not all) routers with built-in DHCP server let you set up Reserved Addresses - based on a machine's MAC address. The machine is configured to use DHCP, but receives the same address each time.

The [Server Guide]("https://help.ubuntu.com/12.04/serverguide/httpd.html")  has information on changing the port:> The Listen directive specifies the port, and optionally the IP address, Apache2 should listen on. If the IP address is not specified, Apache2 will listen on all IP addresses assigned to the machine it runs on. The default value for the Listen directive is 80. Change this to 127.0.0.1:80 to cause Apache2 to listen only on your loopback interface so that it will not be available to the Internet, to (for example) 81 to change the port that it listens on, or leave it as is for normal operation. This directive can be found and changed in its own file, /etc/apache2/ports.conf

---

### Post by user201304 on 2013-04-07
> **Iowan said:**
> Many (not all) routers with built-in DHCP server let you set up Reserved Addresses - based on a machine's MAC address. The machine is configured to use DHCP, but receives the same address each time.

My new router has that feature and it works, thanks for the tip.

> The [Server Guide]("https://help.ubuntu.com/12.04/serverguide/httpd.html")  has information on changing the port:

I changed 
/etc/apache2/ports.conf
 and
/etc/apache2/sites-enabled/000-default 
to listen to the same ports, restarted the service, and it seems to work.

Thanks guys!

---

