---
title: "Wireless/Wired connections not working"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by zerosktr1314 on 2009-01-25
I recently downloaded Ubuntu 8.10 and it won't connect to wireless and when wired it can't find a network address. I'm extremely new to Linux based systems so I don't even know the commands to check what cards are on my laptop etc.

---

### Post by Loosewheel on 2009-01-25
> **zerosktr1314 said:**
> I recently downloaded Ubuntu 8.10 and it won't connect to wireless and when wired it can't find a network address. I'm extremely new to Linux based systems so I don't even know the commands to check what cards are on my laptop etc.

There are some useful commands, and information here:
[https://help.ubuntu.com/8.10/internet/C/troubleshooting.html#troubleshooting-device](https://help.ubuntu.com/8.10/internet/C/troubleshooting.html#troubleshooting-device)

Kinda basic stuff you need to get started.

---

### Post by Iowan on 2009-01-26
One place to start - Open a terminal and enter: ```
ifconfig -a
``` This *should* show you if your interfaces are getting an IP address. (Only one will probably be active.)

---

