---
title: "pxe booting - server does not respond to arp"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by dmatusow on 2010-01-21
I am trying to get a server to boot off the lan (pxe). I added a tftp server and tested it as operating successfully. I just plugged the pxe-server in and see the dhcp request/response as expected. The pxe-server then sends out an arp to the same address as the dhcp exchange, but the server never responds. I have a few questions.
 
1. as the pxe-server already has info on the mac/ip-addr, why is it now sending another arp
 
2. why doesn't the server respond? I have most of my network setup the same way and the dhcp exchange is fine.
 
3. I'm guessing that the arp is triggered by the bootp exchange (next-server).
 
I do not have the server in the host table under that address. 
 
127.0.0.1 localhost
127.0.1.1 ubuntu-desktop
192.168.5.101 windows1
 
Do I need to add 192.168.5.120 with a name to get arp to respond?
 
Thanks

---

### Post by dmatusow on 2010-01-21
more info:
 
I can see that the pxe-server is trying to request the linux file, as seen in the attached.  I have tested the tftp server and it worked perfectly.  I never see a tftp transfer happen.  
 
????

---

