---
title: "DHCP client does not seem to register hostname in DNS"
date: 2006-01-26
forum: Networking &amp; Wireless
---

### Post by dilyard on 2006-01-26
I've been running SuSE for the past 4-5 years and just recently migrated my work desktop to Breezy Badger a week ago.  I've configured the workstation to use DHCP and kept the old hostname (galaga) from the SuSE install.  Everything has worked great until today when apparently I was forced to re-lease my IP.

Everything is still working fine on the workstation, however, now galaga cannot be seen on the network.  This presents a problem since all the cubes around me use galaga as a print server in Solaris, Linux and Windows.

We can access it through the IP address, but not the hostname.

Any ideas?  Thanks

---

### Post by localzuk on 2006-01-26
How was the name registered? Via hosts files? DNS server? Multicast?

Are you using the same network card on the machine? As a static lease from a dhcp server would work off the MAC address of the card and then a dns server would link to the ip address that was assigned.

---

### Post by dilyard on 2006-01-26
I believe its passed from the hosts file.  The workstation seems to know who it is, but the rest of the world does not.

---

### Post by localzuk on 2006-01-26
It isn't passed from a hosts file - as this is just a local IP -> Domain Name mapping system.

This would mean that every machine that needs to know the name must be told the ip -> domain name mapping.

---

### Post by dilyard on 2006-01-26
Sorry, I think I answered the question without actually thinking about it.  Its should be registered in DNS, but its not.  I cannot figure out how to get DNS to update.

I can ping the IP address of my workstation from anywhere, but I cannot get a reverse lookup of the IP.  I've been trying to figure out how this dhclient3 is configured, but I'm not a "network guy" so its a lot of trial and error.

Thanks

---

### Post by localzuk on 2006-01-26
Has the server got records set up for linking the IP to the hostname?

---

### Post by dilyard on 2006-01-26
If you mean the DNS server, I have no idea as I have no access to it.  I've not had this issue with SuSE or Redhat, but I never really had to configure DHCP on them.  I tried to compare the configurations with some of our SuSE systems in the area, but the DHCP client is completely different.

---

### Post by localzuk on 2006-01-26
The problem is that the name is not defined by the client but by the server. Unless the IP address that is being assigned to the machine matches the one in the DNS server you will have no luck. I think looking at the client is a dead end and it needs to be addressed by whoever runs the DNS server.

---

### Post by dilyard on 2006-01-26
Shouldn't the client be able to tell the server what its name should be?  Thats what I've done in the past.  Maybe I should uninstall the dhclient3 and install a DHCP client I know how to configure.

For instance, in my dhcp config file on my other systems, I have:
DHCLIENT_SET_HOSTNAME="yes"

I've found what appear to be similar parameters for the /etc/dhcp3/dhclient.conf file, but none of my "experiments" have worked.

Thanks for your help!

---

### Post by localzuk on 2006-01-26
All the client can state is what its local name is. The DNS server is the definitive place which defines the name of the machine. There is no-where in the dhcp/dns systems to allow for the client to tell the dns server what its name is.

The way the system works is:

Client asks for IP from dhcp server - presenting a hardware address (MAC address of network card).
The dhcp server hands out an IP based on its rules, this may include a name for the computer (a replacement local name for use whilst that ip is in effect).
The DNS server must be set up with a domain name + ip pair handling what that machine is called and informing any client that requests the name of the true identity of the machine.
When a client asks for 'machinename' it sends the request to the dns servers which reply with the ip addres sof the machine in question which the client then communicates with.

There isn't anywhere for the original machine to tell the server its name.

Oh and the param you mention in the above is to allow the dhcp server to rename the machine if it requests it for the life of the IP address.

---

### Post by dilyard on 2006-01-27
Well, that certainly makes sense.  The frustrating part is that I don't have this problem on my RH or SuSE systems and they're using the same DHCP servers, the same DNS servers and are on the same subnet.  Debian/Ubuntu seems to take after Sun in this regard.

I'm done trying to figure it out so I'm just going to request a static IP for the workstation.  I like Ubuntu for my laptop and home use, but I think we'll stick to SuSE for the office.

Thanks again for your time.

---

### Post by ranf on 2006-01-27
Have a look at:

/etc/dhcp3/dhclient.conf

```
#send host-name "andare.fugue.com";
```

---

### Post by dilyard on 2006-02-07
Ranf - Thanks for the info.  Its so simple and obvious that I completely ignored this line.  Uncommenting it and putting my host and domain in did the trick.

Thanks again!

---

### Post by ranf on 2006-02-07
Nice to hear that it worked.

I'd be interested in how SuSE does this.

---

### Post by askreet on 2008-04-07
"There is no-where in the dhcp/dns systems to allow for the client to tell the dns server what its name is."

That is a very incorrect statement.  In a Windows Active Directory network this practice is very common and Windows 2000 and XP support what is called "Dynamic DNS updates."

Generally speaking, the DHCP servers can be configured to take this step for other clients (Linux, Windows NT/95/98) that do not support this feature.

I've running into the same issue, I'm glad that you've pointed out that Red Hat and SUSE support this feature, it makes me confident that dhclient3 supports it as well.

Good Luck!
- askreet

---

### Post by askreet on 2008-04-07
I guess dhclient allows you to send a hostname TO BE registered with DNS back to the DHCP server, which can register for you if properly configured.  There appears to be no actual options to have the dhcp client register with the DNS server.  I believe Red Hat uses DHCPCD, instead of DHCLIENT.  I dont have to time to see if this is a better option right now, unfortunately.

---

### Post by ekravche on 2008-04-17
> **ranf said:**
> Have a look at:

/etc/dhcp3/dhclient.conf

```
#send host-name "andare.fugue.com";
```


I've tried that but it doesn't seem to work for me.

Any ideas as to why? I'm running ubuntu 5.10

Thank you in advance.

---

### Post by Gunner_Sr on 2008-05-26
> **ranf said:**
> Have a look at:

/etc/dhcp3/dhclient.conf

```
#send host-name "andare.fugue.com";
```

FYI, this is great as it told me where to look on my Hardy server as I use DNS/DHCP for everything. One thing to be careful of, when comparing these files from desktop to server they are completely different. That is the desktop version has examples commented out, whilst the server doesn't have anything.

Interesting, maybe a bug. :)

-Gunner_Sr

---

### Post by parker13 on 2008-05-27
> **ekravche said:**
> I've tried that but it doesn't seem to work for me.

Any ideas as to why? I'm running ubuntu 5.10

Thank you in advance.

Adding the following line to /etc/dhcp3/dhclient.conf fixed it for me (running Hardy):

```
send fqdn.server-update on;
```

Ref: [https://bugs.edge.launchpad.net/ubuntu/+source/dhcp3/+bug/10239/comments/24](https://bugs.edge.launchpad.net/ubuntu/+source/dhcp3/+bug/10239/comments/24)

---

### Post by askreet on 2008-05-27
> **ekravche said:**
> I've tried that but it doesn't seem to work for me.

Any ideas as to why? I'm running ubuntu 5.10

Thank you in advance.

As was figured out in a previous post, send host-name sends a request back to the DHCP server to register with DNS.  The DHCP server would have to have this feature, and have it configured properly.  What kind of DHCP server is it?

---

