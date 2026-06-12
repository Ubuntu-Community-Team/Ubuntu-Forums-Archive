---
title: "can't access Port 443 from outside"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by danski on 2009-11-06
I'm trying to set up SSL on my apache2 server. And I can't seem to access [https://myipaddress](https://myipaddress) from my pc's browser (different pc to the server).

I'm hoping people can help me problem solve this, as I'm stumped.
Here is what I have discovered:

On the server: lynx [https://localhost](https://localhost) works as expected, so apache seems to be set up ok to serve https.

On the server lynx [https://mydomain](https://mydomain) times out.

Trying to access both my public ip and domain name with https through firefox on my pc both fail. However I can access these through normal http in the browser no problems.

I did a netstat -A and port 443 seems to be listening.

I checked my iptables (iptables -L) and there are no rules set up at all.

Any advise would be greatly appreciated.

---

### Post by Tony Ricena on 2009-11-06
I am assuming that a router is present?  Did you setup the router to allow those ports to access the internet and allow incoming connections to those ports?

---

### Post by danski on 2009-11-06
The server itself is set up on an Amazon EC2 Cloud. So I don't really think I have any control over router settings given that it is on a virtual server. I'm assuming that it isn't a router issue though. ?

---

### Post by danski on 2009-11-07
Ok.. this one is Resolved.

It was never a Ubuntu or Apache issue.

EC2 has it's own firewall where you have to add the ports you would to open.

i discovered the solution here:
[http://stackoverflow.com/questions/919008/ec2onrails-ssl-apache-no-response-on-port-443](http://stackoverflow.com/questions/919008/ec2onrails-ssl-apache-no-response-on-port-443)

---

