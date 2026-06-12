---
title: "Specific Wireless Problem"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by Jack Knights on 2010-08-22
Alright, first off I am new to Ubuntu, so I need step-by-step instructions on how to fix my wireless. I was using wireless fine today, but after I closed my laptop and moved to a new place, the wireless shut itself off. This has happened before and only required a simple restart to turn it back on. But now, it won't come back on and after a bit of trying, (resetting modem, searching for wireless networks, etc) it decided to deactivate the wireless completely. I can no longer "Enable Wireless" and I have no clue what to do. How do I fix this?

Extra info.
- HP G60-235DX (I had Vista, tried the demo of 7 and everything went to crap; now using Ubuntu without any drivers from Windows or any other OS. PURE UBUNTU), two years old.

---

### Post by Iowan on 2010-08-22
[Here ]("http://ubuntuforums.org/showthread.php?t=1505217")is a thread that might be helpful.

---

### Post by Jack Knights on 2010-08-22
I tried this:

 	Code:
 	 service network-manager stop
 rm /var/lib/NetworkManager/NetworkManager.state
 service network-manager start

and it didn't work, with or without "SUDO" in the beginning of the codes. I also tried:

[INDENT]service network-manager stop
 rm /var/lib/NetworkManager/NetworkManager.state
 service network-manager start
[/INDENT]and got the same results. I don't know what I did, but once I was able to check the box for "Enable Wireless" but nothing changed. I still couldn't find my wireless signal. I double checked my modem settings and it is able to be detected, my sister is using the wireless internet right now, so the problem definitely lies with my computer.

---

