---
title: "OpenVPN for some traffic, but not all?"
date: 2011-03-01
forum: Networking &amp; Wireless
---

### Post by peternz on 2011-03-01
I have access to a VPN I use when having confidential instant messaging sessions. For the purposes of my work, essentially.

I'm a command line kind of guy, and like to use Finch (the shell version of Pidgin) for those.

However, when I turn on my OpenVPN connection it routes all traffic through the VPN. Web-browsing, IMing, and I can no longer access other machines on my home network.

Can I set OpenVPN to only route traffic I ask through that connection (either by port number or application, or some way I haven't thought of), while other traffic flows through my usual home network?

Some kind of local proxy perhaps? Or a dd-wrt box set up as a proxy, connected to OpenVPN?

I've played around with the GUI environment too (I have a basic GUI I sometimes use on my main machine) and have installed the full desktop 10.10 on a second machine just to see if I can work it out.

Sadly, I've been bested.

Does anyone have any ideas?

Thank you,

Peter

---

### Post by peternz on 2011-03-01
For the sake of the argument, let's say I need to send traffic on port 54321 to the VPN, but everything else I want to stay through my usual gateway.

---

### Post by peternz on 2011-03-02
Please ignore, I realised a VPN was really not the best option for what I was trying to achieve.

I'm happily using a proxy service for secure IM traffic now.

Thanks,

Peter

---

