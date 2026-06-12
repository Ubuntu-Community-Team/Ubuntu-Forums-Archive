---
title: "Remote Port Forwarding failed"
date: 2010-08-07
forum: Networking &amp; Wireless
---

### Post by ThiKa on 2010-08-07
When I use the following command:

ssh user@ssh_server -L 5500:localhost:5500 -p 22

everything works fine. I can log in, and local port forwarding is done.
Otherwise when I use the command:

ssh user@ssh_server -R 5500:localhost:5500 -p 22

I get an error "remote port forwarding failed for listen port 5500". However when I try remote port forwarding in WinXP by use of putty there is no problem...

Any idea? Thanks for answering

---

### Post by ThiKa on 2010-08-08
Choose Putty as ssh client. It must be a bug...

---

### Post by xmrazik on 2010-11-22
I can also confirm this issue. Remote port forwarding via Putty under Ubuntu also works. In contrast to SSH...

---

