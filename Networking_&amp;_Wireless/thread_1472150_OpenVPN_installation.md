---
title: "OpenVPN installation"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by dinuzz on 2010-05-04
Hi all

I just installed Ubuntu 10.04 on my server and trying to set up a VPN Service on it. I already installed OpenVPN on it. Now just need to configure it in an appropriate way and create certificates etc. Already tried this on a testing server and worked, but not all the way down as described in the this document: [https://help.ubuntu.com/9.10/serverguide/C/openvpn.html](https://help.ubuntu.com/9.10/serverguide/C/openvpn.html)

Does anyone recommend a better site? Or have a good howto at hand?

My prerequisites are:

Router/Firewall connected to the internet (via Cablemodem). The router/Firewall acts as a DHCP Server. The VPN Server is attached to that LAN and has a static IP Address of 192.168.1.150. My network is reachable from the outside via dyndns.org. I can administer the server via ssh. Do I have to bridge the network interface? I only have one ethernet adapter attached.

Many thanks for all of your thoughts.

Cheers

---

### Post by dinuzz on 2010-05-04
[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)


has just been released...

---

### Post by noway2 on 2010-05-05
Try the following: [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)
and [http://ubuntuforums.org/showthread.php?t=1021592](http://ubuntuforums.org/showthread.php?t=1021592).

---

