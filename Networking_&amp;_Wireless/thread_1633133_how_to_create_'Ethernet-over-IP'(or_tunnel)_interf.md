---
title: "how to create 'Ethernet-over-IP'(or tunnel) interface?"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by winetmks on 2010-11-28
Hi,
I'm trying to create EoIP interface on ubuntu so i can create a simple tunnel to my mikrotik router. Is there anyone know how or even done that? If EoIP is not possible, is there any other simple way? 

I had already read and thought about doing it with OpenVPN, but when I read the community documentation for OpenVPN on ubuntu 10.10, I fear it won't connect the tunnel to mikrotik OpenVPN server, since OpenVPN on ubuntu uses 2 certificate and 2 key files(as i read on the docs), but mikrotik configuration, i can see only 1 certificate can be applied on. This confuses me and make me decide to use EoIP(but i can't find any tutorial/docs about it). I don't actually need the encryption and security, i just need to create a tunnel for ubuntu and mikrotik.

any idea?

Thanks for helping me:popcorn:

---

### Post by redmk2 on 2010-11-29
> **winetmks said:**
> Hi,
I'm trying to create EoIP interface on ubuntu so i can create a simple tunnel to my mikrotik router. Is there anyone know how or even done that? If EoIP is not possible, is there any other simple way? 

I had already read and thought about doing it with OpenVPN, but when I read the community documentation for OpenVPN on ubuntu 10.10, I fear it won't connect the tunnel to mikrotik OpenVPN server, since OpenVPN on ubuntu uses 2 certificate and 2 key files(as i read on the docs), but mikrotik configuration, i can see only 1 certificate can be applied on. This confuses me and make me decide to use EoIP(but i can't find any tutorial/docs about it). I don't actually need the encryption and security, i just need to create a tunnel for ubuntu and mikrotik.

any idea?

Thanks for helping me:popcorn:

You could start [**_here_**]("http://www.mikrotik.com/testdocs/ros/2.9/interface/eoip.php").

---

### Post by winetmks on 2010-11-29
to set EoIP on mikrotik, is already familiar to me. But not to ubuntu server. And that's what i'm asking if it is possible.

---

