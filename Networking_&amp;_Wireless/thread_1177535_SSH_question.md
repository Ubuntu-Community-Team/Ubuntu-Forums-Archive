---
title: "SSH question"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by bkulaga on 2009-06-03
Here is the deal.... I tried connecting to my ssh on the same computer where the ssh server is running at and I get this 

bartosz@bartosz-desktop:~$ ssh -p2222 bartosz@174.102.141.211
ssh: connect to host 174.102.141.211 port 2222: Connection refused

why is the connection refused??? I am behind a router i forward the ports and everything
do i have to add something to the sshd_config file??? or something?

when i type in ssh -p2222 bartosz@localhost that works but when i try to type in the actual ip address it does not any ideas?

---

### Post by Iowan on 2009-06-03
**ifconfig** confirms that is the right address? 
What's in /etc/hosts file? (Just grasping... looks like it *should* work...)
 You might post */etc/ssh/sshd_config *.

---

### Post by Brandon Williams on 2009-06-04
'whois 174.102.141.211' tells me that you're trying to connect to an external address, the one provided by your cable service provider. Is this address actually configured on the machine? Or is it the external address used by a router that is port-forwarding SSH traffic to an internal machine?

On my home network, I have an ssh server with local address 192.168.1.17. My router port-forwards ssh traffic to that internal address. If I try to use ssh on a local machine to connect to my ssh server using the router's public IP address as the destination, the connection is refused, even though I can use that address to connect from an external host. When I connect from a host on my internal network, I have to use the internal IP address.

---

