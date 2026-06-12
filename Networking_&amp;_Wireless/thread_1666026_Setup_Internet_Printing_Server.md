---
title: "Setup Internet Printing Server"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by hyapadi on 2011-01-13
I'm planning to setup a secure Internet Printing Server at location A so that I could remotely print from location B.

Is there any tutorial for this? I'm new into this.

FYI, I have successfully setup the printer for local printing as well as local network printing.

But haven't tried with Internet Printing since I'm still don't understand how to setup it, especially with the security part. I would like to have simple authorization such as user/password rather than the complicated one.

---

### Post by garvint on 2011-02-01
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/cups.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/cups.html)

this looks a lot easier than setting up ssh, just forward the port on your router (normally done through a web browser address to your router), open a port address say 5555 for example to the specific computer name or ip address of the ubuntu pc,

then on ubuntu machine run:

sudo apt-get install cupsys cupsys-client

after you edit:

/etc/cups/cupsd.conf

to listen to the ip address and port address of your static.dynamic ip address of your network:


Listen 127.0.0.1:631           # existing loopback Listen
Listen /var/run/cups/cups.sock # existing socket Listen
Listen 192.168.10.250:5555     # Listen on the LAN interface, Port 631 (IPP)


I think that is it. It is fully explained on the link above.

---

