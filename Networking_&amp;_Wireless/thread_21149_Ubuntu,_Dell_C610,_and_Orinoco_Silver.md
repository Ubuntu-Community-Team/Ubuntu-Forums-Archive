---
title: "Ubuntu, Dell C610, and Orinoco Silver"
date: 2005-03-20
forum: Networking &amp; Wireless
---

### Post by USSJoin on 2005-03-20
Hello there! I have a series of Dell C610s, all of which need to be networked together. I'm running Ubuntu Linux Warty.
These laptops do not have any built-in modem or ethernet. I have Orinoco Silver cards that I want to use.
When I put them in at bootup, they are usually detected and can be found in the lsmod with their modules detected. However, iwconfig and ifconfig don't see any trace of the cards, and they do not light up. If they aren't detected at bootup, a modprobe orinoco will bring them to this state as well.
These are PCMCIA cards, of course, and when I insert and remove them, I don't see any acknowledgement of the fact at all-- the PCMCIA FAQ/troubleshooting was unhelpful for this, as none of the symptom-sets really seemed to apply.
If anyone has a clue about what to do about this, I would be most grateful; I've tried everything I can think of.
If you need any files posted, tell me and I'll get them up.
Thanks so much.

---

