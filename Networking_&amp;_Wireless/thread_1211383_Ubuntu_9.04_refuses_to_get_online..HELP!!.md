---
title: "Ubuntu 9.04 refuses to get online..HELP!!"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by carsonrose on 2009-07-12
I am EXTREMELY new to Linux... that being said, I am a very experienced windows user. I installed Ubuntu 9.04 on one of my dell Optiplex GX270 machines... works great. That is unless I want to use the internet... At my office, I have a network that I connect to, I entered the IP address manually, all went well. I bring this same machine home, no firewall, just plugged into a switch... and this thing REFUSES to get online....I have tried everything.. HELP!!?!?!?!

---

### Post by cariboo on 2009-07-12
Open an Applications-->Accessories-->Terminal and type:

```
dhclient eth0
```

This should get you a new ip address, and allow you to connect to the internet.

---

### Post by carsonrose on 2010-07-14
> **cariboo907 said:**
> Open an Applications-->Accessories-->Terminal and type:

```
dhclient eth0
```This should get you a new ip address, and allow you to connect to the internet.

thanks for the help!

---

### Post by Iowan on 2010-07-15
Wow - that's a little delay (almost necro ;) ). If you're still using Jaunty (I still have it on my laptop), there *should* be an option to "Connect automatically".

---

