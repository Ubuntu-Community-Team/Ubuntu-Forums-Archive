---
title: "Need Advice  and Counsel on Firewall Setup"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by paddydd on 2009-03-30
Hi,
  First of all I would like to say thanks to all of the people in this community. I have learned a great deal from the vast library of postings on this forum and those folks that are involved provide a very benficial service.
  
My only difficulty it seems is with firewalls and security. So I have a few questions.

 1. Many people have stated that the default setup of UBUNTU is locked down. I take this to mean that all ports but 80 have been turned off. I am using 8.10 but I am not using SElinux. Is this a correct interpretation?
 2. There is one user on this box and the password is moderately cryptic (numbers, letters and special characters). If the only port open is 80 (per Q1) then how would someone establish a connection to the box?
 3. I have not done this -- so no laughing or worse :-) ) but the box was (for a very very short period of time - minutes) plugged into the Ethernet. Apparently the network device that was used does not do NAT. I looked at the IP address and it started with 64 or someothing in that range. Everytime I have seen a number like that it was from an ISP. I don't consider this safe on principal but I don't understand why if all ports are turned off. What am I missing? Feel free to say several college courses in Network security. :-)
 4. I do have a router that does DHCP and NAT and given that it does NAT I would expect that having this would help. The question that I have is that is this a total block for IP based attacks. Can someone get around the NAT router? The device by the way is a Linksys Etherfast Cable/DSL Router with 4 Port Switch. 
5. I am not against spending some money for a hardware firewall and given this is for a setup for non-technical person I would be more than willing. The question is: Given the Linksys and the default settings for UBUNTU am I in good enough shape to use the box to surf, email and IM. What risk am I taking with this configuration.

Thanks So much,

Paddy
Paddy

---

### Post by dacorr on 2009-03-30
1. Many people have stated that the default setup of UBUNTU is locked down. I take this to mean that all ports but 80 have been turned off. I am using 8.10 but I am not using SElinux. Is this a correct interpretation?

*I believe that common ports are not restricted, you can use a GUI such as Guarddog to edit the IPtables configuration (linux firewall built into kernal) bearing in mind you have incomming and outgoing port 80, outgoing is used when you access the internet.*

2. There is one user on this box and the password is moderately cryptic (numbers, letters and special characters). If the only port open is 80 (per Q1) then how would someone establish a connection to the box?

*you can establish connections on open ports however your incomming port 80 is not used (typically a webserver) so there is no service to compramise.*

3. I have not done this -- so no laughing or worse  ) but the box was (for a very very short period of time - minutes) plugged into the Ethernet. Apparently the network device that was used does not do NAT. I looked at the IP address and it started with 64 or someothing in that range. Everytime I have seen a number like that it was from an ISP. I don't consider this safe on principal but I don't understand why if all ports are turned off. What am I missing? Feel free to say several college courses in Network security. 
4. I do have a router that does DHCP and NAT and given that it does NAT I would expect that having this would help. The question that I have is that is this a total block for IP based attacks. Can someone get around the NAT router? The device by the way is a Linksys Etherfast Cable/DSL Router with 4 Port Switch.

* the IP will change so there is not much point worring about it, when a connection is made it will be made to the router not the ubuntu machine, if the router has not been advised on what to do with incoming connections on any port such as 80 it will generally drop the connection. Only concern are services running on the router such as SSH or web interface.*

as you are not running a service there is little to worry about, i have a similar setup however i do have a webserver, i configured the IPtables (GuardDog) and run SNORT (Intrusion Detection System) most unwanted connections are blocked.

It would be difficult to gain access to the machine using your circumstances.

Other than configuring the IPtables to block all incoming ports but the ones you use will be your best option.

My level of paranoia would involve placing a small machine connected to the router as an additional firewall and filter, more like an advanced router running IDS but still may be overkill for you

Dac

---

