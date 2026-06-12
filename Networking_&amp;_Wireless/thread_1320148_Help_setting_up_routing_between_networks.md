---
title: "Help setting up routing between networks?"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by mtindell on 2009-11-09
Hello, I was hoping someone could enlighten me on how I should configure my setup... 

I have set up a Ubuntu server with two NICs. eth1 (192.168.1.1) is the onboard gigabit nic on my motherboard which is connected to my 2wire DSL gateway, and eth0 (192.168.10.1) is a standard PCI Netgear gigabit NIC which is connected to a 16 port 10/100 switch for my internal network. Both interfaces have been set up as static in the /etc/network/interfaces configuration file. The Ubuntu server is acting as a DRBL, DHCP, and general file server and all machines on the 192.168.10.0 network can PXE boot, use the internet, and ping/access any machines on the 192.168.1.0 network. The 2wire DSL gateway provides my wireless connectivity and hands out DHCP addresses starting at 192.168.1.50 for the laptops in my household. What is prompting this thread is that I would like to be able to access the 192.168.10.0 network from my wirelessly connected laptops that have been assigned 192.168.1.0 addresses from the wireless router.

It seems like it should be relatively easy to allow the machines on the 192.168.1.0 network to ping/access the machines on the 192.168.10.0 network, but I have been unable to get it set up properly to make this happen. I have done some reading around and have been unable to find someone with the exact same scenario I have here, which would enable me to compare notes. Any help or advice would be very appreciated, and might put this problem to rest! Thank you!

---

### Post by Iowan on 2009-11-09
I haven't really messed with routing table instructions. It seems like **route add -net 192.168.10.0 netmask 255.255.255.0 dev eth0** might work.
 Example is paraphrased from **man route** 
(the netmask might/not be required)
or the whole thing might not work...

---

