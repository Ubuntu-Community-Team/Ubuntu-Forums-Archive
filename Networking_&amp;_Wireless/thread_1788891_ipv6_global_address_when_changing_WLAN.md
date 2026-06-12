---
title: "ipv6 global address when changing WLAN"
date: 2011-06-23
forum: Networking &amp; Wireless
---

### Post by idef1x on 2011-06-23
I've two WLAN AP's with both a different IPv6 subnet. When I change from one AP to the other, my IPv6 Global address stays valid and so is the default IPv6 gateway. After a while I get another Global address from the second AP's subnet and another default IPv6 gateway for the second subnet. Both have the same metric. IPv6 connectivity is broken now. When I disable wireless on the laptop and reenable it, it flushes all IP addresses and receives new ones and connectivity is restored.
Does anyone know if this is normal behaviour or should it normaly flush all the addresses when changing network?
It's a bit silly to have to disable/enable wireless all the time..

---

### Post by poolet on 2011-06-23
It's a kind of weird that you said, but let me ask you something, do you have enable the QoS or any IP filtering, like firewall even a simple fake table can block your tunel and break it down... Also make sure that your running NAT-T and not NAT!! Check the following link maybe helps you!! 

[http://ipv6.com/articles/general/ipv6-the-next-generation-internet.htm]("http://ipv6.com/articles/general/ipv6-the-next-generation-internet.htm")

[http://en.wikipedia.org/wiki/IPv6]("http://en.wikipedia.org/wiki/IPv6")

it's all about IPv6 
Hope that I help you!!

---

### Post by idef1x on 2011-06-24
Hello Poolet,
Thanks for responding. I don't make use of tunnels on the laptop that is changing WLAN Acces Point.
If I am on AP1 IPv6 is a native connection and is routed via a Fritzbox router. Everything works just fine. If I use my second AP from the start, IPv6 is routed via an Ubuntu router, which has a 6-to-4 tunnel to Sixxs.net. Everything works just fine. Connectivity problems arise when I am on one AP and switch to the other. Order doesn't matter. First it takes awhile before the latop gets an IPv6 global address in the second AP's subnet and an EXTRA default route to the correct newly connected network, but still no functioning connectivity. Then after a while the default route of the first network times out and gets status FAILED. Still no connectivity though. After long waiting finally the ipv6 connectivity is restored. I can't find out yet which timer is running out to get connectivity back. 
Maybe the question would be better to ask, why switching works for ipv4 flawlessly, but not for ipv6? Or would it be a bug the way it works on my laptop? I don't know :(

---

### Post by idef1x on 2011-06-25
Hmm the problem seemed to be the KDE network-manager. Under Ubuntu it works flawlessy, so i changed to wicd and that solved it for me. Wicd shows in its configuration that it will flush the ip routes, which i think was the whole issue in the first place...

---

### Post by poolet on 2011-06-25
I need to be admit that it was a weird problem, since from your second AP, IPv6 routed fine... If you had a problem to your AP am 100% sure that the problem has to be at metric or something with the configuration at 6-to-4 tunnel...  Glad that you solved it!!!

---

