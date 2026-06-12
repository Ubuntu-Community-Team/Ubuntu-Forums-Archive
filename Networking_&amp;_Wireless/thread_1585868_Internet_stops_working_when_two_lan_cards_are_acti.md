---
title: "Internet stops working when two lan cards are active at the same time"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by xihad76 on 2010-10-01
i was using fire starter to share internet connection in between my ubuntu (server) and my friends windows pc (client).
everything was working fine until i mistakenly (i think so) messed up with any of the network setups.and now i can't figure out what is going wrong actually.
with my single lan card ( through which my ubuntu is connected to the internet using DHCP server) internet works fine. but as soon as the second lan card goes active it stops working.the  second lan card is used to connect to my friend's pc. 

with two lan cards active i can still ping adresses (i.e google.com) but cant browse anything using web browser or login to pidgin or any kind of web activities. 

here goes my two lan cards' settings:

eth1 connection profile: (which is connected to internet using DHCP server)
ip: 192.168.120.79
subnet mask: 255.255.252.0
Default Gateway:192.168.120.1
DHCP server: 192.168.120.1 


eth0 connection profile: (which is used to connect to my friends windows pc through a hub)

ip: 172.16.1.1
subnet mask: 255.255.255.0
Gateway: 0.0.0.0 


any idea about the problem or where i messed up actually? 
thnx in advance..

---

### Post by dmizer on 2010-10-01
Don't use firestarter to share internet. You should uninstall it, as it really does more harm than good.

Ubuntu comes with the ability to share internet out of the box with no additional tools. Take a look here: [http://www.ge.ubuntuforums.org/showpost.php?p=9709154&postcount=2](http://www.ge.ubuntuforums.org/showpost.php?p=9709154&postcount=2)

---

### Post by xihad76 on 2010-10-01
hello there,

Thank you very much for your kind reply.

as u said, i have uninstalled fire starter. and installed gufw.
then in ipv4 settings of my local ethernet card i have set it to "Shared to other computers". 
now how should i configure my client pc? it is run by windows. 

my client pc's ip is 172.16.1.2 and i want that only this pc should have access to internet as there are some other pc also in the network which i don't own. for this what should be the firewall rule? 

thank you again for your immense help.

---

### Post by dmizer on 2010-10-01
> **xihad76 said:**
> hello there,

Thank you very much for your kind reply.

as u said, i have uninstalled fire starter. and installed gufw.
then in ipv4 settings of my local ethernet card i have set it to "Shared to other computers". 
now how should i configure my client pc? it is run by windows. 

my client pc's ip is 172.16.1.2 and i want that only this pc should have access to internet as there are some other pc also in the network which i don't own. for this what should be the firewall rule? 

thank you again for your immense help.

Your client PC should now be able to browse the internet. If not, you may have to add DNS servers. You can try using OpenDNS servers: 208.67.222.222 and 208.67.220.220

If you need to block other PCs on the network, that's a different problem, so it might be wise to start another thread.

---

### Post by xihad76 on 2010-10-01
i have tried this way stated here: [https://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/](https://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/)

as my wired internet connection line,server pc & client pc - all are networked through the same hub, client pc acquires the dhcp adress automatically from the wired internet connection line, not from that of server pc.

so the steps stated in the above mentioned link is not working for me.

---

### Post by xihad76 on 2010-10-01
> **dmizer said:**
> Your client PC should now be able to browse the internet. If not, you may have to add DNS servers. You can try using OpenDNS servers: 208.67.222.222 and 208.67.220.220

If you need to block other PCs on the network, that's a different problem, so it might be wise to start another thread.

no its not working. 

i have also tried using those two open dns. still no luck.

my client pc's configuration is now:

ip: 172.16.1.2 
subnet mask: 255.255.255.0
no default gateway 
DNS servers: 208.67.222.222 and 208.67.220.220

---

### Post by dmizer on 2010-10-01
> **xihad76 said:**
> as my wired internet connection line,server pc & client pc - all are networked through the same hub, client pc acquires the dhcp adress automatically from the wired internet connection line, not from that of server pc.

This is probably the source of your problem. The computer you wish to share internet from needs to be between the hub and the internet connection like so:

Modem---eth0 (Ubuntu pc with ICS) eth1---hub---rest of network

---

### Post by xihad76 on 2010-10-01
Ok. i have figured it out and describing how i did it. hope that might help others who will experience the same issue.


firstly, in my local Ethernet(eth0) ipv4 settings i selected "Shared to other computers". ( like me, if you are editing an existing connection profile in which ipv4 setting was set manually before, make sure that you remove all addresses from route option.)

then, i enabled the profile for eth0 and noted down the ip address and subnet mask that ubuntu automatically assigned to it. ( you can see it by right clicking network manager icon from the top bar and select "Connection information".) in my case local ethernet ip was: 10.42.43.1 , subnet: 255.255.255.0 . i also noted down the dns addresses that was acquired by the other ethernet card connected to internet from DHCP server automatically.


finally, in my client pc i took an ip address from the same range of eth0 (10.42.43.2), subnet: same as eth0 (255.255.255.0), default gateway: server pc's local ethernet ip (10.43.42.1) dns addresses: same as assigned by the DHCP server of Internet connection.  

thats it!

---

### Post by xihad76 on 2010-10-01
> **dmizer said:**
> This is probably the source of your problem. The computer you wish to share internet from needs to be between the hub and the internet connection like so:

Modem---eth0 (Ubuntu pc with ICS) eth1---hub---rest of network


Dmizer, Thnk U very much for all your help! you have been really very helpful. take care.

---

