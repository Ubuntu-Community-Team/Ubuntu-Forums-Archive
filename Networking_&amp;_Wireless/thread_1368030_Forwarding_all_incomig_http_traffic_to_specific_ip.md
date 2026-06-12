---
title: "Forwarding all incomig http traffic to specific ip"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by qwer995 on 2009-12-30
Hi everybody ...
I setup a PPTP vpn server on my office network successfully and People can connect to the server and everything works fine. But I do not want to let them to use port 80 and protocol HTTP. So I want when they open their web browsers and entering an web site address automaticlly redirecting them to specific ip adrress (for example 192.168.10.10 which in this machine I installed apache server.) 
So how I can forward all incoming traffic to that specific IP address ?

---

### Post by SlugSlug on 2009-12-30
surley you cant - if the client has net acess to open the VPN - then they have net access to access HTTP via the client, if they are using VPN to then remote into severs then you could control it but only that remote session not the client it self.

To control the remote session you'd probably want a proxy (squid)

---

### Post by qwer995 on 2009-12-30
> **SlugSlug said:**
> surley you cant - if the client has net acess to open the VPN - then they have net access to access HTTP via the client, if they are using VPN to then remote into severs then you could control it but only that remote session not the client it self.

To control the remote session you'd probably want a proxy (squid)

They do not have directly access to internet. I create for them some user name and password and by this user name and password they can connect to vpn server and then they can see web pages .But  how I can setup a proxy server ? may you show me a tutorial ?

---

### Post by SlugSlug on 2009-12-30
to get round that though - on the client they just need to set the browser settings to no proxy. As they already have net connection...


Google Squid how to there are loads...

---

