---
title: "Wireless router question"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by null.byte on 2009-03-19
Hello :) I bought an ASUS WL-520GC wireless router. My IP is dynamic. 
I opened the port "80" because I have a web server. The IP I pointed the port to is 192.168.1.2.

By the way, I see that sometimes, the IP is changing from 192.168.1.2 to 192.168.1.3 or .4, etc... How can I make it stay only on 192.168.1.2? I am talking about the local one, not the public one.

Thanks in advance.

---

### Post by dacorr on 2009-03-19
you would need to set the webserver host computer IP to static instead of dynamic.

the network settings area would be the best place to look.

however with a router set to DHCP if the webserver is ever powered down the router could still assign the webserver IP to another machine.

You can set the router to use static but you would need to manually set the IPs of all machines on the network.

---

### Post by null.byte on 2009-03-19
There are just 2 machines: my desktop and a laptop. How can I set the router to use static IP?

---

### Post by dacorr on 2009-03-19
depends on the router, if you enter the router IP propabaly 192.168.1.1 into a web browser it should allow you to use webadmin. you will need to login in using the default username and password unless you have changed it.

there should be a section on LAN or WLAN DHCP this is what automatically assigns IPs.

if you only have two computers it will probably be easier to just assing them both to static as nothing else will be asking for an IP

you will need to enter the following on your computers

IP - 192.168.1.2
Mask - 255.255.255.0
Gateway: 192.168.1.1

DNS1 :192.168.1.1

you may want to set them to static before you disable DHCP if you decide to.

---

### Post by null.byte on 2009-03-19
Thanks a lot dacorr!

---

### Post by apmcd47 on 2009-03-19
Check your router to see what range it uses for dynamic IP addresses. Choose two addresses outside this range (remember that you only change the last component of the address!) Now you have two choices: Set the router to permamently assign these addresses to the MAC addresses of your two machines; or assign the addresses on the computers themselves.

I assume you want both machines on static addresses. 

You can find the MAC address with ipconfig on Windows - I can't remeber offhand whether ifconfig on Linux will give you that info, but the ARP table should.

Andrew

---

### Post by null.byte on 2009-03-19
Also thanks to apmcd47 :) Problem solved! :D

---

