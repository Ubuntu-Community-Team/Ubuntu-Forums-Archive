---
title: "Firestarter will not play nice with OpenVPN"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by gossrock on 2009-05-06
I'm having some trouble with firestarter and OpenVPN on 9.04.  When both are running everything is blocked.

I found several guides on line that say I should edit /ect/firestarter/user-pre to include these lines:

```

$IPT -A INPUT -i tun+ -j ACCEPT
$IPT -A OUTPUT -o tun+ -j ACCEPT

```

and then restart firestarter.

No change for me.

Is this the right file on Ubuntu or is there something else that I'm missing?

---

### Post by gossrock on 2009-05-08
okay I am starting to understand this a bit now.  What I have found out is that firestarter wants to protect eth0 (for example) and that the above lines are to punch a hole in that protection for the VPN.

What I would like to do is protect both.  Lets take the unsecured wifi coffee shop example.  You are on a strange network you don't trust.  You want to use a VPN tunnle out to the internet to protect yourself from the unknown people on that network, but you also want to make sure that nothing can get in though the internet either.  So we want to protect both.

What I am finding is that I can wall off eth0 almost completely except for vpn access by adding those 2 lines and then setting both incoming and outgoing to "restrictive" and allowing the OpenVPN port 1194.  I can't do anything untill I start the VPN and then I can browse to my hearts content.  It's like I'm sitting naked on the internet.  I have blocked the unknowns in the coffee shop but the unknows on the internet can just come on in.  

Can I change the 2 line so that I can atleast block the incoming requests.  And possibly explisitly allow outgoing?

---

### Post by kevdog on 2009-05-08
First -- stop using Firestarter and either configure iptables manually or use ufw/gufw.  

Next - are you running any services?  A firewall is for fine tunning incoming access to your machine (you can also fine tune outgoing packets and forward packets, however lets table this discussion).  If you aren't running any open ports or open services, then a firewall is pretty much meaningless.

---

### Post by gossrock on 2009-05-08
hmm, this link looks interesting:

