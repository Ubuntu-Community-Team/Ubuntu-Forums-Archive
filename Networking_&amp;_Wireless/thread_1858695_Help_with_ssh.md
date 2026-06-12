---
title: "Help with ssh"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by Waio on 2011-10-12
Hello, I know this has probably been posted to infinity, but I can't seem to find any problem like mine in the forums:

 I installed ssh server on a netbook at home, it's running lubuntu 11.04.

 After a while (maybe after upgrading from 10.10), ssh stopped working, and as of now, I cant connect even from my local network, which made me think i had to unblock the port from the firewall (ssh'ing into localhost works), so I did, and iptables -L -n is allowing connections to port 22 from both udp and tcp, however, I still can't connect from other computers.

 Maybe I'm missing something in the chain, any tips would be appreciated

---

### Post by Dangertux on 2011-10-12
If you upgraded the machine it is on but it still has the ip address the host key will not match up. On the client machines you need to remove the following file.

/home/username/.ssh/known_hosts

replace username with your username.

This will prompt you to accept the new key when you login to the server and then should allow you to log in.

Hope this helps.

---

