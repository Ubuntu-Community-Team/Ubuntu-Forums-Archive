---
title: "Mistery, sluggish Wireless network working fine in other OS and other networks"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by QuimNuss on 2010-09-25
Ok so the plot thickens,

Recently the wireless either works really slow or doesn't work at all. I can connect to the router, but at terrible downstream rate 200kb while on wired I get ~5Mb. One of the flatmates owns a Mac and he reaches 2Mb, which is poor too, but still...

So I'm not sure where the problem comes from, because, mistery mistery, I found another wireless network which was open, so sick of mine, I tried the other one, and it worked smooth as usual.

So, I am now unsure on who to blame... The internet connection works fine, since the wired network works. The Wireless may work fine, since it works in other OS. Ubuntu's network works fine, since it worked on another wireless network.

It's the specific combination of my computer with our wireless network that messes it up.

I've tried disabling IPv6, changing the wireless channel -I usually get full strengh signal, the behaviour is the same whether I'm near the router or not-, changing the browser, switching to wicd, restoring the router to its factory defaults ...

Nothing seems to solve it. The only thing missing is trying to find new firmware, but I couldn't find the way to backup what I already have and I don't want to trash the router for everyone in the flat.

Another piece of evidence, when I connect to the router through http, sometimes I get the message 400 Bad Request.

Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

Router: Comtrend CT 5361
Line Rate - Upstream (Kbps):     639
Line Rate - Downstream (Kbps):     6045
Software Version:     A101-220TLF-C44
Bootloader (CFE) Version:     1.0.37-0.7

Using Ubuntu 10.04

Any other information that would be useful, please ask.

Thanks to all Sherlocks here!

---

### Post by 73ckn797 on 2010-09-25
I have had similar issues with wireless using a TrendNet wireless card. The connection was weak and sometimes would not connect, even with the desktop computer within 10 feet of the wireless router. I installed "ndisgtk" from the repository and then installed the Windows XP driver from the disk that came with the wireless card. I do not see whether you are using a laptop or desktop computer. If a laptop you may need to find the driver for the card and install through the ndisgtk program. It is a graphical program.

Give it a try.

---

### Post by QuimNuss on 2010-09-25
Humm... I'll try to find the installation CD, it's been years now, I'm not sure they left any.

---

### Post by QuimNuss on 2010-09-25
Ah, btw, I don't get a weak signal, its -34 dbm, which scores like 100% or something, it's gonna be something else?

Anyway, why was it working in the first place?

I'll try your solution though...

---

