---
title: "Run a command after acquiring a network address via DHCP"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by leachyboy2001 on 2009-09-21
Long story I want to run some kind of script that would essentially run at start up that would make my computer acquire an IP address THEN run a set command.

I'm terrible at writing scripts but if someone could think of a way to do this please share.  I can't seem to find any other posts relating to anything of this sort here or anywhere else.

---

### Post by kevdog on 2009-09-21
Something like this in a script perhaps:

sudo dhclient wlan0 && <command name or script file>

---

### Post by lswb on 2009-09-22
There is also provision built in to the dhcp client for automatically running scripts (as root) that may be useful to you. See "man dhclient-script" and look at the HOOKS section.

---

### Post by leachyboy2001 on 2009-09-22
Ahhhh, excellent that is why I ask my questions here, I probably would have never thought of that.

---

