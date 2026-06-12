---
title: "ping has no reply"
date: 2012-10-09
forum: Networking &amp; Wireless
---

### Post by norima on 2012-10-09
Hi guys,
I wonder if someone had experienced the same problem as i do right now with kubuntu 11.10... Actually, I'm not sure where to blame the issue if it's kubuntu or to my connection stuff and all.

Our office is connected with LAN connection setup and there's an intranet website run from Windows 2008 server. All kubuntu clients will access to this website (intranet).  Ok here's the problem two of the kubuntu computers accessing the website will eventually lost their connection to the server.  When I try to ping from these computers that can't access to the server, ping has no reply, I mean just nothing, nothing says destination is unreachable or anything but when i ping to other computers except the server ping is fine.

I'm confuse why it eventually lost its connection to the server?  At first I suspected the cable but i can ping to other computers but not to the server only.  Then I suspected that it's probably due to windows firewall, disabling the firewall neither help.

Any ideas?

---

### Post by norima on 2012-10-09
Oops! my stupid.. figured, the 2 computers used the same ip address that causes them to collide.  But i'm wondering why there's no notification in kubuntu 11.10 about duplicate ip address? anyway the problem is solved.

---

