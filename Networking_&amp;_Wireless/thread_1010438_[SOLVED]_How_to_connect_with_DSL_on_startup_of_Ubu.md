---
title: "[SOLVED] How to connect with DSL on startup of Ubuntu?"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by firethunderstorm on 2008-12-13
Hey guys,

I've a problem connecting to the internet via DSL modem.
I changed my internet provider and got a new modem, which supports direct connection on system-startup. This works fine under Windows XP, so I have a connection on startup without any dial-in via username and password (this means the modem does this).

I would like to have the same under Ubuntu 8.10.
Searching through the forums and help pages said "Network Manager" should do that automatically, but it doesn't and I also don't see the icon of it in the taskbar but it is already installed.

My question is: how can i configure my Ubuntu system to connect automatically on startup (like Windows does it) without directly connecting via PPPoE with username and password.

Thanks in advance for any help :)

---

### Post by firethunderstorm on 2008-12-15
Ok, I found someone who could help me.
I just had to change the following part in file [B]/etc/network/interfaces
[/B]
```
auto eth0
iface eth0 inet **manual**
```

into

```
auto eth0
iface eth0 inet **dhcp**
```

Now Ubuntu has internet connection on start-up.

Hope this helps you.

---

