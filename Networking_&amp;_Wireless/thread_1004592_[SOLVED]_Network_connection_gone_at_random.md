---
title: "[SOLVED] Network connection gone at random"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by Lixas on 2008-12-07
Hello ):P

Asus a6r, kUbuntu 8.04 (kernel 2.6.24-22)

I'm new in linux, but trying trying to deal with my linux problems :) maybe someone would be able to assist me?

I have a strange problem with my wired lan connection - it gones at random time after using computer for a while (few hours, sometimes about after 24 hours) and i can not even connect (ping) to my router. After log out / log in nothing changes, i have to restart my computer to use my network connection again

Tried to restart connection from console using sudo- it does not helps

---

### Post by jmoorse on 2008-12-07
A couple of things to try:

1. When the outtage occurs issue a `sudo dhclient (interface)`.  If this fixed the problem try moving to a static IP
2. Try a different switch port

If the problem still persists try issuing a dmesg command or referring to the logs.

---

### Post by Lixas on 2008-12-09
as far as i set static IP it does not gone. maybe to early to celebrate, but... didn't gone after i set static IP

Will report if something same problem occur again :cool:

---

