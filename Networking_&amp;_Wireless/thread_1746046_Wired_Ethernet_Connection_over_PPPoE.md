---
title: "Wired Ethernet Connection over PPPoE"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by riteshs on 2011-05-01
[B] [FONT=Arial][SIZE=2][SIZE=2]I cant get my wired internet connection to work.
The command 'dpkg -s pppoeconf' returns ' installed ok installed'.

My  connection is through a router which is probably in a semi-bridge mode  and I need to dial a connection to get the net started.

[/SIZE][SIZE=2]The connection Auto eth0 is setup properly with the correct cloned MAC Address (that of my laptop).

I've  also executed 'sudo pppoeconf' and ran the whole series of steps which  towards the end said that my connection will be set on boot.
However, the net doesnt work directly and I dont know how to dial manually either. 

'sudo ifup eth0' returns 'interface eth0 already configured'.
I tried some 10-15 threads but none worked[/SIZE].[FONT=Arial][SIZE=2]Please help.[/SIZE][/FONT]Ubuntu is handicapped without internet.
Thanks in advance.[/SIZE][/FONT][/B]

---

### Post by dineshs on 2011-05-03
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)

---

### Post by riteshs on 2011-05-16
It worked! Thanks you SO very much!!:)

---

