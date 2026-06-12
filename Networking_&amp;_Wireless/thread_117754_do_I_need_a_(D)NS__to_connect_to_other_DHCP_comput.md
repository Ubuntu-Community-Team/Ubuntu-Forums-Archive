---
title: "do I need a (D?)NS  to connect to other DHCP computers?"
date: 2006-01-15
forum: Networking &amp; Wireless
---

### Post by dieselpower on 2006-01-15
Hello, 
I have several questions about my DHCP server.

1:   I just installed dhcp3-server on my router and need to be able to connect to other computers on the lan somehow. I.E. "fish://lawrence-laptop" instead of "fish://192.168.0.I-dont-know". Do I need to install a nameserver in order to do this? If not how do I do it?

2:   In the network module in Kcontrol in kde there is a field for domain name. I am assuming that it should be some made-up name, and be identical on all computers. I have seen examples that end with .com or .org, but that seems wrong to me. What should I do there?

3:   If I set Domain Name to shafers.com can I just "ping lawrence-laptop.shafers.com?

4:   I noticed that /var/lib/dhcp3/dhcpd.leases only reports client-hostnames for the windows and Gentoo computers. Why is ubuntu not reporting hostnames?

Any help on any of these problems would be appreciated.

Lawrence

---

### Post by cwaldbieser on 2006-01-15
[QUOTE=dieselpower]Hello, 
I have several questions about my DHCP server.

1:   I just installed dhcp3-server on my router and need to be able to connect to other computers on the lan somehow. I.E. "fish://lawrence-laptop" instead of "fish://192.168.0.I-dont-know". Do I need to install a nameserver in order to do this? If not how do I do it?
Lawrence[/QUOTE]
The easiest way to configure this for a small home network is to probably just use static IP addresses and enter the hostnames into the /etc/hosts file on each PC.

If your network is large enough to make that unmaintainable, then you need a DNS server.

---

### Post by dieselpower on 2006-01-15
My network is small, only 17 PCs at the most (including my Zaurus and Basic Stamp Projects). But I want to do this just for the fun of learning. So I guess I'll see if I can figure out how to install a DNS server. If anyone has suggestions, I'm listening.

---

### Post by mgor on 2006-01-15
i found a pretty good guide[1]. check it out, especially "DHCPD setup" and "BIND setup".

if you're not intrested in allowing DHCPD updating your DNS records according to the leases djbdns[2] is a good and secure alternative.

[1] [http://www.stanford.edu/~fenn/linux/](http://www.stanford.edu/~fenn/linux/)
[2] [http://freshmeat.net/redir/dnscache/1955/url_homepage/djbdns.html](http://freshmeat.net/redir/dnscache/1955/url_homepage/djbdns.html)

---

### Post by Mr_Grieves on 2006-01-15
It's not just to install the software.. if you did not know.

Don't forget that you probably need
1) A public static IP adress for you DNS server.
2) A valid domain that points on your DNS server.

I guess an alternative solution would be using the computers host files..

---

### Post by dieselpower on 2006-01-15
[QUOTE=Mr_Grieves]It's not just to install the software.. if you did not know.

Don't forget that you probably need
1) A public static IP adress for you DNS server.
2) A valid domain that points on your DNS server.

I guess an alternative solution would be using the computers host files..[/QUOTE]

Yes I know, and how I wish it was different! I want to learn bind9 but dnsmasq looks so nice! I don't know what I'll end up using yet. I have a dynamic IP because I'm on dialup, but I do have a dynamically assigned domain name so I think it should still work. I  have apache set up and am serving a website off it so I know the domain name works [http://www.the-inventor.homelinux.com]("http://www.the-inventor.homelinux.com")
So I guess its off to more head banging and config editing and screwing so I have to use links2 to search google to...  :D :D :D 

Lawrence

---

### Post by mgor on 2006-01-16
[QUOTE=Mr_Grieves]It's not just to install the software.. if you did not know.

Don't forget that you probably need
1) A public static IP adress for you DNS server.
2) A valid domain that points on your DNS server.

I guess an alternative solution would be using the computers host files..[/QUOTE]

if his only going to run a local DNS there's no such need.

i've got hgttg.local running locally and i access the computers via host.hgttg.local.

in other words, i've got no public static ip adress nor a "valid" (public) domain.

---

