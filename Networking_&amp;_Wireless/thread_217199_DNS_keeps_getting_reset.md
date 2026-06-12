---
title: "DNS keeps getting reset"
date: 2006-07-16
forum: Networking &amp; Wireless
---

### Post by brentoboy on 2006-07-16
I use a static IP on my internal network.

I defined the DNS info from my ISP in the DNS area of the network settings. (I've been doing this since breezy, no issues)

Just recently (2 or three days -- probably with the last update) the dns settings are empty if I reboot.  Effectivly, no one in the house but me can figure out how to get online after a fresh reboot until after I reassign dns settings.

Is this happening to anyone else? Does anyone know how this might have started happening?  is there a way to force the system to keep the dns settings?  pls help.

---

### Post by lengguard on 2006-07-16
Go to properties and put in IP and gateway might help

---

### Post by brentoboy on 2006-07-16
it's already in there.

been there since day one (a few months back)

---

### Post by JamesB on 2006-07-17
> **brentoboy said:**
> I use a static IP on my internal network.

I defined the DNS info from my ISP in the DNS area of the network settings. (I've been doing this since breezy, no issues)

Just recently (2 or three days -- probably with the last update) the dns settings are empty if I reboot.  Effectivly, no one in the house but me can figure out how to get online after a fresh reboot until after I reassign dns settings.

Is this happening to anyone else? Does anyone know how this might have started happening?  is there a way to force the system to keep the dns settings?  pls help.

Hi 
There are several ways to get round this if you look round the forum, for me i edited /etc/dhcp3/dhclient.conf
prepend domain-name-servers <IP-FOR-YOUR-DNS-SERVER> (removing the #) and deleting 'domain-name-servers' from the request line 

Mine looks like this:

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
prepend domain-name-servers 212.74.112.66, 212.74.112.67;
request subnet-mask, broadcast-address, time-offset, routers,
domain-name, host-name,
netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;

You might need to reboot
Hope this helps

James

---

### Post by bigken on 2006-07-17
[LEFT]in the firefox browser type about:config and change network.dns.disablepv6 from fales to true 
:wink:

its worth a try 
[/LEFT]

---

### Post by brentoboy on 2006-07-17
> **JamesB said:**
> Hi 
There are several ways to get round this if you look round the forum, for me i edited /etc/dhcp3/dhclient.conf
prepend domain-name-servers <IP-FOR-YOUR-DNS-SERVER> (removing the #) and deleting 'domain-name-servers' from the request line 


I'll play around with this when I get a moment, but I dont use dhcp on this PC -- all the info is static, so I cant imagine why it would help.   That said, if it helps, more power to it.  I'll play with that idea.  --Thanks.

---

### Post by ubuntwinkel on 2006-12-04
Reposted as [new thread]("http://ubuntuforums.org/showthread.php?p=1862091#post1862091").

---

