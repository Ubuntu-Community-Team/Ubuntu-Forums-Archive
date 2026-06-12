---
title: "cannot connect to a webservice from ubuntu 10.04"
date: 2011-08-15
forum: Networking &amp; Wireless
---

### Post by bobdobbs on 2011-08-15
This one is weirding me out.

I have a hosting account with hostgator. They have cpanel access, which is accessibly at hostname.com:2082

I actually contacted hostgator first, and they said that there was nothing wrong on their end. I can still normally use the other services on the host I have with them: I can connect to their ssh daemon and can see my site on their host with my browsers.

I have two computers on my local network. A desktop and a laptop, both running ubuntu. Desktop runs 10.04. Lappy runs 11.04. Both computers are on the same hub and router. They both have the same gateway and the contents of their resolv.conf is identical.

I can connect to myhost.com:2082 via my laptop, but not my desktop.

There is no proxy setup on my desktop. I get the same results on every browser, and whether or not ufw is enabled or disabled.

Firefox tells me:

"Firefox can't establish a connection to the server at myhost.com:2082." Not other browser can connect either. 

From the commandline, I used 'GET myhost.com:2082'.
500 Can't connect to myhost.com:2082 (connect: Connection refused)

I tested a couple of http monitering plugins for firefox. When I make a request to, say, google, I can see http headers being issued. But none are visible when I request from myhost.com:2082.

I fired up wireshark. When I request service from myhost.com:2082, no http headers leave eth0.
This makes me think that I have a networking issue on this machine.

How do I diagnose further?

---

