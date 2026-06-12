---
title: "Preventing NetworkManager from managing certain interfaces"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by jemenake on 2010-01-29
I've got a laptop which I use two wireless adapters with. With one of them, I'd like NetworkManager to manage and automatically connect me to wireless networks when they're available. The other, I want NetworkManager to leave alone, letting me hack on it with iwconfig and whatnot.

I've googled, but I can't figure out how to get NetworkManager to leave the second interface alone. The pages I've read say that all you need to do is mention the interface in /etc/network/interfaces, but I've done that, and NetworkManager still takes over management of it. Maybe the directives I'm using (like "auto wlan1") in the interfaces file are ones that NetworkManager ignores.

Any ideas?

---

### Post by Iowan on 2010-01-30
Hmmm, I'd have suggested defining it in */etc/network/interfaces*... If you configured it for "auto", it will still activate (probably before the NM-controlled one).

---

