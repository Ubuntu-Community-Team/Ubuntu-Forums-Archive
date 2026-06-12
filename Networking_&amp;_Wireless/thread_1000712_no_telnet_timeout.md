---
title: "no telnet timeout"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by GoldWing on 2008-12-03
Hi,


I have some scripts that are doing a telnet to a machines port to check if that application is running.
However, even when the machine is down, the script stops after about 3 minutes.
When I execute the telnet command from another machine, I receive a time-out after 5 seconds.
Do I need to change a parameter somewhere ?
I don't think you can specify a timeout with a telnet command.


Thanks.

---

### Post by s3gfault on 2008-12-03
I would consider replacing telnet with a tool that is designed for the purpose you require.  nmap is such a program.

---

