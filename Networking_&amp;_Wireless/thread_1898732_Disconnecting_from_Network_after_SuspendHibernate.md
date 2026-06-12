---
title: "Disconnecting from Network after Suspend/Hibernate"
date: 2011-12-22
forum: Networking &amp; Wireless
---

### Post by cyberm4tic on 2011-12-22
I understand that it is the default behavior of Ubuntu to disconnect a wireless connection when the computer suspends or hibernates; however, I find this annoying since it takes a non-trivial amount of time for my computer to reconnect after I turn it back on (15-25 seconds). While this may seem like little time, over time it becomes very annoying, especially when you are suspending/resuming frequently.

I was wondering if there was any way to preserve a connection after suspending/hibernating so that my computer doesn't disconnect from the network? I know Windows does this, and was hoping that the same could be achieved with Ubuntu.

My specs are:
-Ubuntu 11.10
-32 Bit Processor
-Dell Latitude E6500

I'm new to these forums, so please inform me if I'm missing anything.

---

### Post by kurt18947 on 2011-12-22
When I resume after suspending 11.10, I get a message upon resuming that my network is disconnected.  The NM applet says otherwise and I do indeed have a network connection by the time I have a usable screen.  I had a problem with NOT having a WiFi network connection upon resume at one time, I had to remove and reinsert the USB adapter to get a connection.  That problem was caused by not disconnecting the network prior to suspending to RAM.  15-25 seconds to reestablish a connection does seem like quite a long time, though. I have 2 machines with WiFi connections and they re-establish a network connection in < 5 sec. after resuming. I have no guess as to  why your connection take so long to reconnect.

---

### Post by cyberm4tic on 2011-12-31
My problem is combination of lag, and occasional failure of the software to begin searching for networks, i.e. it will remain disconnected and not begin to search for networks until I do something like connect to a hidden network. Does that sound familiar at all?

---

