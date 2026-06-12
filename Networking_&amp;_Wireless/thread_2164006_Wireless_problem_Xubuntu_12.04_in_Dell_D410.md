---
title: "Wireless problem Xubuntu 12.04 in Dell D410"
date: 2013-07-20
forum: Networking &amp; Wireless
---

### Post by natyxg on 2013-07-20
[SIZE=3][FONT=book antiqua][SIZE=3][FONT=arial narrow][FONT=arial]Hi. I'm a bit of a newbie so I really have no clue of how to fix my wireless problem. I looked around and didn't find anything that I thought could apply. So here it goes.

Recently I got a used Dell Latitude D410 from ebay, to use as a writing machine. I looked around and decided to use Xubuntu. I installed it and it works great, but it has a weird wifi problem. Basically, I have to boot the laptop twice for the wireless network to work. On the first boot it takes a while to get to the username/password page, and when I log on it says that there is no connection. When I check the connections, only the wired one is available (or would be available if the cable was connected), no sign of the wireless one. I tried these:[/FONT][/FONT]
[/SIZE]
[/FONT][/SIZE][FONT=arial][SIZE=3]rfkill unblock all 

[/SIZE][/FONT][SIZE=3][FONT=arial]  rfkill list all

But nothing happens, in fact, nothing turns up in the terminal. 

Anyway, if I reboot the laptop, it works fine. It boots up super fast and when I log in the wireless is connected, no problem (and the "rfkill list all command" works and shows that there are no soft or hard blocks on the wireless ). If I keep rebooting inmediatly after, the wireless keeps working fine, but if I shut it down for a while (more than 30 minutes, for example), the same thing happens all over again. 

I don't know if it matters, but I also get an error at every boot called "invalid environment block" and it asks me to press any key to continue. Since the laptop boots anyway I was gonna just leave it be, but now I wonder if it has anything to do with the wireless problem.

I've reinstalled Xubuntu 12.04 a couple of times, but the same thing happens. The only programs I've installed are wine and one that reads the system's temperature, I don't know if that matters.

I really have no clue how to fix this, but I'd like to because it's a little annoyance I could do without. 

Thanks. 
[/FONT][FONT=book antiqua]
[/FONT][/SIZE]

---

### Post by wildmanne39 on 2013-07-20
*Thread moved to **Networking & Wireless**.*

---

