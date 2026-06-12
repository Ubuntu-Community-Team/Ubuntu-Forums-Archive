---
title: "Port-forwarding on my linksys router works for everything except bittorrent."
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2009-06-06
I have a new Linksys/Cisco router WRT54G2 v.1 with the latest firmware installed. I currently use port forwarding for things like VNC and SSH into my home PC. However, every time I try to set a new rule (for both TCP and UDP) up for bittorrent, the bittorrent clients I try say the port is closed.  Both Transmission and Deluge will say the ports I select are closed, even if I change the port numbers and do another test. So I'm just wondering if anyone has encountered anything like this before and might have an idea of what could be causing this problem.  Also if port triggering (which I've never used before) might server as a potential work-around.

---

### Post by DGortze380 on 2009-06-07
> **diablo75 said:**
> I have a new Linksys/Cisco router WRT54G2 v.1 with the latest firmware installed. I currently use port forwarding for things like VNC and SSH into my home PC. However, every time I try to set a new rule (for both TCP and UDP) up for bittorrent, the bittorrent clients I try say the port is closed.  Both Transmission and Deluge will say the ports I select are closed, even if I change the port numbers and do another test. So I'm just wondering if anyone has encountered anything like this before and might have an idea of what could be causing this problem.  Also if port triggering (which I've never used before) might server as a potential work-around.

What OS?
What client are you using?
Do you have a hardware firewall?

You likely have to allow the traffic in your routers firewall, or host-based firewall.

---

### Post by diablo75 on 2009-06-07
> **DGortze380 said:**
> What OS?
What client are you using?
Do you have a hardware firewall?

You likely have to allow the traffic in your routers firewall, or host-based firewall.

Heh heh, I can't believe I overlooked my host firewall.  (I'm running 9.04 and the client I use most often is Transmission).  Anyway, I opened Firestarter up and found events hitting it that I had to make a rule for, and that fixed the problem.  I'm a real idiot!
:lolflag:

---

