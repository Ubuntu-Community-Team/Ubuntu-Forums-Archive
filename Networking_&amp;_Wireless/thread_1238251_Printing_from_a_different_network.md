---
title: "Printing from a different network"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by newcolour78 on 2009-08-12
Hi all,
  I am trying to configure my office printer on my laptop computer. I am connected to the general wireless network of my university and I would like to be able to send jobs to my office network printers. 

How can I do that? I have the ip address and dns of the printers, but I can't figure out how to tell ubuntu to go look for them in that particular network. 

I use Intrepid.

Thanks very much,
S.

---

### Post by superprash2003 on 2009-08-12
is this over the internet or LAN?

---

### Post by jonobr on 2009-08-12
Hello


Have you tried using the wizard?

System admin-> printing-> new

It then searches for printers and then allows you to enter target IP and port number.
The drivers may be listed, but you need to figure from your sysadmin the port number in use and if you can print from the nw your on.

---

### Post by newcolour78 on 2009-08-13
Hi guys, thanks for the replies. 

AFAIK the sysadmin has given our group a range of ip addresses, we have a dns server and the printers have fixed ip addresses. 

The printers are both HP laserjets, the drivers are listed.

If I give the wizard the ip address of the printer and check the correct driver, it still says it is not connected. There is no way to specify the dns server, though. 

I am not really an expert of networking, so please ask any information that may be useful to figure out how to get this to work. 

Cheers

---

### Post by Fatman_UK on 2009-08-13
If the laptop and printer are on different networks, it might be tricky to get them communicating. Try asking your network admins to give you a VPN connection (and a lesson in using it). The VPN connection will put your laptop on the same network as the printer, and you will be able to set up your printer as easily as you did in your office.

---

### Post by jonobr on 2009-08-13
Can you ping the printer?

Did the admin giive you the port number you should be using to connect?

---

### Post by newcolour78 on 2009-08-13
A quick nmap from one of the network computers tells me the printer listens on the 515 port. However, I cannot ping the printer from my laptop and I guess it is because it is on a subnet. I can do it, of course, from my desktop which is in the network. 

Is there a way to ping from a different subnet?

The VPN idea looks cool, I still have to understand how feasible. It involves begging the sysadmin :)

Cheers

---

### Post by jonobr on 2009-08-13
Hello


You may not be able to ping due to ICMP being blocked,
However, I dont think thats the case here.

I think the connection between the two networks is completely separate and the two networks should not be talking with each other.
Theres nothing special about pinging from one network to the other, so it just sounds as if there are seperate.

Setting up a vpn will defo need your admin to provide you access.
Hows its setup will depend on what their network supports

---

