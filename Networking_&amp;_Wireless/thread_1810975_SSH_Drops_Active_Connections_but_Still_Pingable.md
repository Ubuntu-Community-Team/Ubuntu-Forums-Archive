---
title: "SSH Drops Active Connections but Still Pingable"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by StatsJunkie on 2011-07-24
I have a very frustrating problem with a new server I built.

On every machine that SSHes in, the connection gets dropped randomly between immediately, and 30 minutes into the session, while the user is actively using the remote system (typing, etc). Before, during and after the disconnection, the system responds to pings regularly (0% packet loss).

It takes about 5-10 minutes before I can make an SSH connection again.

I have tried restarting SSH on the server and rebooting the server. I even removed and reinstalled sshd and it is still happening.

What might be causing these random disconnects and how might I solve this?

---

### Post by HermanAB on 2011-07-24
Howdy,

In my experience, SSH problems are usually due to a bad (older) router somewhere in the system that messes up TCP when some internal table gets full. Ping is not a good indicator of these problems, since it is ICMP.

---

