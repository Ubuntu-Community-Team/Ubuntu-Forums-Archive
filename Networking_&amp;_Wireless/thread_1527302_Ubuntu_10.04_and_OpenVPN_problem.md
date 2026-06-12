---
title: "Ubuntu 10.04 and OpenVPN problem"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by Ayeld87 on 2010-07-09
Hi there

I've got Ubuntu 10.04 LTS installed with OpenVPN 2.0.1 installed on it as well as ufw, vsftpd and ssh.
Everything works fine and it starts up perfectly but if i enable management in the .conf file for openvpn it won't start up beacuse it says permission is denied.
Weird thing is it works after the first reboot just after installing OpenVPN but not therafter.

It works if I either set the management to 127.0.0.1 on port 7505 but if it set it to the machine's IP address i.e 192.168.5.126 it won't start up on it's own.
The only way then to start the service successfully is with the sudo openvpn start command from a terminal session.

So my question is how can I get the service to start up with sudo priveleges or allow the service to bind that socket to the machine's own address on start-up?

Regards,
Alan

---

