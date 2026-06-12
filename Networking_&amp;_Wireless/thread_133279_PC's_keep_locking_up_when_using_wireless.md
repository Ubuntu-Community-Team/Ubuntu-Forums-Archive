---
title: "PC's keep locking up when using wireless"
date: 2006-02-19
forum: Networking &amp; Wireless
---

### Post by AndyCooll on 2006-02-19
After months of toil, thanks to these forums I finally got my wireless network up and running and everything was fantastic ...only it wasn't ...

_Equipment_
I have four boxes running Ubuntu 5.10 Breezy, and three of them were connected to my network via Belkin Wireless G USB Network Adapters (using Ralink's rt2570usb driver). The fourth is my file server which has always been connected to my network using a traditional ethernet link. My router is a Belkin Wireless G router.

_The problem_
At intermittent stages the pc will lock up and the only solution is to force a reboot.

_Symptoms_
Invariably, at least a couple of times an evening the pc will lock up and this has become such a problem that I've reluctantly been forced to go back to ethernet connections. 

The problem is that it is intermittent so it is difficult to pinpoint exactly where the fault might be. Running Totem to play music might be ok all evening if the box is left running and no other action is taken. But then again accessing music files might cause a lock up. You can often access the Internet fine and then it will suddenly lock. However, accessing Liferea (the photo album) is usually a no no as this invariably locks the pc up.
It's almost as if too much network traffic causes a lock up.

The further problem is that I can't use any system tools to investigate what might be wrong as the box is locked. Checking the system logs I get the error message "Cannot connect to 192.168.2.2" which is the file server. However the file server is on an ethernet link and is accessible using another pc, showing the link hasn't actually been lost. And I get this message whether the lock-up occurs when accessing a file on the server or not

This issue occurs on all pc's. And the wireless equipment works fine too. If I log in to XP on my dual-boot pc the wireless network never misses a beat all evening! Equally, return to an ethernet connection on each box and the locking up issue disappears.

_Help requested_
1. I'm no Linux expert, so are there any other logs I might check for information?
2. Is there any software or whatever I might use to monitor the wireless network connection?
3. Anyone else experience the same problem, and if so what actions did you take to resolve the problem?

---

