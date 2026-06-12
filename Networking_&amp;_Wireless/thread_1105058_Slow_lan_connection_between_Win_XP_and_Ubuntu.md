---
title: "Slow lan connection between Win XP and Ubuntu"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by simonvlc on 2009-03-24
Hi all,

we have a problem with some win xp machines connected in lan through a switch to an ubuntu server.

The conf is this:

win1
win2 
centos_machine
ubuntu_server

We have one apache/mysql server installed on the ubuntu machine. When we try to load a page from it, it gives us good response times (about 800ms).

If we deploy an apache webserver in the centos machine, and make a connection to the mysql ubuntu server, all went fine, getting the same time approx.

The problem is that when we do the same with the windows machines, we got those times multiplied by 7-15 (5555-13000ms).

We have installed one ubuntu desktop above one of the windows machines that got higher response times, and when connecting ubuntu-ubuntu, we got 800ms times (so we discarded other hardware/wire/switch problems).

So the obvious bottleneck here is in windows... what can be happen here? Please, we desperately need some ideas.

Kind regards, Simon.

---

### Post by BkkBonanza on 2009-03-24
Do some detective work on the network level. Try using ping and traceroute to see whats happening there. Also look at mis-configured dns. Sometimes when dns is not right it will cause long timeouts. There is no inherent reason why XP and Linux should have very different response times. Also it;s not clear from your info just what you're measuring. Times from WinXP to Ubuntu for page load?

---

