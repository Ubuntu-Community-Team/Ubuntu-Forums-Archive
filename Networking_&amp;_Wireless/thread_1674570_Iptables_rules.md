---
title: "Iptables rules"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by Zubairinfo on 2011-01-24
Hello Experts,

I have ubuntu box configured with Gateway, DHCP, Local DNS and proxy (squid),
server IP 192.168.0.1 with 2 network cards, eth0 connected with internet, eth1 internet shared from eth0 configured with DHCP 192.168.0.0/24, configured with a transparent proxy through squid.

Now i wanted to add the third network interface eth2 and configure DHCP to listen to this interface also with a new  ip pool 192.168.1.0/24, where in i dont want any machine able to access any machine from 192.168.0.0/24 to 192.168.1.0/24 and vice versa.
except both ip pools accessible from the gateway (192.168.0.1)

can any body help me giving some iptable rules  for this solution...

Thanks in Advance.

---

### Post by SeijiSensei on 2011-01-24
You have a couple of options:

Block by interface
```
iptables -A FORWARD -i eth0 -o eth2 -j REJECT
iptables -A FORWARD -i eth2 -o eth0 -j REJECT
```

or block by subnet
```
iptables -A FORWARD -s 192.168.0.0/24 -d 192.168.1.0/24 -j REJECT
iptables -A FORWARD -s 192.168.1.0/24 -d 192.168.1.0/24 -j REJECT
```

Make sure these come before any NAT rules.

You'll need two instances of dhcpd as well, each bound to a separate interface.

---

### Post by theDaveTheRave on 2011-01-24
is it not possible / more sensible to perform such a task through the use of users and groups via some form of active directory (LDAP) ? I say possible as I'm not that experienced in subnetting with LDAP, but it would seem like a more flexible solution - especially as I guess you are using something like LDAP already for sign on credentials.

I only ask as I guess that the server / proxy / gateway is headless and you'll have users who need to access it from both sides of the divide (even if it is just you who may be logged on from either subnet).

David

---

### Post by SeijiSensei on 2011-01-24
> **theDaveTheRave said:**
> is it not possible / more sensible to perform such a task through the use of users and groups via some form of active directory (LDAP) ? 

That's sounds like a lot more hassle than simply blocking connectivity between subnets with iptables.  I'm not even sure how you'd implement a solution like that with LDAP, since the restrictions are applied to the subnets, not to users.

---

### Post by theDaveTheRave on 2011-01-25
I would have thought creating 2 groups (one for each subnet) with users being in either 1 group of the other would have done the trick, and users being able to access computers from ether being in a third.

If users can move around between the subnets then surely restricting access to one subnet from the other will become a moot point, the 'clever' user will simply move to another pc - I know that is what I used to do so as to get 'overiding' access to a printer when I was at uni, certain pc's had access to different printers, but all used a roaming sign on.

Although I appreciate that 'blocking' out certain access from physical locations can help to 'restrict' access (especially when combined with physical access restrictions).

David

---

### Post by Zubairinfo on 2011-02-09
> **theDaveTheRave said:**
> I would have thought creating 2 groups (one for each subnet) with users being in either 1 group of the other would have done the trick, and users being able to access computers from ether being in a third.

If users can move around between the subnets then surely restricting access to one subnet from the other will become a moot point, the 'clever' user will simply move to another pc - I know that is what I used to do so as to get 'overiding' access to a printer when I was at uni, certain pc's had access to different printers, but all used a roaming sign on.

Although I appreciate that 'blocking' out certain access from physical locations can help to 'restrict' access (especially when combined with physical access restrictions).

David


Hello Guys,

I have configured a proxy on my ubuntu server 10.10 with tinyproxy which is transparent proxy with iptales rule "sudo iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 8080"

Now i wanted to exclude to local IPs (192.168.1.5, 192.168.1.10) which should not have any url block. by default all the client machines are blocked.
kindly suggest me a solution.

Thanks in advance.

---

### Post by theDaveTheRave on 2011-02-15
Zubairinfo,

have you figured out a solution yet??

I have just had a read of the [LDAP 'introduction' page]("http://www.openldap.org/doc/admin24/intro.html") and it suggests being able to perform directory access via domain name, and I assume therefore also by 'ip address' (if you give each IP a separate name that is - for which you will need to have a look at DNS servers etc). Have a read of section 1.9 for some ideas...



> **SeijiSensei said:**
> That's sounds like a lot more hassle than simply blocking connectivity between subnets with iptables.  I'm not even sure how you'd implement a solution like that with LDAP, since the restrictions are applied to the subnets, not to users.

Actually I would have though not?

You would have each user being a member of certain groups.

So in a sort of 'xml' scheme...

```

[Group]Admins
[user] Zubairinfo
      [member]Subnet1[/member]
      [member]subnet2[/member]
[/user]
[/group]

[group]subnet1
[user]David
#this user can access shared drives on both locations, but can 'write' #to the drives on subnet 1 only
      [member]Subnet1[/member]
      [member]Subnet2[/member]
[/user]
[user]SeijiSensei
#this user can only access the drives that are shared within subnet 2
#he also therefore has write permisions.
#if he moves to a location on 'subnet2' he still will only have access #to the subnet1 shared drives - lets hope he doesn't have joint #projects in this location! 
      [member]Subnet1[/member]
[/user]
[/group]

```

I'm not exactly sure how you would then control the access to shared drives etc, but I'm sure it would be easier as any new 'subnet areas' that you create would then just require a user being included in that group. You could probably include info regarding read write access etc in each users profile on the server also.

Seems more flexible, although you would probably still want to create subnets for the physical locations, you would now be able to 'bypass' that problem. Anyway it would seem like eventually your system may get more 'sub-subnets' and this would be able to adjust to these needs...

However, I would suggest that the OP hops over to the LDAP forums for a better more expert suggestions for a solution using LDAP - or otherwise...

David

---

