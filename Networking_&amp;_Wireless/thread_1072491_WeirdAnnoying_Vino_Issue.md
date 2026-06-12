---
title: "Weird/Annoying Vino Issue"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by JohnJackson on 2009-02-17
I have enabled remote desktop in System > Preferences > Remote Desktop on my workstation, but am unable to connect to it from my laptop on my wireless network. No matter what settings I put in it does not seem to work, vncviewer just times out using the command vncviewer 192.168.0.2:0. I have tried different ports.

I have tried enabling this on my laptop and I can successfully access it from the workstation. I can also successfully connect from my workstation to my workstation using the private network address. I can also SSH into my workstation from my laptop over the wireless network. ufw is not enabled on the workstation, and I have not enabled any other firewall myself.

Does anyone have any idea what's going on? Both systems are running Intrepid, and are up to date. Thanks.

---

### Post by JohnJackson on 2009-02-22
Well I've got around it by SSHing into the workstation with X forwarding and running vncviewer locally. More secure but slightly more inconvenient. By the way, the only allow local connections option is not selected.

---

