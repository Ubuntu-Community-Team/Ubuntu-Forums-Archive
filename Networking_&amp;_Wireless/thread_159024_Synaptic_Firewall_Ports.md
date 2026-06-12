---
title: "Synaptic Firewall Ports"
date: 2006-04-12
forum: Networking &amp; Wireless
---

### Post by Big Will on 2006-04-12
I'm running Ubuntu 5.1 and Kubuntu 5.1 behind an ISA 2004 firewall. What ports / protocols do I need to open up on the firewall to get to the various repositories?
I can see in the various browsers where to set proxy, although Konqueror is not keen to authenticate to the ISA box. 
As an aside - are there any other repositories I can get to?
Sorry - Linux newbie - after 15 years as a dedicated MS man I have finally seen the light - a month ago almost to the day!
Any helps greatly appreciated - as are any other hints / tips / places for documentation.

---

### Post by Darkriser on 2006-04-12
if you are refering to incoming ports - then none. synaptic doesn't need any incoming port for its functionality.

as it uses only http requests, you only need port 80 for outgoing traffic.

or am I absolutely wrong? :-k

---

### Post by Big Will on 2006-04-12
I can see where to set browsers up to use my proxy - I can not see where to set Synaptic up to do the same - help again?

Thanks for the quick reply too!

---

### Post by tomski on 2006-04-12
[QUOTE=Darkriser]if you are refering to incoming ports - then none. synaptic doesn't need any incoming port for its functionality.

as it uses only http requests, you only need port 80 for outgoing traffic.

or am I absolutely wrong? :-k[/QUOTE]


Repositories can and do use ftp:// as well as http:// [(check here)]("http://www.apt-get.org/main/")

so i would check :
/etc/apt/sources.lst

see if any listed have ftp:// in the lines for the repo's

if so then open the relative ports on the fwall
refer to the following url for a list of ports and the protocols they use :[URL="http://www.sockets.com/services.htm"]
ports[/URL]

also i thought that if a port is open for an outbound connection then it will automaticaly open the inbound one for that connection so long as the packets match up.

if not try to configure it in a way so that all connections from the LAN to the NET are allowed by default (might be bad if you have an infected machine on the LAN) IE: LAN is a trusted Zone & the NET is untrusted and f-walled

---

### Post by Big Will on 2006-04-12
Thanks you Tomski & Darkriser - quick responces and I've learned some more.

BUT - it still won't work. You see, port 80 is blocked - I use a proxy facing the inside of the LAN using port 8080 (like a lot of folks). So I need to let Synaptic know to use port 8080 instead of port 80 - which is the question I ought to have asked....

All the repositories in the file you let me know about are http sites, Dark.

Any ideas on the port redirection of Synaptic? I have set Network Proxy Preferences to apparently no avail, although Firefox is working fine once the same proxy info is fed into it...

---

