---
title: "dbus - kopete auto reply"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by ondrokm on 2010-08-15
Hi
I want to auto reply to all messages incoming to one of the accounts (also when I'm online). I think it may be done using dbus command that would be called be kopete every time a message come (Kopete - Setting - Notifications - Incoming message - Run command: *automsg.sh -"$account"*). In the automsg.sh script I would test $account string ( = kopete account) and optionally call dbus to send a message. 
A message could be send by:
```
qdbus org.kde.kopete /Kopete sendMessage "$contact" "auto message"
```
Don't you know how to obtain $account and $contact ( = contact id) from the incoming message?

---

