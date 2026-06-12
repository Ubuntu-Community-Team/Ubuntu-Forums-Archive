---
title: "Ubuntu server - can't resolve hostname"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by jatoo on 2010-07-08
I recently set up an Ubuntu server computer (10.04) with the hostname 'morbo', and with a static IP address.

With all my other ubuntu systems i can ping and ssh using their host names, like:
```
ping alex-ubuntu.local
ssh alex-msi.local
```

With the server however, i can't reach it via 'morbo.local' nor can i reach my other ubuntu systems from morbo by their hostnames.

I have seen a 'quick and dirty' solution which might help here : [http://art.ubuntuforums.org/showthread.php?t=1371711](http://art.ubuntuforums.org/showthread.php?t=1371711) , but i don't want to have to add every system to morbo's list and morbo to every systems list, and because it works without manual configuration on all my other systems, i don't see why it shouldn't be possible here.

Currently everything connects to one d-link router - does this mean it is the DNS server? 

If anyone could help me out with this or point me in the right direction to learn how this stuff works it would be greatly appreciated.

Thanks!

---

### Post by Yarui on 2010-07-08
I'm pretty sure you have to add the hostnames to the hosts file like that link suggests.  I have never seen a linux machine that can successfully resolve hostnames without putting them in the hosts file.

---

### Post by Sanjeevtrip on 2010-07-08
does all your other machines accessible by hostname
do nslookup to any hostname and you should get the dns server ip, where you can add this new host.

---

### Post by jatoo on 2010-07-09
Thanks for your replies,

> **Yarui said:**
> I'm pretty sure you have to add the hostnames to the hosts file like that link suggests.  I have never seen a linux machine that can successfully resolve hostnames without putting them in the hosts file.

I haven't manually added any host names to any other Ubuntu systems and they are all working fine, i can ping/ssh any of the from any of the others using their names, just not the server.

> **Sanjeevtrip said:**
> does all your other machines accessible by hostname
do nslookup to any hostname and you should get the dns server ip, where you can add this new host.

The output from nslookup:
```
alex@alex-ubuntu:~$ nslookup alex-msi.local
Server:		192.168.1.1
Address:	192.168.1.1#53

** server can't find alex-msi.local: NXDOMAIN

```

192.168.1.1 is my router.  I haven't had to set anything up in there for my other systems to make the accessible by their host name.

Any ideas?

---

### Post by Iowan on 2010-07-09
What is in the server's */etc/resolv.conf*?
(Maybe I missed that information in what you already provided)

---

### Post by jatoo on 2010-07-09
Iowan, 

nope, i hadn't.

just this:

```
nameserver 192.168.1.1
```

---

### Post by Iowan on 2010-07-09
Are the other Ubuntu machines static addresses or DHCP? I use DNSMasq for DNS/DHCP - even DHCP machines can be reached via hostname... IF they've included their hostname in */etc/dhcp3/dhclient.conf* on the **send hostname** line.

---

### Post by capscrew on 2010-07-09
> **jatoo said:**
> Thanks for your replies,



I haven't manually added any host names to any other Ubuntu systems and they are all working fine, i can ping/ssh any of the from any of the others using their names, just not the server.



The output from nslookup:
```
alex@alex-ubuntu:~$ nslookup alex-msi.local
Server:		192.168.1.1
Address:	192.168.1.1#53

** server can't find alex-msi.local: NXDOMAIN

```

192.168.1.1 is my router.  I haven't had to set anything up in there for my other systems to make the accessible by their host name.

Any ideas?

Do you have Avahi running in this network?  That is what is used to configure a system if the user does nothing  to configure.  What are the IP addresses of all the hosts?

---

### Post by jatoo on 2010-07-09
> **Iowan said:**
> Are the other Ubuntu machines static addresses or DHCP? I use DNSMasq for DNS/DHCP - even DHCP machines can be reached via hostname... IF they've included their hostname in */etc/dhcp3/dhclient.conf* on the **send hostname** line.

One of the other machines is static, the rest DHCP.  I've tried making the server DHCP and static, but when i make it DHCP it doesn't show up in my router, and doesn't take the reserved address set for it.

> **capscrew said:**
> Do you have Avahi running in this network?  That is what is used to configure a system if the user does nothing  to configure.  What are the IP addresses of all the hosts?

I don't have Avahi running on the server, but i just checked two other systems and they both have avahi-daemon processes running.

I hope this is what you want, this is a list of the systems in the house:
```
alex-msi     192.168.1.9   wireless, DHCP
alex-ubuntu  192.168.1.33  static
HPE17523     192.168.1.2   wireless, DHCP
Nick-PC      192.168.1.3   wireless, DHCP
john-ubuntu  192.168.1.5   wireless, DHCP
```

Thanks for your replies.

---

### Post by jatoo on 2010-07-09
Got it!

Thanks capscrew, i installed avahi-daemon and avahi-autoipd, restarted networking and voila! everything works now.

I'm not sure if i needed to install both of those, but it's working now, that's the main thing.

Thanks everyone for your help!

---

### Post by jatoo on 2010-07-10
Ok, i marked as solved prematurely (can i change that?).  After restarting i am back to where i was before.  Do i need to configure Ahavi somehow?  Set it to run on startup?

---

### Post by capscrew on 2010-07-10
> **jatoo said:**
> Ok, i marked as solved prematurely (can i change that?).  After restarting i am back to where i was before.  Do i need to configure Ahavi somehow?  Set it to run on startup?

The settings are at: **/etc/avahi/avahi-daemon.conf **.  You can use the man pages for reference.

[**_Here _**]("https://help.ubuntu.com/community/HowToZeroconf")is some basic info.

I think if you are going to configure anything that you really should  look into installing some sort of **local **DNS system.  It seems kind of silly to have to configure something so you don't have to configure something else. 

I think DNSmasq would work very well in your LAN.

---

