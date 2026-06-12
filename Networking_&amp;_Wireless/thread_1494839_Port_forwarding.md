---
title: "Port forwarding"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by kumarldh on 2010-05-27
Hi,

I am not sure if this is the right place to ask this question. I have following setup at my home.

A broadband modem is connected to a WiFi Netgear ADSL router and my laptop connects to internet using the WiFi.
The modem has ip in the range of 192.168 and the IP allocated to my modem is public ip. My laptop has ip 10.0.0.2 and runs Ubuntu. Now what I want is to forward my laptop's port 80 or webserver to the modem's public ip or other way around so that I can have an IP pointing to my laptop and run a web server. Any clues?

---

### Post by Iowan on 2010-05-27
I'm a bit unsure, but either the modem or the router (or both?) will need to be configured to port-forward. If the laptop gets a DHCP address, you may want to either set up a static address on machine - or static lease on DHCP server (router?). Unless your ISP provides you with a static address, you may need a service like no-ip.com or dyndns.com.

---

### Post by lisati on 2010-05-27
My preference is to use my router(s) to handle things like internal IP allocation (i.e. control the IPs on your local network) and port forwarding. On your router's web-based control panel, there should be an option to set up both. My Netgear router calls the IP address allocation "address reservation".

---

