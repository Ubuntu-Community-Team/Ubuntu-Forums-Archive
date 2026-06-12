---
title: "Wireless suddenly stopped working after unplugging wired connection"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by ryankask on 2009-12-16
Greetings. I'm aware of the plethora of threads relating to problems running the Broadcom driver for Dell notebooks. However, my wireless has been working flawlessly since I installed Xubuntu on the notebook and all of the sudden yesterday, it stopped working.

I was running on a wired connection (eth0) all night and then went from my dorm to another building to use Wireless. All of the sudden I noticed my wireless was no longer working. The "Enable Wireless" checkbox in the NetworkManager Applet 0.7.996 was "greyed out" and it seemed like the driver was no longer working.

I am actively trying to remedy the problem using old posts, but given that my wireless was working fine yesterday (and all days prior), it seems to have something to do with just unplugging my wired connection without rebooting. Any suggestions? Any diagnostic information I can post to help troubleshoot this issue?

One final issue:

I ran the command "rfkill" and this is the ouput:

ryan@ryan-laptop:~$ rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

There is no button on my laptop so why does it say it is hard blocked? I try turn it off using "rfkill unblock all" but this doesn't help. 

Cheers,
Ryan

---

### Post by ryankask on 2009-12-16
Greetings,

I am an idiot and solved the issue. Last night I must have accidentally pressed a function key and the wireless on/off switch (F2). This explains the hard block being reported "yes" by "rfkill".

> ryan@ryan-laptop:~$ rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no


Doh!

Ryan

---

