---
title: "Bypass OpenVPN"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by eldaria on 2010-04-30
On my Ubuntu Server I use an OpenVPN client connection to an external VPN provider. 
I use this connection to bypass my ISP who is blocking servers, for example port 80. 

However this has the downside that my servers connection to the Internet is limited to the bandwith of my VPN provider. I subscribe to a 10 Megabit VPN tunnel but my ISP connection is 100 megabit.
So if I download something from the server with the VPN connection active I get only 10 Megabit. 

Is there a any way of selectivly use the VPN while it is active? For example by specifying what services should use the VPN for example Apache, or the oposite, specify what applications should not use the VPN but connect directly?

---

### Post by eldaria on 2010-04-30
Ok I found a solution that works.
I added a separate route to enable it to bypass the VPN connection.
Not really what I wanted, but it works.

---

### Post by wildmanne39 on 2013-03-28
Thread closed. Please do not post in old threads.

---

