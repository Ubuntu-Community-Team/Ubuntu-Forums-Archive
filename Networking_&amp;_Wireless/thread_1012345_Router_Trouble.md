---
title: "Router Trouble"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by JohnMori on 2008-12-15
As a Ubuntu newbie (like two days) I really need help. I purchased a Dell Mini 9 with Ubuntu.Works fine except that I am having problems with my router.

I am using a Linksys wrt54g router and have a Mac and a PC hardwired into it and a laptop PC running fine on wireless.

The problem is with the new Mini Dell and Ubuntu. After many hours of re-entering numbers I see that the router accepts only XP and VISTA.

My mini can see the network but the connection to the network will not go through.

Is the only answer to alas, buy the GL Linksys that accepts Linux? Or am I setting this up wrong?

Question two. Given this limitation will I have any problems taking the Mini on the road to hotels, and othe WiFi locations?

Thanks in advance for any help.

John

---

### Post by gTinker on 2008-12-16
[QUOTE=JohnMori]As a Ubuntu newbie (like two days) I really need help. I purchased a Dell Mini 9 with Ubuntu.Works fine except that I am having problems with my router.

I am using a Linksys wrt54g router and have a Mac and a PC hardwired into it and a laptop PC running fine on wireless.[/QUOTE]

OK, I'll take that as the router is working correctly and that you have correctly configured it for either static or dynamic IP addresses, whichever you use.


[QUOTE=JohnMori]
The problem is with the new Mini Dell and Ubuntu. After many hours of re-entering numbers I see that the router accepts only XP and VISTA.

My mini can see the network but the connection to the network will not go through.[/QUOTE]

Just mentioning, "will not go through", doesn't give us much to work with. Exactly what it is that you tried and any error messages you saw probably would give us more data to troubleshoot with.

How are you determining that the box can "see" the network? Does anything happen when you try to get an IP address from the routers DHCP server (if that's what you've configured). Say, something like sudo dhclient? Is your interface up, ifconfig -a?
[edit] If I assumed too much about your ability to run commands in a terminal, since I see you characterised yourself as a newbie, ask and someone will assist.


[QUOTE=JohnMori]
Is the only answer to alas, buy the GL Linksys that accepts Linux? Or am I setting this up wrong?[/quote]

Something is probably set wrong, probably something on the mini. 

I doubt you would have any different results with the GL model, the OS it's running is transparent to router operation. I do like that model because it's fairly easy to flash to a more full featured router with GNU/Linux software but that probably isn't something you need or want to spend time configuring.

[QUOTE=JohnMori]Question two. Given this limitation will I have any problems taking the Mini on the road to hotels, and othe WiFi locations?[/QUOTE]

I would think you might.

---

