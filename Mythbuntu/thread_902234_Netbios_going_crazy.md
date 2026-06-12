---
title: "Netbios going crazy"
date: 2008-08-27
forum: Mythbuntu
---

### Post by TheCook on 2008-08-27
Hi all,

I have been running Mythbuntu for a few months now but I have only just noticed that it is sending out a lot of traffic on my network directed at port 138(NETBIOS-DGM).  By a lot I mean two goes every 12 minutes.

Is this normal?  Where should I start looking?

Regards,
TheCook

---

### Post by anonymousdog on 2008-08-27
If you mean that two netbios datagram packets are sent every twelve minutes, then those are probably netbios announces.  If you've enabled Samba services, it'll do that; it's part of the process that allows the mythbox to appear in the Network Neighborhood/Places of Windows boxes.  You'll see very similar behavior from any Windows machine that shares files (most modern Windows desktop and server OSn) -- haven't compared, but I bet the Windows boxes are more chatty.  (BTW, I wouldn't consider ten packets an hour to be high traffic volume at all.)

---

### Post by TheCook on 2008-09-02
You're right it doesn't look like high volume traffic when you think packets per hour.  It just looked big when my firewall listed 20 odd pages of them (spose I should check the logs more often)

I had turned Samba off (at least I think I did).  I'll check again tonight.

Thanks

---

