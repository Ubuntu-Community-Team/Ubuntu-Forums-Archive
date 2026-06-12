---
title: "Homepage routed to D-Link router login page on local machines"
date: 2011-05-20
forum: Networking &amp; Wireless
---

### Post by MartinHansell on 2011-05-20
Hi,

[Details of my setup are below.]

In addition to 2 "desktop" machines, I recently set up an Ubuntu Server with Apache2, but when I try to access my [www.homepage](www.homepage) from a machine locally connected to the same router (via both wired & wireless interfaces), I am directed to the Login page of the router, not to the [www.homepage](www.homepage).  Yet, when I access the [www.homepage](www.homepage) from elsewhere, my [www.homepage](www.homepage) is accessible.

I can browse to my [www.homepage](www.homepage) by entering the local IP address into browsers on both local machines, so I know the machines are talking to each other.  Just not letting me get in via normal internet browsing channels.

Got any thoughts?

Martin

Server:  Ubuntu 11.04
Webserver: Apache2
Router:  D-Link DIR-615
IP Address of:  192.168.0.110 (reserved on router, static on server)

Desktop:  Ubuntu 10.10
Network connection: wired - plugged into LAN2 of wireless interface
IP Address: 192.168.0.100 (reserved on router, DHCP on desktop)

Laptop:  Windows 7
Network connection: wireless
IP Address : 192.168.0.102 (DHCP only)

Homepage : [http://hansellfamily.homeip.net](http://hansellfamily.homeip.net) (via DynDNS)

---

### Post by Toz on 2011-05-20
I'm willing to bet that the router admin page port is currently set to 80 and is intercepting the internal requests and routing them to the router admin page.

On the router, try changing the admin port (Tools->Admin->Administration) to a value other that 80.  

Keep in mind, that if you do change it, you will need to enter this new port in the url when you do want to connect to the router. For example, if you change it to 8080, then:```
http://192.169.0.1:8080
``` should connect you to the router (assuming of course that your router is at 192.168.0.1).

---

### Post by MartinHansell on 2011-05-22
> **Toz said:**
> I'm willing to bet...

On the router, try changing the admin port (Tools->Admin->Administration) to a value other that 80.

Thanks for that response - it makes a lot of sense!  I think you might be a rich man now if not for open source!  But when I try to follow your advice, I fall over!  My firmware version is 7.09 and so far I cannot find the place where I change the router's admin-page-port.

Instead of Tools it's now Maintenance.  On the Device Administration page you can allow remote management, SSH and telnet, but not that!  This version is produced by Unifi - our local fibre-optic ISP brand, So I have approached them for some info, but thought I'd open it out here also.

Any more gambles?

And thanks again!

---

### Post by Toz on 2011-05-22
Sorry, I don't own one of these devices, but if this is what the management page looks like now, then in the Remote Management section, make sure the "Enable Remote Management" is checked and change to "HTTP Port" value to something other than 80.

[IMG]http://unifi.athena.my/images/stories/capture2.jpg[/IMG]

---

### Post by MartinHansell on 2011-05-26
Hi Toz,

Yeah that's it!  And I tried that also.... I have tried setting the allowed user/access IP to 

* 129.168.0.110 (my own machine on the network)
* 192.168.0.1 (the routers IP - dun ask me why loh - just experimenting)
* 0.0.0.0 (same - messing only!)

but none of these did the trick... any other thoughts?

Thanks for your input - it's appreciated!

---

### Post by Toz on 2011-05-26
Can you post back a screenshot of your settings?

---

### Post by MartinHansell on 2011-06-03
Hi - sorry i;ve been a bit crazy lately!

I'm not sure how to get my image into this message so I've uploaded it as an attachment...

Thanks.
Martin

---

### Post by Toz on 2011-06-03
Have you rebooted the router and tried connecting to [www.yourdomain.com?](www.yourdomain.com?) With the port set at 8080, are you still getting the admin login page?

---

