---
title: "resolvconf not being smart"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by arsenix on 2009-04-30
I'm having an issue with resolvconf that I can't seem to figure out.  Basically what is happening is that resolvconf is putting the nameserver from my last wireless connection at the top of my resolv.conf file, even if I am not connected to wireless and even if I am connected to a hardline.  Obviously the desired behavior here is to put the eth* nameservers ahead of wireless cards... and if wireless is not up then don't put the wlan* nameservers in there.

Anyone else experience this?  Have any tips?  I have poked around on it and frankly I don't understand where it picks up the last wireless connection's nameserver.  If I bring down all the network connections and then run "resolvconf -u", it still puts the last active wireless connection's dns into resolv.conf!


James

---

### Post by arsenix on 2009-04-30
Predictably... after fooling around with it for a while and finally resigning myself to posting on here for tips... I fixed it five minutes later.  Somehow the act of posting always gives me the last bit of insight I need to fix an issue.  Here is the explanation for others who may encounter the same problem:

Techno description:
  The resolvconf script lists all files in /etc/resolvconf/run/interfaces for nameservers, in the order specified by the file /etc/resolvconf/interface-order.  The NetworkManager puts a file into /etc/resolvconf/run/interfaces called "NetworkManager" which has the nameservers for your currently active NM connections.  This file gets processed last because it does not match any of the lines in interface-order other than "*".  Somehow I had an "eth0" file in the interfaces directory which was not getting correctly updated... just sitting there stuffing my wlan (odd eh?) nameserver into my resolv.conf every time resolvconf update was run.

Cut to the chase description:
  If you are using NetworkManager to manage your network connections and nameservers/resolv.conf isn't behaving right, make sure that the only file in /etc/resolvconf/run/interfaces is "NetworkManager" and delete any other files.


James

---

### Post by t0mppa on 2009-04-30
> **arsenix said:**
> Predictably... after fooling around with it for a while and finally resigning myself to posting on here for tips... I fixed it five minutes later. Somehow the act of posting always gives me the last bit of insight I need to fix an issue.

Isn't that always the case? I've been wondering, if one could just begin with  asking for help when problems arise, just to cut the tedious "trying everything you can think of" phase out of the loop and just focus on solving the issue in the following 5 minutes after asking for help.

---

### Post by ThomasNovin on 2009-12-08
Doesn't work for me, I still have a 10 second delay connecting to any network because of resolvconf. I only have NetworkManager in /etc/resolvconf/run/interface after removing the file eth0.

---

