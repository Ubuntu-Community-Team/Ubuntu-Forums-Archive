---
title: "statilc ip address confusion"
date: 2013-01-01
forum: Networking &amp; Wireless
---

### Post by jmsgz on 2013-01-01
Hi folks
   my co leased a public/static ip address from my ip provider.
   so that we can in house host our own www server.

   it is 
   
   192.168.0.217
  
   netmask

   255.255.255.0

   can "this" address be sub-netted so that i have more publically
   visible ip address ? or is this simply a one (1) ip address.?

   if so 

   do i have to simply use it as our co's publically viewed ip address
   and NAT/re-direct to internal private ip address's at the firewall?
   the firewall is an OpenBSD machine using pf. I simply am having
   a brain fart in getting my head around this address.

   i guess if they provided me with an address of
   192.168.0.0/28 i could subnet since it would have been a block
   of 16 with a usable of 14 addresses.

   but with a 217 in the last octet i am slightly confused.

   thanks 
   in advance.

**EDIT: Note - the ip addresses above (are) public, I have just replaced them with a private subnet version -sandyd**

---

### Post by redmk2 on 2013-01-01
> **jmsgz said:**
> Hi folks
   my co leased a public/static ip address from my ip provider.
   so that we can in house host our own www server.

   it is 
   
   n.n.n.217  [COLOR="Red"]**<-- public IP address in the original question**[/COLOR]
  
   netmask

   255.255.255.0

   can "this" address be sub-netted so that i have more publically
   visible ip address ? or is this simply a one (1) ip address.?

   if so 

   do i have to simply use it as our co's publically viewed ip address
   and NAT/re-direct to internal private ip address's at the firewall?
   the firewall is an OpenBSD machine using pf. I simply am having
   a brain fart in getting my head around this address.

   i guess if they provided me with an address of
   **[COLOR="Red"]n.n.n.0/28[/COLOR]** i could subnet since it would have been a block
   of 16 with a usable of 14 addresses.

   but with a 217 in the last octet i am slightly confused.

   thanks 
   in advance.

You can't *subnet* an address.  You *subnet *networks.  Did you lease an IP address or a block of IP addresses (e.g. a subnet)?

---

### Post by sandyd on 2013-01-01
**Removed IP Address - please do not post them on public forums**

Thanks!

---

### Post by jmsgz on 2013-01-01
we requested a public/static ip address.
we were not issued one with a /XX extension.
we were given a XXX.XXX.XXX.XXX of which the last
octet did not contain a 000 or /XX

however the netmask is 255.255.255.0 which is 
creating confusion in "my mind!!!"

i thought a netmask of the a above meant that
the last octet yields 8 bits or 256 more 
available address's ?

what am i missing?

---

### Post by redmk2 on 2013-01-01
> **jmsgz said:**
> we requested a public/static ip address.
we were not issued one with a /XX extension.
we were given a XXX.XXX.XXX.XXX of which the last
octet did not contain a 000 or /XX

however the netmask is 255.255.255.0 which is 
creating confusion in "my mind!!!"

i thought a netmask of the a above meant that
the last octet yields 8 bits or 256 more 
available address's ?

what am i missing?

If you are assigned an ***IP address*** Then that's what you get.  The subnet mask defines the network you are in **and the IP address space** 

If you provision a block of IP addresses (a subnet) then the [COLOR="Red"]**/number**[/COLOR] would provide you with the address space starting with the network number.  Like this```
192.168.0.0 /24  (255.255.255.0)
  network = 192.168.0.0 
  Start IP 192.168.0.0
  End IP 192.168.0.255

192.168.0.0 /**[COLOR="Red"]25[/COLOR]**
network = 192.168.0.0
start 192.168.0.0
end 192.168.0.127

or 
192.168.0.127 /**[COLOR="Red"]25[/COLOR]**
start 192.168.0.128
end 192.168.0.255
```

An address in any subnet would use an address ***in the network defined by the network number and its subnet mask***.

**[COLOR="Blue"]Edit:  For example the IP address 192.168.0.100 is in the first and second networks I defined, but NOT in the 3rd network.[/COLOR]**

---

### Post by jmsgz on 2013-01-01
ok, since there was no /XX provided and since i did not request a block, 
and since i only "need" one address at this point
 
summarizing

i can then NAT/redirect- at the firewall to a lan and a dmz utilizing
two nics using private address's



such as 
                        |                 | int_if---> internal lan/pc's 
    internet --ext_if-->|openbsd firewall | dmz_if----> dmz www server
                        |                 |

---

### Post by jmsgz on 2013-01-01
diagram in last reply did not show correctly


so the intent
is simply to redirect at the firewall from the 
internet via an openbsd pc
to 2 internal networks
1 a local lan_if:network
and a dmz to a publically visible webserver
listening on port 80 and NAT'd at the firewall

requiring 3 nics and a small pc running pf
on openbsd?

am i thinking correctly?

---

