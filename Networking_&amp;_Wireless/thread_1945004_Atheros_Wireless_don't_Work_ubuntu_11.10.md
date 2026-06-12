---
title: "Atheros Wireless don't Work ubuntu 11.10"
date: 2012-03-22
forum: Networking &amp; Wireless
---

### Post by brunounix on 2012-03-22
Hello everybody!

I have a problem with the Atheros wireless card was working perfectly until I installed the updates and then reboot. After that did not work anymore, someone tell me what could be?

[[COLOR="White"]midias sociais[/COLOR]]("http://www.brunodesouza.com")

---

### Post by cprofitt on 2012-03-22
Can you tell us what model Atheros it is?

You can do that by running the following command:

```
lscpi | grep Network
```

Your output should look like this, but with an Atheros wireless card not Intel:
```
~$ lspci | grep Network
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
```

---

