---
title: "No WiFi Access, Only Wired"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by KemKev on 2011-02-05
Fresh installation of Ubuntu 10.10 does not "see" my wireless network (Windows 7 "sees" it quite fine). I ran [COLOR="Blue"]sudo lshw -C network[/COLOR] and it showed the network is disabled (see screen print of output attached).  The wireless switch on my laptop is on.  

From reading various threads, it seems there is a problem with the Broadcom B43XX cards that requires some manual workarounds to get them to work.  Mine is B4311.  Sure would appreciate any help and thanks in advance.

---

### Post by KemKev on 2011-02-05
**RESOVLED**
I installed the proprietary driver for the B43XX and that did the trick.  To launch the utility, System -> Administration -> Additional Drivers.

---

### Post by Ad1217 on 2011-02-05
Or you can run "sudo jockey-gtk" in the terminal.

---