### Post by chadk5utc on 2013-01-01
you could use an online subnet calculator to give you a better understanding of what the others are explaining
[http://www.subnet-calculator.com/](http://www.subnet-calculator.com/)

---

### Post by ahallubuntu on 2013-01-01
The static IP should be set in your modem.  Just enter the IP, gateway, and netmask they have provided you there.  Don't overthink this.  Leave the LAN setup the way it probably was before.

If you want to run a web server and the local IP of the web server is, say, 192.168.0.101, just forward ports 80 and 443 through the NAT firewall in your router (perhaps the router is part of your modem) to that IP and you're done.

---

### Post by jmsgz on 2013-01-01
we are using sipcalc  and hexcalc
to expand our understanding, ,,,,,thanks for the suggestion

there will be "no" commercial modem/router/firewall

we are "creating" the router/firewall using an openbsd box
utilizing openbsd packet filtering............


we  plan on using three nics for this 
one facing internet 
one facing private internal lan
one facing public www webserver

NAT and redirection to be performed at the openbsd firewall.

we were confused with what was supplied to us....
and that was the source of the posting.
we were unable to talk to ip provider yet
so we were wondering about subnetting and
netmasks etc. We realize now that we have
one (1) public static address and will
be doing the following

we are using openbsd firewall packet filtering because of its
capability and user ability to understand what is happening
and what is happening to traffic. It allow the administrator
to alter rules, ques's, load balalancing, redirection, etc
by internal pf.conf configuration.
Openbsd has a uniques reputation for security,,,,,
we prefer to stay away from over the counter firewall/routers.
that's the reason for the 3 nic card requirement.
it could be accomplished with two but we like the idea
of a dmz containing the www server.

---

### Post by redmk2 on 2013-01-01
> **jmsgz said:**
> diagram in last reply did not show correctly


so the intent
is simply to redirect at the firewall from the 
internet via an openbsd pc
to 2 internal networks
1 a local lan_if:network
and a dmz to a publically visible webserver
listening on port 80 and NAT'd at the firewall
It won't be publicly visible unless you port forward.  The IP address that is public will be on the WAN side and the private IP addressed LAN will be on the other side.> 

requiring 3 nics and a small pc running pf
on openbsd?

am i thinking correctly?

I believe you understand now.  If you want to use a PC running OpenBSD and PF you can.  You idea is fine (see my one note above).   You can simplify this with 2 nic's and a single LAN.  Your need for a DMZ is really not needed when you use private IP addressing.  You will always be port forwarding from the public IP address to a specific private IP address anyway.   As others have said you could even configure an off the shelf soho router if you wanted.

---

### Post by redmk2 on 2013-01-01
> **jmsgz said:**
> we are using sipcalc  and hexcalc
to expand our understanding, ,,,,,thanks for the suggestion

there will be "no" commercial modem/router/firewall

we are "creating" the router/firewall using an openbsd box
utilizing openbsd packet filtering............


we  plan on using three nics for this 
one facing internet 
one facing private internal lan
one facing public www webserver

NAT and redirection to be performed at the openbsd firewall.

we were confused with what was supplied to us....
and that was the source of the posting.
we were unable to talk to ip provider yet
so we were wondering about subnetting and
netmasks etc. We realize now that we have
one (1) public static address and will
be doing the following

we are using openbsd firewall packet filtering because of its
capability and user ability to understand what is happening
and what is happening to traffic. It allow the administrator
to alter rules, ques's, load balalancing, redirection, etc
by internal pf.conf configuration.
Openbsd has a uniques reputation for security,,,,,
we prefer to stay away from over the counter firewall/routers.
that's the reason for the 3 nic card requirement.
it could be accomplished with two but we like the idea
of a dmz containing the www server.

There is no need for a 3rd NIC as the IP address of the web server will not be a public one.  You will need NAT to use a private address for all hosts in the LAN network.

Think of it like this```

Public IP -->|router|<--NAT to Private IP's on LAN 

```

If you were to add a 3rd NIC it would look like this```

Public IP --->|router|<--NAT to Private IP's on LAN
                     |<--NAT to Private IP for DMZ and webserver on 2nd LAN

```
PF is capable of handling 3 NIC's and you certainly can do this, but in practice it has limited advantages.  If you are going to be compromised most likely it will be the webserver itself no the entire LAN.

---

### Post by jmsgz on 2013-01-01
> **ahallubuntu said:**
> The static IP should be set in your modem.  Just enter the IP, gateway, and netmask they have provided you there.  Don't overthink this.  Leave the LAN setup the way it probably was before.

If you want to run a web server and the local IP of the web server is, say, 192.168.0.101, just forward ports 80 and 443 through the NAT firewall in your router (perhaps the router is part of your modem) to that IP and you're done.


thanks there "is" something to say about simplicity!!!!!!
jmsgz

---

### Post by jmsgz on 2013-01-01
> **redmk2 said:**
> There is no need for a 3rd NIC as the IP address of the web server will not be a public one.  You will need NAT to use a private address for all hosts in the LAN network.

Think of it like this```

Public IP -->|router|<--NAT to Private IP's on LAN 

```

If you were to add a 3rd NIC it would look like this```

Public IP --->|router|<--NAT to Private IP's on LAN
                     |<--NAT to Private IP for DMZ and webserver on 2nd LAN

```
PF is capable of handling 3 NIC's and you certainly can do this, but in practice it has limited advantages.  If you are going to be compromised most likely it will be the webserver itself no the entire LAN.

physically and technically u r correct there is no need for a third
nic.,,,,,,,,,,,,,,,,,
how-some-ever, security according to those who profess to know (me excluded)recommend a seperate nic for dmz

---

### Post by circa on 2013-01-01
> **sandyd said:**
> **Removed IP Address - please do not post them on public forums**

Thanks!
I think you might have missed it, but the IP address is still showing in the first message.

---

### Post by chadk5utc on 2013-01-01
all thats posted on the first post in a common class C private address

---

### Post by jmsgz on 2013-01-01
thanks for all of the posts folks

we "think" we got it figured out with your help.....

next problems will probably be pf.conf related and i  will
have to expose my ignorance to the people at openbsd
forums....


jmsgz

---

