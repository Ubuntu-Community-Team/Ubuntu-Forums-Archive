---
title: "Cannot access Internet while on vpnc"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by seismicmike on 2009-10-01
I'm having trouble with vpnc. I have it installed along with the network-manager-vpnc package and they are working fine. I am not having any trouble connecting to the VPN. The problem I'm having is that while I'm connected to the VPN, I can't connect to the wider Internet. Google, Wikipedia and more importantly the website I'm trying to build, won't come up.

Can anyone help me figure out what's going on?

Thanks.

PS. This is on Ubuntu 9.04

---

### Post by seismicmike on 2009-10-02
Shameless self bumping.... :)

---

### Post by jt6806 on 2009-10-07
Edit your VPN connection and click the "IPv4 Settings" tab.
Click the "Routes" button.
Select the "Use this connection only for resources on its network" checkbox.

---

### Post by seismicmike on 2009-10-07
Hey whaddya know that worked! Thanks dude!!!

---

