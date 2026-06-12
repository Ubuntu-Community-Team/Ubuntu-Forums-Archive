---
title: "Monitoring with Ubantu Sever 10.02"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by crackconfig on 2010-07-22
I have **Ubantu Sever 10.04** machine..I want to **monitor (filter)** my network internet users that uses windows7 and XP at the client side. Which utility i should use for this.. i **want to filter some websites and a log based** support too.

please do the needful and suggest the best.
thanks in advance

crackconfig!

---

### Post by varunendra on 2010-07-22
Hmmmm.....
4+ hrs. and still no 'best' suggestion for you. :lol:

Anyway, not the best, not even a satisfactory one but here is the 'first' one:

If you can dedicate a PC (at least intel pentium 1.2GHz processor, 1+ GB RAM) as a firewall, then '[Untangle Firewall]("http://www.untangle.com/Downloads/Download-ISO")' can do perhaps more than your expectation for free!
You can also install it on VMware (the host PC should be powerful enough to run host OS+Untangle VM).

If you are looking for a native solution then you may wish to learn about iptables:
[http://en.wikipedia.org/wiki/Iptables](http://en.wikipedia.org/wiki/Iptables)
([IPTables Tutorial]("http://www.frozentux.net/documents/iptables-tutorial/"))

(I personally have no idea about iptables yet, just heard somewhere it can do what you asked for)

Let's hope someone comes up with a better (if not the 'best' :D) and easy solution. However I'm serious about Untangle for the same cause (I've used Sonicwall before and Untangle is supposed to be almost equally efficient but free alternative).

---

### Post by crackconfig on 2010-07-23
Thanks for this reply buddy.
If **untangle firewall** as you said has all the filter implementation options..I 'll go for it ..
let's see what happens..

THANKS
crackconfig

---

### Post by varunendra on 2010-07-23
Pleasure is mine!:)
I'd like to know your practical experience with it since I've only read their 'short guides' & reviews so far, haven't practically implemented it yet.

---

### Post by 3ball on 2010-07-23
Another route you might take to do that is use openDNS as your name servers, if you're hosting DHCP on the Ubuntu server. You can then manage your filtering easily with their web interface from anywhere, and even monitor traffic requests.

1. choose an account type and create a login at [[COLOR="Blue"]https://www.opendns.com/start/[/COLOR]]("https://www.opendns.com/start/")
2. Log into your dashboard and create a network [[COLOR="blue"]here[/COLOR]]("https://www.opendns.com/dashboard/settings/"). 

If your ISP is dynamically assigning you an IP, use [[COLOR="blue"]this article[/COLOR]]("http://www.opendns.com/support/article/109") to set your network. If not, just specify the static IP of your network.

The OpenDNS nameservers are 208.67.222.222 and 208.67.220.220.

---

