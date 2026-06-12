---
title: "Surfing to my own ip-address won't work"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by Kruptein on 2009-12-08
I know what my external ip-address is, caus conky gave it and on those whatismyip sites on the net they give the same;

But if I typ that ip-address in my browser it says it doesn't exist :(

So what am I doing wrong/what is disabled or enabled that shouldn't be?

---

### Post by argosreality on 2009-12-08
What exactly are you trying to do? Browsing to your own address won't bring anything up unless you have a server listening for some activity. Are you trying to share files, run a website, email? What?

Also do you have a router? If so, you'll have to forward ports from the routers configuration pages to the appropriate computer you are trying to access for that service

---

### Post by Kruptein on 2009-12-08
Sorry I probably had to say;

I'm running apache php and mysql on my computer and can reach them perfectly if I go to localhost or 127.0.0.1
but I want to be able to reach that server on an other computer and I thought that you only should surf to the computer's external ip address
but I'm apparently wrong =)

---

### Post by puppywhacker on 2009-12-08
That would be the case if your ADSL or Cable modem or whatever would be in bridged-mode, where the public ip-address is on your PC. Instead you seem to have a natwork address translation (NAT) where your PC has a private address and all your traffic is translated on the modem. You will need Port forwarding to be abled to reach your PC from the internet, or use the private address (probably something like 192.168.0.2)

---

### Post by lisati on 2009-12-08
Hmmmmm.... interesting. For me, surfing to my external IP address from within my home network, as given by [http://whatismyipaddress.com](http://whatismyipaddress.com), takes me to my modem config page. Has done for a while.

---

### Post by doas777 on 2009-12-08
> **lisati said:**
> Hmmmmm.... interesting. For me, surfing to my external IP address from within my home network, as given by [http://whatismyipaddress.com](http://whatismyipaddress.com), takes me to my modem config page. Has done for a while.

I usually disable managment from the wan interface. I also have a spoofkill rule at the top of my router firewall list, to drop any traffic coming inbound on the external interface, bearing the source IP range of my internal network.

OP: have you forwarded the ports on your router inbound to your servers address/port?
[http://portforward.com/](http://portforward.com/)

and if so, can you test it sucessfully at:
[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

### Post by lisati on 2009-12-08
> **doas777 said:**
> I usually disable managment from the wan interface. I also have a spoofkill rule at the top of my router firewall list, to drop any traffic coming inbound on the external interface, bearing the source IP range of my internal network.

OP: have you forwarded the ports on your router inbound to your servers address/port?
[http://portforward.com/](http://portforward.com/)

and if so, can you test it sucessfully at:
[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

Thanks for the suggestions.

---

### Post by Kruptein on 2009-12-09
> **puppywhacker said:**
> That would be the case if your ADSL or Cable modem or whatever would be in bridged-mode, where the public ip-address is on your PC. Instead you seem to have a natwork address translation (NAT) where your PC has a private address and all your traffic is translated on the modem. You will need Port forwarding to be abled to reach your PC from the internet, or use the private address (probably something like 192.168.0.2)


I can reach my server with my private address on my own laptop, but not on another computer.. that's my main goal otherwise I would just typ localhost =)

---

### Post by puppywhacker on 2009-12-09
If your other computer is in the same network, you probably have a firewall like ufw or firestarter blocking access to port 80 from the network, therefor localhost will work, but inside your own network not. 

from the commandline you can look at the firewall rules with
```
iptables -L -v
```
I expect it will show around 30 lines of default firewall rules.

and flush them for the time your computer is not rebooted with
```
iptables -F
```

Apart from this, if your other computer is on the internet, you will also need portforwarding.

---

### Post by Kruptein on 2009-12-09
if I flush them, there will not be any security hole I hope?
(in meantime I also allowed http port 80 with firestarter but this didn't make a chanche)

and I have more then 30 rules ;)

---

