---
title: "DNS fails to resolve hosts file entries"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by ml41782 on 2009-07-08
It doesn't seem to matter what I do I can't resolve with nslookup anything in the /etc/hosts file. The system always looks to the external DNS's and fails to resolve the internal network.

---

### Post by terazen on 2009-07-08
Nslookup query's dns servers like dig does.  If you try to ping the address it should check /etc/hosts first before trying dns.

---

### Post by ml41782 on 2009-07-08
It has been my understanding that the hosts file was for internal resolution for the machine itself and if it wasn't there then it looked outside to the external DNS. So if I want my mail to work I have to run DNS on my laptop ? 
 
This is starting to sound like microsoft

---

### Post by terazen on 2009-07-08
If ping resolves the name you want then mail should work as well.

I believe the file to check on would be your/etc/nsswitch.conf, but if ping works you shouldn't even need to look at it.

When I say "if ping works", I mean if it resolves the name.  Having it resolve a name to ip and actually getting a ping reply are 2 different things.

---

### Post by ml41782 on 2009-07-08
Thats what gets me. 
I can ping webserver and you see the resolution to 192.168.1.50
 
but the nslookup fails to resolve internal webserver within the box. 
 
 
127.0.0.1        localhost
192.168.1.50   webserver
192.168.1.10   webbox
# The following lines are desirable for IPv6 capable hosts
# ::1     ip6-localhost ip6-loopback
# fe00::0 ip6-localnet
# ff00::0 ip6-mcastprefix
# ff02::1 ip6-allnodes
# ff02::2 ip6-allrouters
# ff02::3 ip6-allhosts

---

