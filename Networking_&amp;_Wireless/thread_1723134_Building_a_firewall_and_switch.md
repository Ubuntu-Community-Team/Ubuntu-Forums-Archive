---
title: "Building a firewall and switch"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by perrti-y02 on 2011-04-06
Hello,
I am wanting to build myself a Linux based firewall and network switch but I am not entirely sure where to start. I would like to point out that I am aware that it would be easier and quicker to just buy a switch and use that, but this is an intellectual exercise.

What I want to do is have a NIC which has the internet coming in. The traffic is then passed through the firewall program (I think IP tables is what I should be using?).

Now my main issue is that I will have quite a few Network Interfaces to manage. The machine could easily assign IPs by DHCP and act as the DNS server but what would I need to use to share the internet connection to all the NICs? There will be at least 4 interfaces, but possibly up to 12.

Any help would be much appreciated.

Tim

---

### Post by decoherence on 2011-04-06
> what would I need to use to share the internet connection to all the NICs?

You can use iptables for this as well. It's a matter of setting up the routing.

Unfortunately I'm not expert with iptables so I can't give you the particulars. Good luck in finding your answer -- there should be plenty of docs for this online.

---

### Post by nosebreaker on 2011-04-06
Oh boy, this is going to be a pain to do!

I believe what you want is called a bridge.  I'd try installing bridge-utils and ebtables, and use brctl to control the bridge.  Honestly I don't know how to get it to transparently pass traffic across multiple interfaces like that though.  I know people have done this to place a system in-line with an outgoing network, but I've never heard of anyone replicating a switch, just spend the $20 on one!

---

