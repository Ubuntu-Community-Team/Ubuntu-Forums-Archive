---
title: "Can't connect to internet..."
date: 2011-04-16
forum: Networking &amp; Wireless
---

### Post by Colour on 2011-04-16
Ohai thar,
So I just installed Ubuntu 10.10 on my PC and everything is working fine exept that I can't connect to internet at all :/
I mean nothing related to internet works exept that when I boot up Ubuntu a pop-up appears on the screen saying "Wired connection - You are now offline". I tried everything I could find on the internet like typing in the terminal "sudo pppoeconf", followed all the steps and still nothing. Help me :(

---

### Post by varunendra on 2011-04-16
Please provide some detailed info like:

[LIST]
[*]How are you trying to connect? (through cable to an adsl router/modem I guess)
[*]Is DHCP enabled on your modem/router, or you are assigning IP manually?
[*]Is your modem configured to connect permanently (pppoe) or do you have to supply an ID-password everytime you connect?
[*]Outputs of following commands:
[/LIST]
```
ifconfig -a
```
```
route -n
```

Plus any other details you think is important.

Also, have you made any configuration changes during following the guide you mentioned, or have you returned everything to their default values?

---

