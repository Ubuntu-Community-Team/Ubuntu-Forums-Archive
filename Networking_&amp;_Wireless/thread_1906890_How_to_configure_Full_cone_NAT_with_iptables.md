---
title: "How to configure Full cone NAT with iptables ?"
date: 2012-01-10
forum: Networking &amp; Wireless
---

### Post by lvl1s7a on 2012-01-10
[FONT=Courier New]Hi Experts;[/FONT]

[FONT=Courier New]I want to find the right iptables commands combination to address the following need:[/FONT]

[FONT=Courier New]- NEs are NATed thru the linux box (using iptables) towards the WAN cloud, where the NTP servers are situated.[/FONT]
[FONT=Courier New]- In order to achieve redundancy, the NTP Servers are in a load balancing cluster with one virtual IP address (172.30.4.245) [/FONT]
[FONT=Courier New]- The problem is that when the NEs request for NTP updates using the 172.30.4.245, the NTP response is received from one of the actual IP addresses (.200, .230 .240).[/FONT]

[FONT=Courier New]Example:[/FONT]
[FONT=Courier New]The iptables is not allowing this flow, which is a normal behaviour since the requested vs responding address are not the same (172.30.4.245 vs 172.30.4.230) :[/FONT]

[FONT=Courier New]Request : UDP 10.68.2.11:23445 ---> 172.30.4.245:123 (this is Before NAT, of course after NAT the source is 10.23.14.72)[/FONT]
[FONT=Courier New]Response: UDP 172.30.4.230:123 ---> 10.23.14.72:23445 (Response to the WAN address)[/FONT]

[FONT=Courier New]I'm wondering if there is any way to let iptables establish the UDP flow only based on the (s-port/d-port) regardless of the IP addresses, and execute the NAT back to [/FONT][FONT=Courier New]the LAN based on that.[/FONT]

[FONT=Courier New]UDP/NTP is just an example, almost all the needed services are setup in the same way (load balancing in Cluster).[/FONT]
 
[FONT=Courier New][IMG]http://i42.tinypic.com/35b7bsg.jpg[/IMG][/FONT]
 
 
[FONT=Courier New]Appreciate your help ![/FONT]

[FONT=Courier New]Thanks & Regards[/FONT]
[FONT=Courier New]lvl1s7a[/FONT]

---

### Post by Doug S on 2012-01-10
Hi lvl1s7a, and welcome to ubuntu forums.
 
I guess I have a question: Rather than try to program around the problem at the NTP end, why not fix that end? I would suggest to put the servers on a LAN behind the 172.30.4.245 box. If that is not possible then you should be able to have the packets return via the 172.30.4.245 box, getting re-mapped to that IP address.
 
By the way, I have been trying to figure a way to do what you actually asked, but haven't figured it out.
 
Is what you called a "WAN cloud" really a WAN cloud? All of the IP addresses you listed are reserved for LAN's and not routable on internet.

---

### Post by lvl1s7a on 2012-01-11
Thanks a lot Doug for the reply;
 
Please find my comments below
 
> **Doug S said:**
> 
 
I guess I have a question: Rather than try to program around the problem at the NTP end, why not fix that end? I would suggest to put the servers on a LAN behind the 172.30.4.245 box. 
 
If that is not possible then you should be able to have the packets return via the 172.30.4.245 box, getting re-mapped to that IP address.
 

 
Those servers don't belong to my responsibility scope :), All the services are setup in this way (not only NTP), I'm only responsible for the left part of the network.
 
And there is no .245 box, it's a virtual IP address shared by all the servers, in a weighted round robin manner (the weight is the load).
 
 
 
> **Doug S said:**
> 
By the way, I have been trying to figure a way to do what you actually asked, but haven't figured it out. 
 
What I'm looking for is something that tells iptables to track the outgoing packet, memorise the LAN IP address and bind it with the source port before the NAT happens towards the outside, 
 
And when the respose arrives, iptables checks only the destination port (vs the previously memorised source port) and NAT back the packet towards the memorised LAN IP.
 
I'm not sure if this can be implemented with iptables, but it does exist with other vendors 
 
You can check this document about full-cone NAT for your reference:
 
[http://www.cisco.com/web/about/ac123/ac147/archived_issues/ipj_7-3/ipj_7-3.pdf](http://www.cisco.com/web/about/ac123/ac147/archived_issues/ipj_7-3/ipj_7-3.pdf)
 
It's also in RFC 3489 check: [http://tools.ietf.org/html/rfc3489#page-5](http://tools.ietf.org/html/rfc3489#page-5)
 
> **Doug S said:**
> 
Is what you called a "WAN cloud" really a WAN cloud? All of the IP addresses you listed are reserved for LAN's and not routable on internet.
 
Yes it's really a WAN cloud, WAN never meant public addressing or Internet :);) it's just a Wide Area Network, instead of a local one.
 
Thanks again & Regards
lvl1s7a

---

### Post by Doug S on 2012-01-11
Hi lvl1s7a,
 
Thanks for the references. I also see, from searching around, that you posted this same question on a few other forums. It is clear to me that I should have done more homework before replying yesterday, sorry. I do not know of an iptables solution for your multiple NEs on your LAN side problem. If you find a solution elsewhere, please post back here.
 
Edit (hours later): I thought of solution that might work (my experience with virtual computers is quite limited, so I am not sure):
 
Install a virtual computer on your linux box and always do your full cone thing back to that computer. From what I have been reading, a single client is quite doable for the cone thing. Now in turn, that virtual computer does what is now a normal NAT back to the NE set of computers.

---

### Post by lvl1s7a on 2012-01-12
> **Doug S said:**
>  
Thanks for the references. I also see, from searching around, that you posted this same question on a few other forums. It is clear to me that I should have done more homework before replying yesterday, sorry. I do not know of an iptables solution for your multiple NEs on your LAN side problem. If you find a solution elsewhere, please post back here. 
 
Hi Doug;
Please don't be sorry ! I'm more than glad that we had this brain storming together. sure I'll post back here as soon as I find a solution. 
 
> **Doug S said:**
> 
Edit (hours later): I thought of solution that might work (my experience with virtual computers is quite limited, so I am not sure):
 
Install a virtual computer on your linux box and always do your full cone thing back to that computer. From what I have been reading, a single client is quite doable for the cone thing. Now in turn, that virtual computer does what is now a normal NAT back to the NE set of computers.
 
Very good idea, so this virtual box will handle every service I have (not only NTP).
I'll try to go in this direction meanwhile, thank you very much indeed.
 
 
Thanks again Doug & Best Regards.
lvl1s7a

---

