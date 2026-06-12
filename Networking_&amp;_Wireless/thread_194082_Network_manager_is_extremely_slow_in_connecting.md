---
title: "Network manager is extremely slow in connecting"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by stalefries on 2006-06-10
using the standard network connection applet, I am connected to a network as soon as I log in. Using Network Manager, it takes FOREVER for it to connect to a network, and it constantly tries to connect to a network with a significantly weaker strength. Is there anything I'm doing wrong? WOuld using ndiswrapper help at all? The default drivers installed work just fine (I haven't tried any WEP or WPA, no need). I'd like to have Network Manager for the simplicity it provides.

---

### Post by Vinze on 2006-06-11
I think this is because NetworkManager starts connecting when logged in, whereas the default network connection thingy will connect during boot. I might be wrong, but if I'm right, I hope they'll work on it.

---

### Post by stalefries on 2006-06-11
No, they're both loaded at login. I'm sure of that. But why would NM take so long? In fact, I don't think it actually ever connected to a network properly, before I finally gave up and killed the nm-applet process.

---

### Post by stalefries on 2006-06-18
I really hate to just bump this, but I'de really like to be able to use Network Manager instead. It seems so much easier to use, but if I can't get it to work, I'm stuck.

---

