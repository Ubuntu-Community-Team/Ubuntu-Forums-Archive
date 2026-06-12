---
title: "Bind hack and cloned localhost"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by Alfie O'mega on 2010-02-08
Hi All,
 
I have a problem and maybe one of you have the solution.
 
1. I have been the victim of some kind of DOS attack. When I try to connect, my computer connects on port 53 with another computer that is a LAN address. I then can't connect.
 
2. I can get something out of Nmap however. It has ISC Bind 9.5.1-P2.1 operating on port 53/udp which is open, .
 
3. In addition Nmap tells me when I scan my localhost: Warning: Hostnmae localhosts resolves to 2 IPs. Using 127.0.0.1. This may explain why despite closing port 53 this attacker seems to walz right in. In addition, I should note that I had discovered that to access the Network Manager applet I had to enter a system password twice--my old password (I change them regularly) and my current passworld--the keyring is granting access to two different versions of 127.0.0.1. 
 
4. Looked at CERT's website and there is some kind of DOS vulnerability with ISC Bind. There were patches listed for various systems, but not Ubuntu. 
 
5. I seem to have two different problems going on: First, that my localhost IP addresss has somehow been cloned and the attacker can access this alternative localhost. Second, that my service can be denied using bind somehow. 
 
Here are my questions:
 
A. How do I get rid of this second IP address and patch the hole that allowed it to be created in the first place. 
 
B. How do I patch the DOS vulnerability and still get access to the Internet. 
 
Grateful for all help attempted.
 
Al
 
;)

---

### Post by Alfie O'mega on 2010-02-08
Anyone?  I know it's a tough one and it probably requires a reinstall, but am trying to avoid this as the problem will certainly recur.

---

