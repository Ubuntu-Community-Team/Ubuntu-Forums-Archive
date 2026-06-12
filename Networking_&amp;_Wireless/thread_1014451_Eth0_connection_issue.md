---
title: "Eth0 connection issue"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by patrflanagan on 2008-12-17
I have a sort of strange networking issue.  I'm using ubuntu 8.10 and after a recent update my wired connection no longer seems to work.  Typing in ifconfig shows a functioning eth0, and pings to the router work fine.  However when I try to access any outside web page I get an unknown host error.  I assumed this must be a dns issue, but pinging just the ip of an outside connection also fails.  I tried to remove network manager and use wipc instead, but this didn't solve the problem.  Thanks for any help.

---

### Post by Iowan on 2008-12-17
Might also be a routing problem.  Check your configuration to verify your gateway address still points to your router. Beyond that, check/post results of **route**.

---

### Post by patrflanagan on 2008-12-17
For my default entry, the gateway still points to the router, but the entry for 192.168.0.1 just points to *.

Unfortunately its kinda impossible for my to just copy and paste the results of commands since I can't connect to the internet on my linux machine.

---

