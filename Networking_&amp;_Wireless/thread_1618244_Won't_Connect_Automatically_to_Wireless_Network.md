---
title: "Won't Connect Automatically to Wireless Network"
date: 2010-11-10
forum: Networking &amp; Wireless
---

### Post by onaridge on 2010-11-10
Each time I boot up my laptop, I have to manually connect to my wireless network. When I ran Ubuntu virtually from Windows 7, it found the connection automatically. Now I have a dual partition of W7 and Ubuntu and it won't auto connect. How can I make it so?

---

### Post by TBABill on 2010-11-10
What do you mean that it won't auto connect? Is it prompting you for the keyring password, then connecting? Or do you have to manually select your network in order to connect each time?

---

### Post by onaridge on 2010-11-10
I have to manually select each time.

---

### Post by uncaspi on 2010-11-10
Please post the content of /etc/network/interfaces

---

### Post by onaridge on 2010-11-10
auto lo
iface lo inet loopback

---

### Post by onaridge on 2010-11-11
Found the solution. 
Right click wireless icon, select edit connections, select wireless tab, edit connection, check "connect automatically".

I guess the default was not to connect automatically.

---

### Post by feedmeh8 on 2010-12-08
worked for me too! thanks.

---

### Post by onaridge on 2010-12-09
your welcome!

---

### Post by flyingmule on 2011-04-07
Doesn't work for me.

---

### Post by Ruination2 on 2012-06-23
> **flyingmule said:**
> Doesn't work for me.

I'm having the same problem, and my Connect Automatically box is checked.

That's not the problem.

---

### Post by lisati on 2012-06-23
Back to sleep, old thread. If the problem you're experiencing is slightly different, it's sometimes a good idea to start a new thread rather than resurrect an old thread that might be based on outdated information.

---

