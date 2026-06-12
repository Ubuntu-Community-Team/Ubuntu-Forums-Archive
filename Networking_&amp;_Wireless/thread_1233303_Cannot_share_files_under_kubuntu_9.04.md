---
title: "Cannot share files under kubuntu 9.04"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by henry83 on 2009-08-06
I have tried to share files in a LAN between two computers under kubuntu 9.04 32 bits with no success when I click on "configure file sharing" nothing happens. Any idea to solve this problem?

---

### Post by Kubunteando on 2009-08-06
No, but I use the ssh server (openssh-server package).
I installed that package and then I can connect to the remote computer just by writing in Dolphin navigation bar: sftp://<IP address OR name of the remote machine - the name only works if the DNS can resolve it or if you have it in the host file)

To write in Dolphin navigation bar just right-click on it and select Edit, then you will be able to write.

SSH is more secure (it is an encrypted transfer) so you can even use it to transfer files through the Internet.

---

### Post by henry83 on 2009-08-06
Thanks your advise worked to get files from a computer located in an office that is not in my LAN but I could not use it in my LAN it doesn't work, Samba works fine though when one computer is with Windows XP. What I can't do is to access to my other computer in my LAN when both  are running kubuntu.

---

### Post by superprash2003 on 2009-08-07
it should work via LAN as well , just enter the local LAN ip instead of the WAN ip

---

