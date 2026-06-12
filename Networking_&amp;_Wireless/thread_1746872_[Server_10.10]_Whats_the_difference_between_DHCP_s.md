---
title: "[Server 10.10] Whats the difference between DHCP server and IP masquerading"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by Jimboland on 2011-05-02
Can somebody explain me the difference between IP masquerading and NAT.
I know a DHCP server gives addresses to client computers, and masquerading 'masquerades' the private ip addresses so they can be used on the internet. But i don't understand how i can use both of them together to make a ubuntu server installation to work as a router. I have to enter the NAT tables, but i don't how to do it because i don't understand how to use it. 

NAT translates  private IP addresses to one public address, so why do i need to use masquerading? 

And DHCP assigns IP addresses to clients.

---

### Post by lz1dsb on 2011-05-02
According to the IP Masquarading How to:

[http://tldp.org/HOWTO/IP-Masquerade-HOWTO/](http://tldp.org/HOWTO/IP-Masquerade-HOWTO/)
"IP Masquerade is a networking function in Linux similar to the one-to-many  (1:Many) NAT (Network Address Translation) servers found in many commercial  firewalls and network routers.  For example, if a Linux host is connected to  the Internet via PPP, Ethernet, etc., the IP Masquerade feature allows other  "internal" computers connected to this Linux box (via PPP, Ethernet, etc.) to  also reach the Internet as well.  Linux IP Masquerading allows for this  functionality even though these internal machines don't have  **an officially assigned IP address**. MASQ allows a set of machines to **invisibly**  access the Internet via the MASQ gateway.  To other machines on the Internet,  the outgoing traffic will appear to be from the IP MASQ Linux server itself.   In addition to the added functionality, IP Masquerade provides the foundation  to create a HEAVILY secured networking environment.  With a well built firewall,  breaking the security of a well configured masquerading system and internal  LAN should be considerably difficult to accomplish."


With NAT in theory you could have many to many relations (i.e. you could have a pool of public addresses that you can use for the translation). 



But I don't know IP Masquarading that well...

---

### Post by capscrew on 2011-05-02
> NAT translates private IP addresses to one public address, so why do i need to use masquerading? 

Nat and IP masquerading are the same thing.  Different terms to describe the same thing.  Many private IP addresses masquerading (appearing as) 1 public IP address to the public Internet.

---

