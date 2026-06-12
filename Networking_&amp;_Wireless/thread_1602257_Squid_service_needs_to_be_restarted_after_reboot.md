---
title: "Squid service needs to be restarted after reboot"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by maminyana on 2010-10-21
I have a problem with my Squid server.
Anytime I reboot the server, Squid doesn't work properly. But the service is up! 
If I ask the system with "sudo service squid status" responds that is running

I have to manually restart the service with: 
sudo service squid restart
After that It works OK.

Since the server is a classroom server, and all the teachers that use the server aren't able to manually restart the service, I need to fix this problem. 
Any suggestion? Docs I have to check?

---

### Post by sv2dgi on 2011-03-10
Same issue here. The strangest thing of all is that I have two identical servers, one faces the problem the other does not...

---

### Post by JGJones on 2011-09-21
I was having this problem and so I looked on Ubuntu forums to look for a solution. However I've figured it out - it appears that as my computer is using wireless (I'm using a localhost squid server), squid starts up before any network connection is established and this is why it doesn't work.

I think it's to do with the failure to pick up the DNS server addresses as the networking haven't started yet so I've edited the /etc/squid/squid.conf file to add this line:

dns_nameservers IP_ADDRESS

IP_ADDRESS - this is your DNS servers that you use for Internet access

It seemed to have resolved it for me. I hope this helps you.

---

