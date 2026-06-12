---
title: "Trouble with wireless connectivity NBR 9.10"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by cwscribner on 2010-03-15
Hi all,

I've been running the Ubuntu NBR 9.10 since it was released and I've noticed quite a few problems connecting to a wireless signal.  It's not uncommon for me to wait 5-10 minutes before my netbook finally establishes a connection.  Sometimes I have to manually try to reconnect several times before it finally connects.  Any help on this would be greatly appreciated!

Stats:
Asus Eee PC 1050HA
Ubuntu NBR 9.10

---

### Post by leorolla on 2010-03-15
I was having the same problem with ndiswrapper. Then I removed it and installed another driver, and problem is solved.

What driver are you using? (sudo lshw -C network)

---

