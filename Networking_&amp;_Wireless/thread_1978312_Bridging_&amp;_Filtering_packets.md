---
title: "Bridging &amp; Filtering packets"
date: 2012-05-11
forum: Networking &amp; Wireless
---

### Post by la_mer222 on 2012-05-11
Hi all,

I'm sorry, I'm sure this question (or similar to) has been answered before. I Did perform some searches on this forum and found nothing that was 100% for me.

What I'd like to do is setup a linux bridge between my core router and my content filter that will inspect packets (and/or capture them if the option is available) and also be able to drop all packets going to specific IP addresses, etc... So basically, I'd like the setup to look something like:

Core couter ---> linux bridge (inspect/capture/drop packets here) ---> content filter ---> firewall ---> WAN to the internet. The 

The reasoning behind that setup is I'd like to prevent my content filter from siphoning through information that it doesn't need to care about. I'd rather have the bridge that sits before it work out that junk. I hope that makes sense.

I understand (I think) the idea behind bridge-utils and using the brctl tool, as there are a lot of sites and documentation on the two. The piece I'm missing is, do I use iptables to inspect/drop packets, and if so, can someone provide an example of how that is supposed to work? Or is this something not really doable with the config above?

Sorry if this is a 'noob' question, I'd just like to see if I can do this.
Thanks for any advice or pointers.

---

### Post by bab1 on 2012-05-11
> **la_mer222 said:**
> Hi all,

I'm sorry, I'm sure this question (or similar to) has been answered before. I Did perform some searches on this forum and found nothing that was 100% for me.

What I'd like to do is setup a linux bridge between my core router and my content filter that will inspect packets (and/or capture them if the option is available) and also be able to drop all packets going to specific IP addresses, etc... So basically, I'd like the setup to look something like:

Core couter ---> linux bridge (inspect/capture/drop packets here) ---> content filter ---> firewall ---> WAN to the internet. The 

The reasoning behind that setup is I'd like to prevent my content filter from siphoning through information that it doesn't need to care about. I'd rather have the bridge that sits before it work out that junk. I hope that makes sense.

I understand (I think) the idea behind bridge-utils and using the brctl tool, as there are a lot of sites and documentation on the two. The piece I'm missing is, do I use iptables to inspect/drop packets, and if so, can someone provide an example of how that is supposed to work? Or is this something not really doable with the config above?

Sorry if this is a 'noob' question, I'd just like to see if I can do this.
Thanks for any advice or pointers.

Bridge-utils are used to connect hosts on separate subnets (i.e. 192.168.0.0/24 to 10.0.0.0/24) via layer 2 (frames) rather than at layer 3 (packets).  To filter by packets you can just use IPtables.

Another way to think of it is: layer 2 is local (one subnet) and layer 3 is routed (internetworks).

---

