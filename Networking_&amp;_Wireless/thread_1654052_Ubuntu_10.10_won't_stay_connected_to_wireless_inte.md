---
title: "Ubuntu 10.10 won't stay connected to wireless internet"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by babaloual on 2010-12-27
Hi everyone,

I am running Ubuntu 10.10 on a Dell Dimension 4700 desktop computer. I just upgraded to 10.10 from the previous version after getting my D-Link wireless adapter back after loaning it out. My internet now won't stay connected. I can connect when I first turn on the computer, with after 2-5 minutes it drops the connection and gives me the "Wireless Network Authentication Required" prompt. It won't connect again without unplugging the adapter and plugging it back in.

I borrowed a Belkin wirelss adapter to try it, and it does the exact same thing. PLEASE can someone help me, I really need the internet up on the computer.

(Also, when I first got the adapter-- while running the old version of Ubuntu-- it would not recognize or connect at all and I spent 4 hours messing with drivers and settings to get it to work, which it did flawlessly. Until I upgraded.)

Thank you!!

---

### Post by DonJuan4076 on 2011-01-10
Hi

I am having the same problems as the poster. Please help. I currently am running Ubuntu 10.10 and windows 7. Windows 7 has no problems connecting and/or staying connected to the Internet but when i log into Ubuntu 10.10 it iwll stay connected to the internet for 2-3 min then logs off. I have reinstalled Ubuntu a few problems so that not the problem.... please help

---

### Post by PatchesTheCaveman on 2011-01-11
Please provide diagnostic information as requested in this post so we can assist you:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by jimmydean886-2 on 2011-06-26
This seems to be a problem with any system running snmp. When you run SNMP, it interrupts the wireless connection from time to time for some reason or other. If you are using a secured network, and you never have an intent of using an unsecured one, removing it seems to solve the problem. It also shaves off about 3 seconds of boot time, more on older systems most likely.:) Try it on your computer, and if it causes problems, just reinstall the snmplib5 package. That's the one you should have removed in the first place. I hope this is the solution you are looking for!


EDIT: This will NOT prevent you from connecting to unsecured networks.
EDIT(2): DO NOT ATTEMPT if you have an HP scanner or printer. Some drivers require snmplib5 to work.

---

