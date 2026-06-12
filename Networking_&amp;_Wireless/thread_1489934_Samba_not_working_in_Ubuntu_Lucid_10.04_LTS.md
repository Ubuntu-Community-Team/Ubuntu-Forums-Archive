---
title: "Samba not working in Ubuntu Lucid 10.04 LTS"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by Guilhermino on 2010-05-21
I've already read many posts regarding this problem, but until now none of the advice has worked.
The problem is I can't see the network shares of two wireless networked windows 7 pc's on my desktop running ubuntu 10.04.
When I try to open the windows network link on my ubuntu menu, it responds with a message stating it cannot retrieve the share list from server.
I can however perfectly ( even if slowly ) connect through the "connect to server:" link, even using the machine's name ( so name resolution seems to work ).
After many advice I saw in various forums that added nothing to my problem, I've finally tried to examine network traffic with the wireshark sniffer. All I've found is that my ubuntu box, when trying to retrieve the share list ( when I double-click windows network ), sends two packets searching for the master browser and a series of others searching for the group name, but never gets any answer.
can anybody help me ? I'd really prefer to browse the network than connecting directly to other pc's.
Thanks.

---

