---
title: "tftp over router"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by ras123 on 2011-07-19
Hi,
I need to connect my workstation running Ubuntu 11.04 and a beagle board with customized linux. The workstation (ip 192.168.1.2) is connected to a router (ip 192.168.1.1), and the router is connected to beagle board (ip 192.168.1.2). 
How configure the tftp-hpa? I found at ubuntu community ([https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)) documentation, but the file is different in my pc at the location /etc/default/tftpd-hpa
> # /etc/default/tftpd-hpa

TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/var/lib/tftpboot"
TFTP_ADDRESS="192.168.1.2:69"
TFTP_OPTIONS="--secure"I configured it as shown above, but it is not working!! any help please.
Thanking you,
Ras

---

