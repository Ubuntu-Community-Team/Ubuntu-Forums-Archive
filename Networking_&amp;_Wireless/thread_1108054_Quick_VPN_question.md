---
title: "Quick VPN question"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by rshnike on 2009-03-27
I have an Intrepid running a [SAGE]("http://www.sagemath.org/") server on my LAN that I'd like to access from work, which I gathered meant that it was time to reopen some material on setting up a VPN.

I haven't really gotten that far into it yet though I assume that ultimately I'm going to need PPTP, so for that it seems like there's a ton of info scattered all around about how to do it.

I was just wondering simply on the hardware side, do I want to set up a new separate box running I guess 8.04 server and have it in front of my router? Or behind my router and forward some ports to it? (Or should I go with no separate box and use the openvpn that ships with DD-WRT?)

I'm a bit paranoid about security, and a lot of the material on the forums about setting up a VPN doesn't mention what type of security measures to take.

Thanks a lot.

---

### Post by coutts99 on 2009-03-27
Can you run openvpn on the box you want to get to itself, and just forward a port to it?

Openvpn only requires one port to be forwarded, normally 1194.

This is how my set-up at home works.

---

### Post by rshnike on 2009-03-27
Is it really that simple then? Yeah I can forward the port to this box. Thanks I'll try that. Did you have to do much configuration for openvpn or did you just follow the instructions on the site?

---

### Post by coutts99 on 2009-03-27
> **rshnike said:**
> Is it really that simple then? Yeah I can forward the port to this box. Thanks I'll try that. Did you have to do much configuration for openvpn or did you just follow the instructions on the site?

Just follow the site, openvpn is very easy to setup :)

---

### Post by rshnike on 2009-03-27
Great. Off I go. Thanks!

---

