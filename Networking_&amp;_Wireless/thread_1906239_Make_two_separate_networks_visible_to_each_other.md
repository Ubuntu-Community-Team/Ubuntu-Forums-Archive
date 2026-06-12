---
title: "Make two separate networks visible to each other"
date: 2012-01-08
forum: Networking &amp; Wireless
---

### Post by ubuserve on 2012-01-08
Hi All. New here, please be gentle...:-).. Being a complete newbie… I am stuck… My setup is the following: an ISP modem provides me with the internet connection; an Ubuntu server is wired directly to the modem; a netgear wireless router is also wired directly to the modem; 4 laptops (3 running windows 7) and 1 running lubuntu connect wirelessly to the netgear router. All computers (i.e. the 4 laptops and the Ubuntu server) have internet access. 
  The Ubuntu server has an ip address 192.168.1.10; the netgear router is at 192.168.1.11. All laptops have ip addresses in the range 10.0.0.2 – 10.0.0.8.
  I want to use the Ubuntu server (with a 2tb hard disk) as a common shared storage for all the laptops. I have been trying to set up SAMBA but cannot make the laptops see the smb shares. I suspect that my problem is that the laptops and the server are on different networks (192.168.1.1 and 10.0.0.1, respectively) and therefore cannot see each other. I cannot ping the server from the laptops and vice versa. 
  Could anybody please help me with the setup. Does my problem have anything to do with ip forwarding? Is it something else? The more I read the more confused I get since I am not an IT guy…

---

### Post by Doug S on 2012-01-08
Hi and welcome to Ubuntu forums. And thanks for your very complete description of your network and issue.
 
Myself, I would setuup the netgear wireless router as a switch instead of a router. That would put your laptops and lubuntu on the same local sub-net as your ubuntu server.
 
Now. to answer your actual question: Yes, your current problem is related to needing port forwarding properly setup on your netgear router. Edit: however this would be a difficult port forwarding problem as it would be backwards from the normal way (I think). Edit 2: The more I think about it, the more I don't think this forwarding issue can be done with a typical bought router. It could be done with iptables.
 
Let us know how you want to proceed and we'll help further.

---

