---
title: "What's the deal with 3G?"
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by isecore on 2010-08-21
I've been trying to setup a Huawei 3G data-dongle with my Ubuntu laptop, and have been having a lot of funky issues.

With 9.10 and previous it just worked. You popped it in, answered some very brief questions and put in the pin and presto. Now with 10.04, nothing happens. It finds the built-in memory reader, but not the modem itself it seems.

Did some googling and it suggested I install usb-modeswitch and the accompanying packages. Did that, and then it works. Sort of. You have to tickle it a lot, restarting network-manager, generally doing some weird sort of rain-dance with the computer and suddenly for no logical reason the connection appears in Network Manager and you can connect. And then it works, but since I'm not the primary user of this laptop (it's being borrowed to a non-technical friend) I can't be around all the time to hold the machines hands until it figures out what's going on. Because after you disconnect, put the machine in standby or reboot it, then it goes back to not recognizing anything.

Seemingly I can't get a straight answer either. Why was it so amazingly simple and nice back in 9.10 and what changed? And how do I make it simple again.

---

