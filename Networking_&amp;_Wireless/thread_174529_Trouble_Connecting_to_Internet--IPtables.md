---
title: "Trouble Connecting to Internet--IPtables?"
date: 2006-05-12
forum: Networking &amp; Wireless
---

### Post by dacky on 2006-05-12
I just had Ubuntu Dapper working with squid, dansguardian and samba (1 hour ago).  I followed [http://www.ubuntuforums.org/showthread.php?t=91370&highlight=iptables+masquerade](http://www.ubuntuforums.org/showthread.php?t=91370&highlight=iptables+masquerade).  It was all working fine.  I had to move the computer to a new IP address.  Now I can't get any internet.  I also am using this for ltsp, which was working but is not now.  

I suspect iptables and proxy but don't know how to fix them.  How can I check the iptables and proxy?  How can I return them to default and start over?

I need squid to work and dansguardian (which worked before I had a problem).  I stopped squid and still no internet.  Something is wrong in the networking.

---

### Post by dacky on 2006-05-13
I've found two options.  Which one of the following will work with squid, dansguardian, and squidguard, for transparent proxy?  I don't want thin clients nor windows machines hooked to the server to bypass a proxy.  I have Dapper fresh install and will load ltsp.

iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner squid -j ACCEPT 
iptables -t nat -A OUTPUT -p tcp --dport 3128 -m owner --uid-owner squid -j ACCEPT 
iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner EXEMPT_USER -j ACCEPT 
iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-ports 8080 

Or . . .

iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner proxy -j ACCEPT
iptables -t nat -A OUTPUT -p tcp --dport 3128 -m owner --uid-owner proxy -j ACCEPT
iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-port 3128

What is the difference with the owner and where do I change this so the above works?  Will this be permanent?  How do I make it permanent?  Thanks for any help.

---

