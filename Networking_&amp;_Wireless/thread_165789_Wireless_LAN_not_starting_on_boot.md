---
title: "Wireless LAN not starting on boot"
date: 2006-04-25
forum: Networking &amp; Wireless
---

### Post by Phasmagon on 2006-04-25
Hello everybody,

I recently switched to Ubuntu Dapper Drake 6.06 Beta and the problem I am facing is that my Broadcom wireless NIC is not working unless I deactivate and re-activate it again. Then everything is fine. But when the computer boots, nothing.

Can anybody help with this issue?

---

### Post by TrojanSkin on 2006-04-25
Sorry, I can't help. I had the same problem with my 3Com USB wireless adapter. I ended up going back to Breezy. Still have to run #modprobe ndiswrapper every time I log on, though. Frustrating.

---

### Post by rado_london on 2006-04-25
Try to make the eth0 (if this is your card) to be default in System -> Administration -> Networking. 
If  it doent work look at[ this thread]("http://www.ubuntuforums.org/showthread.php?t=152382")


Good Luck

---

### Post by TrojanSkin on 2006-04-26
Try this [http://www.ubuntuforums.org/showthread.php?t=162587]("http://www.ubuntuforums.org/showthread.php?t=162587")
Don't know about Dapper, but it works on Breezy.

Good luck!:-D

---

