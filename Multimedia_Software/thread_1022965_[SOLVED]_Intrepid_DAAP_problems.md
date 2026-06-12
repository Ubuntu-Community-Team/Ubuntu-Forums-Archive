---
title: "[SOLVED] Intrepid DAAP problems"
date: 2008-12-27
forum: Multimedia Software
---

### Post by tsali on 2008-12-27
Situation:

I cannot access or share music via Rhythmbox from my laptop with Intrepid Ibex. The DAAP plugin is installed, checked and "enable sharing" checked.

I would like to access a DAAP share on my home server that's being served up by tangerine on debian.

I am able to access this share in Rhythmbox on my desktop running Hardy. iTunes users on other machines can find and access as well.

So that leaves something wrong with DAAP/Rhythmbox on my laptop.

I have tried to access the DAAP share directly via entering the host:port as follows - 192.168.1.100:3689

No connection can be established.

Where do I go from here?

---

### Post by tsali on 2008-12-28
Ok...figured it out.

Tangerine doesn't run as a service. It is running as an application in a user session. When I terminate the user session, the DAAP server stops as well.

So, for now, I'm leaving a user session running on the server. I don't like doing this and would prefer to find a way to run it as a service.

---

