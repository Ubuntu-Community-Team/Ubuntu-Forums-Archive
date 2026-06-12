---
title: "Connecting remotely to server via SSH and 2 routers."
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by nitindb on 2009-02-02
I have set up a small Linux based network made up of 1 headless Ubuntu server, 2 laptops and 2 desktops and 2 routers (1 adsl and 1 wireless).  The local IP address of ADSL modem is 192.168.0.1 and the same for Wireless router is 192.168.1.1.

The server is administered using secure shell (OpenSSH) through a non-standard SSH port (eg.2233).  SSH-ing within my local network is not a problem, but I am not sure how to SSH from outside my local network.  I have a static public IP address and don't seem to have any firewall issues.  

Firstly, I am not sure of the correct syntax?  The syntax I am using when connecting locally is:- ssh -p 2233 servername@192.168.0.100.  What syntax do I use when I want to connect remotely? 

Secondly I am not sure how or what ports I am supposed to forward, if any?  I need this to work as I want to be able to connect to my office network from home and also from abroad.  Can any of you bright chaps guide me with this?

Regards,

Nitin DB

---

### Post by cariboo on 2009-02-02
It's pretty simple really you have to port forward from your server to the router. I assume the server ip address is 192.168.0.100 so you would have to forward that ip address to port 2233 on the router.

To check if you have set port forwarding correctly go to [canyouseeme]("http://www.canyouseeme.org/").

Jim

---

### Post by nitindb on 2009-02-02
Problem is that there are two routers one with an ip address of 192.168.0.1 (Wireless) and another with 192.168.1.1(ADSL).  Also I am not sure of the syntax where remote SHH-ing is concerned?  For local SSH I am using:-
ssh -p 2233 servername@192.168.0.100.  But when at home, what do I use to log into the server at my office, given that local IP address would be of no use outside the LAN?

---

### Post by Neural oD on 2009-02-02
you would have to know the external ip of your network

---

### Post by nitindb on 2009-02-02
I know the static Public IP of the network.  I had ordered a static public IP from my ISP and I have the number which is something along the lines of:- 52.122.xxx.xxx.  Is this what you mean by external IP address?

---

### Post by kevdog on 2009-02-02
If from inside your network, you visit showmyip.com or similar page it will show you the external address.  As far as the two router bit, do you need to make 2 hops from the outside to get to your server?

---

### Post by nitindb on 2009-02-02
I know my external IP address.  But I am not sure whether I need to make two-hops from the outside to get to my server, I am not sure.  How do I find this out?

---

