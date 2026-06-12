---
title: "Install and configure OpenVNP client"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by stenci on 2009-12-08
I want to configure OpenVPN on my new Ubuntu laptop. 

I already have configured server and clients, all working with Microsoft OS.

I did some searches, and all I found is about how to install and configure the server, and just a few (useless for me) words about the clients.

With the Synaptic Package Manager I installed openvpn, but now... I don't know what to do.

Are the same configuration files that the IT guy gave me for the Windows OpenVPN configuration still good for the Ubuntu version?

How do I configure/start it?

Thanks,
Stefano

---

### Post by stenci on 2009-12-08
In [this page]("https://help.ubuntu.com/community/OpenVPN") is described the configuration of the Ubuntu server and Windows client.

I am trying to configure the Ubuntu client to a Windows server.
I don't have access to the Windows server.
I have the client.ovpn and company.crt files that allow me to connect with a Windows client.

Are the same two files good for a connection from an Ubuntu client?

How do I set the Ubuntu client up?

Thanks,
Stefano

---

### Post by jame86 on 2009-12-12
bump

---

### Post by DGortze380 on 2009-12-12
> **stenci said:**
> In [this page]("https://help.ubuntu.com/community/OpenVPN") is described the configuration of the Ubuntu server and Windows client.

I am trying to configure the Ubuntu client to a Windows server.
I don't have access to the Windows server.
I have the client.ovpn and company.crt files that allow me to connect with a Windows client.

Are the same two files good for a connection from an Ubuntu client?

How do I set the Ubuntu client up?

Thanks,
Stefano

rename client.ovpn to client.conf and put it in /etc/openvpn

/etc/init.d/openvpn restart

---

