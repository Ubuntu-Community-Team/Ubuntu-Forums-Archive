---
title: "how to allow DAAP in firestarter?"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by alexv305 on 2010-10-22
Firestarter has something weird going on lol

I allowed ports 3689 and 5353 for incoming and outgoing traffic in firestarter but my other machines wont detect a DAAP share. They do see them when I turn off firestarter. I'm even more confused when I see that I have a local connection using port 56690 when I turn off firestarter and monitor the log. It seems that DAAP is using 56690 but when I allow it for incoming/outgoing it still doesnt pick up my DAAP shares.

Is there a way I could fix this? I mean, I could run without a firewall but...idk if thats such a good idea :/

---

### Post by robegue on 2010-12-09
quoting from:
[http://embraceubuntu.com/2006/09/22/share-music-in-a-network-using-avahi-daap/#comment-8907](http://embraceubuntu.com/2006/09/22/share-music-in-a-network-using-avahi-daap/#comment-8907)

 I found this solution from a blog beacuse. Is a fix in the iptables. It cannot be done from the firestarter GUI, this because firestarter doesn’t suppport opening mDNS. You have to edit:
/etc/firestarter/user-pre

then add the following lines

$IPT -A INPUT -p udp –dport 5353 -d 224.0.0.251 -j ACCEPT
$IPT -A OUTPUT -p udp –dport 5353 -d 224.0.0.251 -j ACCEPT

---

