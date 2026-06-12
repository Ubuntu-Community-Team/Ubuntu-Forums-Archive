---
title: "LAN not working"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by farhanakram on 2011-10-15
I am currently using Ubuntu 11.04. I use university lan so i normally connected using network manager with manual network setting. However, in order to connect to broadband,i run pppoeconf command. I could connect to broadband but afterwards i am ubable to connect my lan. I hav run lshw command and it can detect my ethernet card. I configured network settings in /etc/network/interfaces also.However on running sudo /etc/init.d/networking restart:it says 
SIOCADDRT:No such process 
Failed to bring up eth0
I hav tried every damn possible method bt still unable to get through dis problem...

---

### Post by tonybsa on 2011-10-15
> **farhanakram said:**
> I am currently using Ubuntu 11.04. I use university lan so i normally connected using network manager with manual network setting. However, in order to connect to broadband,i run pppoeconf command. I could connect to broadband but afterwards i am ubable to connect my lan. I hav run lshw command and it can detect my ethernet card. I configured network settings in /etc/network/interfaces also.However on running sudo /etc/init.d/networking restart:it says 
SIOCADDRT:No such process 
Failed to bring up eth0
I hav tried every damn possible method bt still unable to get through dis problem...
Sorry do't have an answer but do have the same error message!
Ubuntu 10.04 server 
I have two NICs eth0 -- 192.168.0,3 and eth1 IP from DHCP.
Can connect to local LAN (using NFS and Samba)

Server can connect to Internet

Other PCs on the LAN can not connect to Internet but can connect to server.

Router on 192.168.0.1 
Have tried every google info I can find. All http, tcp, smtp ports (22,25,53,143,etc) are shown as open

---

