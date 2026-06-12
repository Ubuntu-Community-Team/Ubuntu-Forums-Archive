---
title: "Issue with openvpn"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by badbit on 2010-06-25
Hi,
 
I am having a bit of an issue with OpenVPN. I create tap devices as I need ethernet style tunneling.
 
I need to execute commands after a connection has been intialized and packets are in the forward loop.
 
I can use the up and ip-route commands but these execute when the tap device comes up, not when the tunnel has been initialized.
 
Does anyone know of a way I can get a script once a tunnel is connect, not when the tap device is created?
 
Or alternativly, only up the tap device when a connection has been initialised? (I guess this is impossible, as the tap needs to be in place to route udp pings to confirm that the tunnel is active)
 
Any help would be much appreciated.

---

