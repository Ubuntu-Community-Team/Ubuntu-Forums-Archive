---
title: "Need help with DNS and DSL connection"
date: 2006-05-08
forum: Networking &amp; Wireless
---

### Post by Rnet2 on 2006-05-08
I want to create a email server that is connected to a DSL connection. How do I configure DNS? So internal machines can send and receive email, and still be able to get out over DSL?

Is there a how-to on creating an email server utilizing two internal machines and a DSL connection to the internet?

Thanks in advance!

---

### Post by mips on 2006-05-08
Does your DSL have a static or Dynamic IP address ?

---

### Post by Rnet2 on 2006-05-12
Normally, when connecting to the dsl router the pc is given a dhcp address. I gave my pc a static address out of range of dhcp.

---

### Post by Rnet2 on 2006-05-12
Normally, when connecting to the dsl router the pc is given a dhcp address. I gave my pc a static address out of range of dhcp.

---

### Post by mips on 2006-05-12
[QUOTE=Rnet2]Normally, when connecting to the dsl router the pc is given a dhcp address. I gave my pc a static address out of range of dhcp.[/QUOTE]

I'm mean the WAN side or ISP side, not the LAN. Does the ISP give you a static or dynamic address. I'm not referring to your PC.

---

### Post by Rnet2 on 2006-05-12
Oops! 
Yes the IP address does change.

---

### Post by Rnet2 on 2006-05-12
Specifically:

For testing we are currently on a lan that is connected to the internet via DSL.
We want to create an email server that can store and forward email from internal clients. 
(not sending email out to the internet)

Once we prove this type of installation, we will remove the server from the DSL network and place it on our corporate netwrok. From their the server will be used strictly as an email gateway. When email needs to leave the network (connects to the internet), Our internal lotus notes server will handle the mail,  from the linux server and send it out through our firewall.

The reasoning is that we have an older system that sends mail to our lotus box. If lotus is down for any reason the system does not store the mail it generates. Hence we want to use linux to store and forward email to lotus notes.

---

