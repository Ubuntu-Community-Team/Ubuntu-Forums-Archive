---
title: "Help!! I can't access my router!"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by Nailox on 2010-01-24
the router is TP-Link TL-WR340G. When I got it I entered the menu and configured everything without problems. Some time ago I had to reinstall ubuntu and after that I couldn't access the router. I tried to reset it, i tried switching the wifi on and off. I connect the router and the pc with the network cable, i type 192.168.1.1 in firefox and it says: can't access site. I plug the internet cable in the modem - its the same and I dont have internet at all. Can you please help me fix it TYIA !

---

### Post by chewearn on 2010-01-24
You might have to force hard reset of the router.  Find out how from it's use manual, and what its default IP address after reset.  Though, this would mean you loose all settings in the router.

Normally, hard reset a router involved using a paperclip to push and hold the reset button, then plug the power supply and wait for at least 30 seconds before releasing the reset.

---

### Post by blackened on 2010-01-24
Hard reset instructions for your router are here: [http://www.tp-link.com/support/showfaq.asp?id=83]("http://www.tp-link.com/support/showfaq.asp?id=83")

---

### Post by Nailox on 2010-01-24
yes I followed those instructions and I did the hard reset - still no luck. When I connect the network cable from the router to the PC it starts to connect and in the end it says: "wired network disconnected" What am I doing wrong?

---

### Post by chewearn on 2010-01-24
I suspect DHCP is not working and you are not getting an IP.  Try setting a static IP instead.

---

### Post by jk007 on 2010-01-24
Yes, try with fixed IP and check Speed/Duplex, might be Autonegotiation problem, too.

---

### Post by Iowan on 2010-01-24
**ifconfig -a** shows a valid address? Can you ping the router?

---

### Post by thundertortoise on 2011-02-09
I'm experiencing the EXACT same issue as the one described above. I know it's been a while but was hoping someone could help me. I'm a new Ubuntu user.

I need to use software that requires certain ports to be open. It's Windows only so I'm running the program inside of VirtualBox. I called my ISP (COX) and they said it's because my computer isn't set up to use dynamic IP. Then basically said they couldn't do anything for me because I was running Linux (what a cop-out!).

It's the same as the first poster, I can access the router just fine. Plug an ethernet into the router from my comp. and get a connection. But cannot plug directly into the modem.

Very frustrating. I'd REALLY appreciate any help! A really cool job hangs on the line if I get this to work (:

---

