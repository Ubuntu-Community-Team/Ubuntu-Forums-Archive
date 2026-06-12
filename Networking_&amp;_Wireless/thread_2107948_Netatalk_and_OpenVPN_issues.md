---
title: "Netatalk and OpenVPN issues"
date: 2013-01-23
forum: Networking &amp; Wireless
---

### Post by dragao-azul on 2013-01-23
Hello,

I've been trying to configure a backup server which I can access through VPN, so I've setup OpenVPN, Samba and Netatalk (3.0.2) on an ubuntu 12.04 system.

I've tested the system with my MacBook running time machine from the laptop to the server and (although slow) it works "fine".

But I get some problems:

The first one is something to do with the VPN (I'm using a tap device and UDP protocol with tunnelblick on OS X). After some time (when I leave the computer backing up overnight) the VPN appears to be connect according to tunnelblick but no data is transmited. Then I can't disconnect and my network settings get all messed up (I'm not even able to connect to the internet using my local connection) and I have to reboot the computer.

The second one is with netatalk: Most of the times I try to backup (when the computer has been offline for a while) I have to restart the netatalk service on the server or else the volumes appear but time machine stays stuck on "looking for backup disc".

Any suggestions on how to solve this? This might be a dumb question but since I'm new at this, which logs should I look at?

Thanks!

---

