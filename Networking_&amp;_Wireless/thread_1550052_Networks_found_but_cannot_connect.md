---
title: "Networks found but cannot connect"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by uncfan_2563 on 2010-08-10
Hi guys, I've been an Ubuntu user on x86 for a while and now I'm running it on PowerPc for the first time. I have a PowerBook G4 Titanium 15" 400 MHz that I bought an original AirPort card for. The wifi is supposed to work out of the box and I *do* see my wireless router show up. However, I cannot connect to it. I've tried unlocking the WEP and running it openly and that still doesn't work. I initially tried running Network-manager as is the default and later tried Wicd. Neither seemed to make a difference, I just can't connect. I'd really appreciate some help from you guys, the experts :)

edit: Running Ubuntu 10.04 LTS

---

### Post by Iowan on 2010-08-10
Keep in mind that I've never *touched* a PowerPC...
Check **sudo lshw -C network** for more information about your interface. I presume **ifconfig -a** shows nothing significant...

---

### Post by uncfan_2563 on 2010-08-10
And where is this information supposed to get me?

---

### Post by Iowan on 2010-08-10
It would be helpful if you could post it. The **lshw** info will show (among other things) what driver (if any) is being used. Those with more experience in drivers can use the information to (perhaps) suggest a different (or updated) driver.

---

