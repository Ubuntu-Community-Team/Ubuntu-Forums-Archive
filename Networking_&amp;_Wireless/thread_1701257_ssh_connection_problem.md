---
title: "ssh connection problem"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by crotchet on 2011-03-06
hi everybody:

I have two static IP address, one is 59.77.35.120, and the other is 210.34.15.88. If I use the first IP, I can login a remote server faepop36.tugraz.at using ssh. But when I use the second IP, there is always an error like:

ssh: connect to host faepop36.tugraz.at port 22: Connection timed out

Who know the reason??? 

I appreciate your suggestion and help!!!

Thanks

---

### Post by kevdog on 2011-03-06
It doesn't sound like a ssh error, rather a routing error.  Can you ping by name??  Have you tried to a port scan with nmap on the name or ip address and port?

---

### Post by crotchet on 2011-03-06
Thanks for your reply. I did try to ping the server, the result is like

PING faepop36.tugraz.at (129.27.161.141) 56(84) bytes of data.
64 bytes from faepop36.tu-graz.ac.at (129.27.161.141): icmp_seq=1 ttl=43 time=250 ms
64 bytes from faepop36.tu-graz.ac.at (129.27.161.141): icmp_seq=2 ttl=43 time=249 ms
64 bytes from faepop36.tu-graz.ac.at (129.27.161.141): icmp_seq=3 ttl=43 time=249 ms
64 bytes from faepop36.tu-graz.ac.at (129.27.161.141): icmp_seq=4 ttl=43 time=249 ms

It seems like that the Internet is OK. Could you please give me some hints about how to do a port scan??

I am quite new to linux, thanks a lot!






> **kevdog said:**
> It doesn't sound like a ssh error, rather a routing error.  Can you ping by name??  Have you tried to a port scan with nmap on the name or ip address and port?

---

### Post by kevdog on 2011-03-06
nmap is the utility I would install from the repository.

Then use it on the command line like:
nmap -sS <ip_address or DNS_name>

specifically for just a port 22 scan it would be

nmap -sS -p 22 <ip_address or DNS_name>

---

### Post by crotchet on 2011-03-07
I really appreciate your help. I have scanned the port 22, the result is like

nmap -sS -p 22 faepop36.tugraz.at

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-03-07 16:06 CST
Interesting ports on faepop36.tu-graz.ac.at (129.27.161.141):
PORT   STATE    SERVICE
22/tcp filtered ssh

Nmap done: 1 IP address (1 host up) scanned in 2.83 seconds



It seems like that the port 22 is filtered by something (firewall??). What can I do now??

Thanks a lot






> **kevdog said:**
> nmap is the utility I would install from the repository.

Then use it on the command line like:
nmap -sS <ip_address or DNS_name>

specifically for just a port 22 scan it would be

nmap -sS -p 22 <ip_address or DNS_name>

---

