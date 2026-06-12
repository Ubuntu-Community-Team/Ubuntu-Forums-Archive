---
title: "Intermittent access to Apache 2.2 server"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by dc200 on 2011-01-05
I've got Apache 2.2 running on a desktop within my LAN, and the other computers in that LAN can't see the server unless I ping them from the server first. When I do this, the other computers can browse the server without any problems.

If the client closes the connection (i.e. exits browser) and then tries reconnecting to the server after 5-10 minutes, the problem repeats itself. I have to ping them from the server again before they can connect to it.

Does anyone have any idea what could be causing this? I've got very little experience with HTTP servers, but it looks like an issue with UDP hole punching to me.

---

