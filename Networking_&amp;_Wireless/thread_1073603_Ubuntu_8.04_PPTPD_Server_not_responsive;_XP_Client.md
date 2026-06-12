---
title: "Ubuntu 8.04: PPTPD Server not responsive; XP Client timing out"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by Jac3510 on 2009-02-18
Hey guys - handy recommended I move this thread here, so here we go:

----------------------------------------------------------------

My PPTPD server is not connecting. I have a 2wire 2701 HG-B which is set to DMZ mode (meaning ALL ports are forwarded to this machine). PPTPD is updated and installed. The /etc/pptpd.conf has the proper local and remote IPs, and the /etc/ppp/chap-secrets has the correct user accounts set up. I totally deleted the firewall (apparmor). In other words, my public IP goes directly into the computer (how's that for security! :p)

That said, I am on windows XP and create a VPN connection like I've done a million times before. I tried both the public IP address and my (updated) dyndns address. When I click "connect," absolutely nothing happens. I run tail -f /var/log/messages and tail -f /var/log/syslog, and here's the crazy part . . . as far as my linux box is concerned, NOTHING is coming into the computer at all. Any surprise my VNC connection just times out on attempt?

Two more symptoms: I have another ubuntu machine on the same network, behind the same router, using the same setup (only with 8.10 rather than this, 8.04). I set it to DMZ, it connects immediately. Just the 8.04 machine won't connect. And lastly, I did have the 8.04 working at one point for a few minutes, but when I changed my second machine over to DMZ to test it (and it worked), it stopped working on .04, even though I changed it back to DMZ.

Obviously, I need a more secure way to set up the PPTP server. I can handle that later. Right now, I just need to why NOTHING is happening.

Help?

-----------------------------------------------------------------

And . . .

-----------------------------------------------------------------

Thanks, handy. I think I have decided the 2wire is bad. After extensive googling, I found this is a pretty common problem. The reason it is not connecting is because it is listed as inactive on the network, even though I am perfectly capable of serving the net. In fact, now, it isn't just my 8.04 machine that is inactive (the one set to DMZ), but ALSO my maximum protection 8.10 machine, which I've never had a problem with. I took a break from the problem, came back an hour later, and now this one (which I'm on now) won't register, either.

Unless you guys have a better suggesting, I'm getting a Westell instead. This thing has been giving me problems from day one. A month of this sporadic behavior has been more than enough for me.

-----------------------------------------------------------------

Thoughts?

---

