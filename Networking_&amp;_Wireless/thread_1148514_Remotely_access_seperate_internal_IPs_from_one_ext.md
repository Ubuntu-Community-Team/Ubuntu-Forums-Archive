---
title: "Remotely access seperate internal IPs from one external with Subdomains"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by Jloser on 2009-05-04
Currently I have 2 computers, both running ubuntu, inside of a network.  One of these computers runs a public website ([www.example.com](www.example.com)).  I can ssh to example.com and connect to my main server.  I am interested in connecting directly to my other box.  As of now I have it setup to SSH to a different port that is forwarded in my router config.  Is it possible to direct traffic to the second box by creating a subdomain?

I would like to be able to directly access on box at example.com and the second at number2.example.com.  I only have one IP address...

Is this possible?

---

### Post by dawonn on 2009-05-04
WOW! I'm in search of EXACTLY what you write here... PLEASE post if you find a solution~

~Dereck
:popcorn:

---

### Post by dawonn on 2009-05-05
[https://www.linuxquestions.org/questions/linux-networking-3/subdomains-behind-single-ip-723725/](https://www.linuxquestions.org/questions/linux-networking-3/subdomains-behind-single-ip-723725/)
[INDENT]
You need a router that can do NAT. All subdomains will have the same external IP.

[http://en.wikipedia.org/wiki/Network...ss_translation](http://en.wikipedia.org/wiki/Network...ss_translation)[/INDENT]

There's a start...

---

### Post by Jloser on 2009-05-05
I am not very sure that this is possible. The way I understand it this is typically done with different IP addresses and then the traffic is routed properly based on the IP address given by the DNS server.  

Both example.com and number2.example.com would have the same external IP address, so any communication would be forwarded to to apache on my main server.  So I guess this isn't really an ubuntu or networking question, but more of an apache question.  Is it possible to setup some sort of virtual host to redirect all communication to a separate computer?

From my research and limited knowledge, I don't think this is possible.  Can anyone else provide some information?

---

### Post by dawonn on 2009-05-05
You are correct as far as I can tell unfortunately... TCP/IP packets carry no domain name information.

---

### Post by Jloser on 2009-05-05
Would someone who knows how to do this legitimately let us know the proper way this should be done and verify that it is in fact not possible?

---

