---
title: "I did it again"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by computerfox on 2011-03-06
Hey guys, I did it again.  Out of nowhere my virtual servers stopped working.  I cleaned out the system and tried setting it up as usual, but still can't get it back up.


I am still forwarding the proper ports.
I am able to access the directory through the main server address (foxwebhosting.dyndns.org), but not through computerfoxdesign.net.

I have no idea what happened.

Attached is all the other information I think should be known as of now.

Any help would be appreciated.  Thank you.

---

### Post by SoftwareExplorer on 2011-03-06
Are you sure that the DNS for foxwebhosting2.dyndns.org is pointing at the right IP? It seems like all the ports at foxwebhosting2.dyndns.org are filtered (connection requests to them are ignored without sending a 'sorry you can't connect to that port' message) except for 4567.
You should at least have port 53 (DNS) and 80 (Webserver) open. 
I suspect that foxwebhosting2.dyndns.org (and probably foxwebhosting.dyndns.org too) are pointing to the wrong IP. How would that effect computerfoxdesign.net? To look up computerfoxdesign.net I have to find out connect to the DNS server at foxwebhosting2.dyndns.org, which means I have to know the IP address. If the address is wrong, I won't be connecting the correct DNS server.

---

### Post by computerfox on 2011-03-06
Good point.  I actually tried to get into the server outside of the network and it wouldn't work.  That possibly could be the problem.

Is the attached what you mean?

How would I check which IP the site is pointing to?

---

### Post by computerfox on 2011-03-06
Got it!

For future reference because I know at least I'm gonna end up needing it.

1)Check the dns in webmin->host/dns
2)Make sure all the virtual servers are on port 80
3)Default server MUST be on any port, any address
4)Make sure you add a [www.example.com](www.example.com) virtual server
5)MUST have a DNS Zone for each virtual server
6)Make the addresses in the DNS Zone are pointing to the public IP
7)Make sure you don't forget to apply changes
8)IF IT AINT BROKEN DON"T FIX IT
9)DON'T DO ANYTHING STUPID
10)DON'T GIVE UP.

---

### Post by SoftwareExplorer on 2011-03-06
I'm pretty sure what you posted a screenshot of is what DNS servers to ask when trying to find out mhat a DNS name points to. What we want is not to change the servers we ask (who will eventually refer us to the right DNS server to ask), but to change what the server that is in charge of answering questions about what IP address foxwebhosting2.dyndns.org says foxwebhosting's address is.

A good command line tool for figuring out DNS things is the 'dig' program.
You can ask what IPv4 address a domain name points to by running something like 'dig a <domainname>'. You can ask a specific DNS server by adding "@<server name or ip>', giving you something like 'dig a <domianname> @servername'. So for a real life example, 'dig a foxwebhosting2.dyndns.org @74.82.42.42'. In your case, where you are trying to troubleshoot, it's probably good to pick a DNS server that is out on the internet specifically, so that the default wont get choosen. We don't want the default, because it would start with your computer, which is not necessarily what the rest of the world sees.

Edit:Looks like you figured it out while I was still typing.

---

### Post by kevdog on 2011-03-06
I thought for a minute by the name of this thread this was an obscure Brittany Spears reference.

---

### Post by computerfox on 2011-03-07
> **SoftwareExplorer said:**
> I'm pretty sure what you posted a screenshot of is what DNS servers to ask when trying to find out mhat a DNS name points to. What we want is not to change the servers we ask (who will eventually refer us to the right DNS server to ask), but to change what the server that is in charge of answering questions about what IP address foxwebhosting2.dyndns.org says foxwebhosting's address is.

A good command line tool for figuring out DNS things is the 'dig' program.
You can ask what IPv4 address a domain name points to by running something like 'dig a <domainname>'. You can ask a specific DNS server by adding "@<server name or ip>', giving you something like 'dig a <domianname> @servername'. So for a real life example, 'dig a foxwebhosting2.dyndns.org @74.82.42.42'. In your case, where you are trying to troubleshoot, it's probably good to pick a DNS server that is out on the internet specifically, so that the default wont get choosen. We don't want the default, because it would start with your computer, which is not necessarily what the rest of the world sees.

Edit:Looks like you figured it out while I was still typing.

Yeah, lol.  But I would probably know MUCH less if you didn't inform me what you have in the previous threads.  That's why I PM you directly if I need help again

---

### Post by computerfox on 2011-03-07
> **kevdog said:**
> I thought for a minute by the name of this thread this was an obscure Brittany Spears reference.

I was counting down the seconds till someone said that. LOL

---

