---
title: "Network Adaptor problem following 10.10 beta update"
date: 2010-09-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Zoea on 2010-09-23
Hi there

I'll try and keep this simple

[B]My Hardware:
[/B]Intel i5 750 CPU
Gigabyte P55M-UD4 Motherboard (P55, F11 bios)
4GB DDR3
160GB SATA1 Hard Drive (AHCI was disabled to allow boot)

**Steps to replicate:**
Install Ubuntu 10.10 (x64) beta from CD 
Run installed system (at this point the ethernet worked fine) and immediately launch Software Update (System Update?)
Install updates (partial was offered presumably cause 10.10 is still beta)
Restart System

**Problem:**
Onboard Realtec gigabyte ethernet no longer works. Does not detect a network cable connected. Lights do not come on on back of motherboard showing link status. Port appears to be dead.

Now here is the strange part (and the bad part). The gigabit ethernet no longer works in Windows 7 either, where it was working perfectly before. I have tried different ports on the router and it doesn't show a link light either. Something seems to have knocked out the onboard ethernet on my motherboard. 

What could have caused this? Was it a new kernel or some process during the updates? Any idea how I can fix this short of RMAing my motherboard? 

Thanks for your help and suggestions. If you have a P55 mobo and have 10.10 beta I would suggest you hold off on updates if you have a realtec onboard LAN or you might loose it. Or if you have updated and it still works, please let me know.

---

### Post by CharlesA on 2010-09-23
It really sounds like a hardware problem tbh. I've had a similar thing happen to me exact it was on a brand new mobo. The network card would work off and on, no matter what OS was on it.

I don't think a software update can fry hardware.

I'd RMA the mobo, if you can.

If you want to hold off on the RMA until Maverick is out of beta to see if the problem persists.

---

### Post by Zoea on 2010-09-23
Doesn't it seem strange that I had no problems with all my time in Windows until I tried a linux update though? I have tried reflashing my mobo bios to see if that helps but no luck. I just dont want to see this happening to any other people with this particular hardware combination.

I will try 10.10 when it's not beta for sure but since the adaptor doesn't work in windows any more I don't think it's coming back to life. Can't RMA at the moment since I have a lot on and I don't really want to RMA anyway.

---

### Post by CharlesA on 2010-09-23
Understandable. :)

---

