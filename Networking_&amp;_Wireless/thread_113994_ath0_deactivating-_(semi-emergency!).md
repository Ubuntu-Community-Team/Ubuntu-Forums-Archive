---
title: "ath0 deactivating- (semi-emergency!)"
date: 2006-01-07
forum: Networking &amp; Wireless
---

### Post by iand675@gmail.com on 2006-01-07
I installed kubuntu on a computer and whenever I try to activate my linksys wmp54g card, it instantly deactivates again. I dont know what output to share, and normally I find that this card doesnt require ndiswrapper. What can I do to fix this?

---

### Post by Lambert on 2006-01-07
After trying to activate go to terminal and post output of these commands.

```
dmesg
```
```
cat /var/log/syslog
```

You can limit these to the last so many lines that look like they deal with your wireless.

Depending on the output I might come back and ask you to do it again but we'll turn debugging on to get a little more information.

---

