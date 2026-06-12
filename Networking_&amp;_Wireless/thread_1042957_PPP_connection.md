---
title: "PPP connection"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by rustybar on 2009-01-18
Hi guys, I have a enquiry regarding ppp connection to other system from ubuntu or Linux in generally. Hope you all can advise me.

I have 2 system, one is using ubuntu 8.10 and is connected to the internet, the other is an embedded PC which is not connected to internet. Both system are web server which host some configuration pages to configure certains stuffs. The embedded PC is connected to the Ubuntu through ppp connection using null modem cable. 

Now since both are web server, when i type the ip address, naturally the configurations webs pages of the ubuntu will be shown. However, I would like to access the configuration web pages of the embedded system too.
 
How would I be able to do that? Is it through updating the ARP or the iptables to redirect it? Please advise. Thanks!

---

### Post by Macchi on 2009-01-18
A simple way to set the communication between two machines it to connected their network interfaces through a crossed ("or null modem") cable, then set static IP addresses, set both machines the same network & netmask, and then (again for both machines) provide the address of the other machine as the gateway.
Test the connection for instance with the command "ping -c 3 192.168.x.y from each machine.

With a suitable set I believe you will not have to use iptables to set routing, unless you want to access the other webserver from the internet. 



PS: Such combinations of heterogeneous network internfaces and different ways to connect can be a pain to debug. I am now experimenting to find a solution for some particular limitations of the network manager.

---

### Post by rustybar on 2009-01-18
Hi, thanks for the reply. I would actually like to access the other web server through the internet too. So I'm just thinking how will it be possible for 1 ip address to be mapped for accessing 2 web servers.. Any advice for that? Thanks!

---

