---
title: "Asus UL30 wireless/internet issues 10.10"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by russx2 on 2010-10-11
Hi guys,

I have a fresh install of Maverick final. Wireless *seems* fine (can search networks, connect OK, etc.) but after a few minutes any network activity ceases to function. I can't ping etc. Reconnecting to the wireless network fixes it but, again, only for a few minutes.

Any ideas? I'm guessing this is some kind of power saving bug? Or...? It's very odd. Everything's 100% fine and stable in 10.04 (wireless wise).

I *believe* my specific model (Asus UL30a) ships with an Atheros 9285 (AzureWave rebranded) card.

Thanks.

Russ

---

### Post by karl3 on 2010-10-13
i have the same problem on asus ul30vt.

---

### Post by theburningor on 2010-10-13
Odd. I have an ASUS UL30A which was running fine under Lucid and seems to be doing fine with the wireless after upgrading.  I wonder what was different.

---

### Post by nakunaru on 2011-03-11
I have been having the same issues, I couldn't access any of my network shares until 10.10 but now it will but up for a bit and then go down causing me to have to reset my connection. I have an Asus K60I but it also does the same thing on my desktop.

---

### Post by theburningor on 2011-03-15
There was a related issue on here [Unresponsive menu items in network manager applet]("http://ubuntuforums.org/showthread.php?t=1679776")
 which turned out to be caused by a memory leak in the nm-applet in the nautilus-elementary repository.  Might want to go into system monitor and look and see if nm-applet is having issues. Specially, look at the memory usage for the nm-applet process.  My machine is running at 6.6mb right now and I'd take anything over 10 as a sign of trouble.

---

