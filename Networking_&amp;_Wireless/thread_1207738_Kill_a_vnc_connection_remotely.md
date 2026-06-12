---
title: "Kill a vnc connection remotely"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by eserikto on 2009-07-08
I have xvnc running on an ubuntu computer at home. I tend to vnc in from a windows machine that I have at home. Sometimes I'll forget to close vnc at home and won't be able to access the same xvnc session remotely because it's already in use.

So, I want to be able to kill the connection without restarting xvnc. I only have remote access to the ubuntu machine. Anyway, googling around pointed me at tcpkill. I have xvnc listening to port 5902.

sudo tcpkill -9 port 5902

*sometimes* works. Other times it won't kill the connection between my home windows machine and my server. It will however prevent any new attempts from even trying to access my xvnc, so I know the tcpkill is working.

Today is one of the days where I can't get tcpkill to kill the connection. Any ideas?

---

