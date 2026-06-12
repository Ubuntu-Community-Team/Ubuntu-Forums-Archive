---
title: "syslog errors chdir failed"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by burnleyhome on 2010-08-18
I have set up 10.04 as a file server/DHCP server with Samba. I used the Linux OS for the file permissions and gave full access to all the Samba shares. It works great (when I figured out UCL stuff). This replaced my Win2000 server which worked as file server/DHCP server. All clients are Windows XP (home and Pro).

I'm a total newbie with all my configuration taken from tutorials and forums.

My /var/log/syslog has some errors that I cannot solve (or find much info on).

Aug 18 14:35:47 srvex smbd[3274]: [2010/08/18 14:35:47,  0] smbd/service.c:191(set_current_service)
Aug 18 14:35:47 srvex smbd[3274]:   chdir (/home/shared/public) failed

I get this repeatidly with different shared directories mentioned but the rest is always the same. What do I need to do to get rid of them?

---

