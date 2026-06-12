---
title: "I sudddenly lost my internet connection on my old HP"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by oliverb4ss on 2009-04-21
I have a HP Compaq nc8000 with the Broadcom BCM5705M_2 Gigabit ethernet card.

This morning I turned on the computer and the network icon in the notification area has the little triangle with the "!" and it says that the network is disconnected.

I have a working connection from my router to all other computers in my house.

I initially moved to Ubuntu because the very same network adapter wouldn't work with XP, I tried all kinds of different drivers. In Ubuntu it worked right away, until now.

It's a fairly old machine, I suspect the hardware might be failing. How can I find the cause of this problem, whether it's hardware or software?

---

### Post by oliverb4ss on 2009-04-21
I also found a USB WiFi-dongle (Trendnet TEW-424UB), but when I plug that in, nothing happens, and I don't know if or how I manually mount or search for devices like that.

So, still no progress.

---

### Post by Iowan on 2009-04-21
Check the basics - **ifconfig -a**, **lshw -C network**... Does interface have an alias (eth0), and does it get an IP address? You might also **ping lo** - Can't say I'm familair with the process, but that's *supposed* to see networking is up.

---

### Post by oliverb4ss on 2009-04-22
Okay, for reasons I cannot fathom the connection is back up.

I guess problem solved then.

I'll soon be getting a new computer anyway, it's about time.

---