[http://www.antionline.com/showthread.php?t=231458](http://www.antionline.com/showthread.php?t=231458)

though my head can't take much more tonight.  I'll look at it later.

---

### Post by gossrock on 2009-05-08
kevdog,

I'm don't want to be running any open ports. But I have already noticed by going to shields up ([https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)) that I have already installed something that has opened up port 22 and I'm not sure what it is.  If I have done that I would like to be sure that nothing will be alowed to be opened without me realizing that it has been opened.  I'm thinking your right I'm thinking that I may have to learn iptables but I was trying to take the easy way out.  That seams to be failing.

---

### Post by gossrock on 2009-05-08
ah, gufw looks good. I will have to try it out.

---

### Post by gossrock on 2009-05-09
Problem(s) solved.  Here is my documentation of what I did. (Including stupid mistakes)

First the open port 22.  It wasn't mine that was open. It was the vpn service provider who had an open port 22.  I finally had the briliant Idea of ataching to the internet without the router in between and port scan myself that way.  And low and behold it was not open.  

But because of my stupidity in not doing that earlier I ended up learning iptables because firestarter, gufw and ufw where not working as expected.  Of course they are not designed to configure a computer that they are not running on and so iptables also was not working as expected.  But this was because I didn't have a full grasp of the problem. 

In resurching iptables I found a very helpful posting with a firewall script ([http://rhau.se/2009/02/10/simple-iptables-firewall-script-with-nat-and-sfq-sceduling/](http://rhau.se/2009/02/10/simple-iptables-firewall-script-with-nat-and-sfq-sceduling/)) Now this script was way more than I needed but It helped out in searching through the man page and figureing out how things worked.

So heres what I ended up with as a setup.  I chose to have as a policy to be restrictive on both inbound and outbound trafic and to only open the ports that I wanted open outbound leaving everything closed inbound.   I'm sure I don't really need that level of restriction I think it's cool that I can do it so I will :)

Heres my script for when I'm running the vpn:
```

#! /bin/bash

# set inteface strings 
# eth+ matches both eth0 (my wired) and eth1 (my wireless)
ETHERNET="eth+"
TUNNEL="tun0"


#clear current rules
iptables -F

#set default to drop (probobly redundent with final explicit section)
iptables -P FORWARD DROP
iptables -P INPUT DROP
iptables -P OUTPUT DROP

#accept anything that I already have an established connection with
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

#open port 1194 on ETHERNET for TUNNLE to connect through.
iptables -A OUTPUT -o $ETHERNET -p udp --dport 53 -j ACCEPT #DNS
iptables -A OUTPUT -o $ETHERNET -p udp --dport 67:68 -j ACCEPT #DHCP
iptables -A OUTPUT -o $ETHERNET -p udp --dport 1194 -j ACCEPT #openvpn



#open ports on TUNNEL that you want to use.
iptables -A OUTPUT -o $TUNNEL -p udp --dport 67:68 -j ACCEPT #DHCP
iptables -A OUTPUT -o $TUNNEL -p udp --dport 53 -j ACCEPT #DNS
iptables -A OUTPUT -o $TUNNEL -p tcp --dport 80 -j ACCEPT #http
iptables -A OUTPUT -o $TUNNEL -p tcp --dport 443 -j ACCEPT #https
iptables -A OUTPUT -o $TUNNEL -p tcp --dport 110 -j ACCEPT #pop3
#iptables -A OUTPUT -o $TUNNEL -p tcp --dport 22 -j ACCEPT #ssh"
#iptables -A OUTPUT -o $TUNNEL -p tcp --dport 20:21 -j ACCEPT #ftp
#iptables -A OUTPUT -o $TUNNEL -p tcp --dport 6881:6889 -j ACCEPT #bit torrent


# explicitly drop everything that has not been previously allowed
iptables -A FORWARD -j DROP
iptables -A INPUT -j DROP
iptables -A OUTPUT -j DROP

```


here is the script I can run while at home on my trusted network:
```

#! /bin/bash

#clear current rules
iptables -F

#set default to drop (probobly redundent with final explicit section)
iptables -P FORWARD DROP
iptables -P INPUT DROP
iptables -P OUTPUT DROP

#accept anything that I already have an established connection with
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

#open ports on TUNNEL that you want to use.
iptables -A OUTPUT -p udp --dport 67:68 -j ACCEPT #DHCP
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT #DNS
iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT #http
iptables -A OUTPUT -p tcp --dport 443 -j ACCEPT #https
iptables -A OUTPUT -p tcp --dport 110 -j ACCEPT #pop3
iptables -A OUTPUT -p tcp --dport 22 -j ACCEPT #ssh"
#iptables -A OUTPUT -p tcp --dport 20:21 -j ACCEPT #ftp
#iptables -A OUTPUT -p tcp --dport 6881:6889 -j ACCEPT #bit torrent


# explicitly drop everything that has not been previously allowed
iptables -A FORWARD -j DROP
iptables -A INPUT -j DROP
iptables -A OUTPUT -j DROP

```


Comments are defiantly welcome.  This being my first endeavor at iptables I would love to have constructive criticism.

---

### Post by gossrock on 2009-05-09
Now the next part of the project is to make a script run when I start up.  I have found that the original settings show up when I restart.

---

### Post by gossrock on 2009-05-09
addidional port information:
[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)


and in the "how did I not find this before" and "I really wish I saw this earlier" catagories:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by mdacova on 2010-05-12
> **gossrock said:**
> I'm having some trouble with firestarter and OpenVPN on 9.04.  When both are running everything is blocked.

I found several guides on line that say I should edit /ect/firestarter/user-pre to include these lines:

```

$IPT -A INPUT -i tun+ -j ACCEPT
$IPT -A OUTPUT -o tun+ -j ACCEPT

```

and then restart firestarter.

No change for me.

Is this the right file on Ubuntu or is there something else that I'm missing?


Worked for me I have a 10.4 ubuntu with the same issue  user-pre with the above rules fixed the issue

---

### Post by Karl_L on 2012-08-08
I posted this somewhere the other day but I'll repeat it here and then ask my own question:

Go to /etc/firestarter and sudo gedit user-pre to add:
   
$IPT   -A   INPUT   -i   tun0+   -j   ACCEPT
$IPT   -A   OUTPUT   -o   tun0+   -j   ACCEPT

or, tun1+, depending on which label your hma-start labels the tunneling device.

That takes care of the problem some have had of running Firestarter and an hma proxy at the same time on Linux. 

 OK, now I'm trying to get Firestarter to let my printer operate.  I've added every port that Firestarter blocks when I try to print a test page but no joy.  Now I'm wondering if I should be thinking about editing user-pre to allow Firestarter to accept input and output from the printer "device" . Is there a doc on this I should be checking?

---

### Post by wildmanne39 on 2012-08-08
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

