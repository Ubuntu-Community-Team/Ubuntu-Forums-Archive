---
title: "Xbox Tunnel"
date: 2012-01-18
forum: Networking &amp; Wireless
---

### Post by cowfish on 2012-01-18
Alright so I have a routing dilemma here, I need to connect my xbox through some kind of tunnel to a VPS to get around an annoying DNS block. I know this works since I do it on my desktop, however the xbox is not capable of ssh on it's own, so it needs a little help. I have an old computer lying around with two ethernet cards, and so I set up a bit of a router, with the xbox plugged into it. This is the part I need help with. How can I set this up so that the traffic gets tunneled to my VPS, bypassing the DNS? The layout is something like this:

Xbox (192.168.2.120) -> RouterComp (192.168.1.125) -> Router (192.168.1.1) -> Internet -> VPS (xxx.xxx.xxx.xxx)

Is this even possible? It seems like there should be a way to do this, but I haven't found it yet. Interestingly enough, changing the DNS server on individual devices does nothing against the DNS block. The only way around it is to change the DNS servers set in the router (192.168.1.1). Not sure why but I guess I need a better understanding of how the block works. Anyway thanks for any help :D

---

### Post by syerges on 2012-01-18
If you figure it out, let me know as I have had to take alternative measures to connect to my xbox. If you can't find a solution you may want to do as I did and set up a Windows network on another computer for your xbox that you can still access with your other computers.

---

### Post by cowfish on 2012-01-18
I don't think setting up a separate network will solve this though since as long as 192.168.1.1 is in the equation (which it has to be to connect to the internet) the DNS block will be in effect. SSH seems to be enough to hide my traffic from the DNS block

---

### Post by cowfish on 2012-01-19
I can't believe I'm posting this, but I got it to work :D In case anyone else is trying to set up something similar to get past restrictions, here's what I did. I first set up an OpenVPN server on my VPS. Then, I used an old server as a router by connecting one ethernet port to the internet, and my xbox to the other. I then connected the server to my VPN as the interface tun0. The xbox was on eth1. I then used the script here to set up routing, with eth1 as my internal interface and tun0 as the external. Powered up the xbox and it connected to live, finally! Also, I changed the DNS servers in the xbox to google's. Not sure if that mattered or not, but I made sure that the restrictive router (192.168.1.1) was not known to the xbox at all, so I guess that's what did it.

---

