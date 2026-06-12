---
title: "Wireless Encrypted network conection problem."
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by adrian05 on 2009-02-19
Hello. I'd like to appologise for my bad english first.
I'm using Ubuntu 8.10 and NetorkManager to connect to my university encrypted network. I installed the Broadcom wireless drivers which came with Ubuntu(I was asked if I want to install then as soon as I first entered Ubuntu). it connects to non-encrypted wireless networks with no problems. But when I try to connect to the wireless encrypted network, it keeps asking for Authentification. I think the problem is that it asks for the second certificate(client cert), but NetworkManager 0.70 has no option for setting the path to the second cert, using eap = TTLS(I allready inputed the CA certificate but I have 2 certificates: CA and client certs).Can I use a config file for network manager to set the path for the second cert?
Settings for "wlstud": Screenshot.jpg (attached)
When connecting to wlstud after few secconds appears: Authentication.png (attached).
<code>
adrian@ubuntu:~$ lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
<code>


Please, if someone has some ideeas, please help me. Thank you.

---

