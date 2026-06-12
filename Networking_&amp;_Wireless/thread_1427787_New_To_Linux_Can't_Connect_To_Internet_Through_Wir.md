---
title: "New To Linux Can't Connect To Internet Through Wireless Network"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by jmanson2 on 2010-03-11
I just installed Ubuntu 9.10 64 bit on my HP Touchsmart TX2 1020us which has a Broadcom 4322 chip.  At first my computer didn't seem to see the card at all, but then I typed the command (sudo apt-get install bcmwl-kernel-source) and then restarted the computer and now I'm connected to the network, but cannot connect to the internet so how do I figure this out.  Like I said I have very little experience with linux at all so please don't make your answers too complicated.

---

### Post by helgman on 2010-03-12
Hello,

Open a terminal (if you don't know where it is just take a look around you applications) and then past the output of the following commands in your reply:

[LIST=1]
[*]ifconfig
[*]iwconfig
[/LIST]

Regards,
Helgman

---

### Post by jynyl on 2010-04-03
You might find this one useful ... [http://ubuntuforums.org/showthread.php?t=1368699]("http://ubuntuforums.org/showthread.php?t=1368699").

It seems the 4322 chip is new and existing versions of Ubuntu don't have drivers for it.  Here's hoping Lucid will be up to date.

---

### Post by Iowan on 2010-04-04
Have you tried (also from a terminal) pinging Internet by IP address (74.125.95.99)?

---

### Post by mcoleman44 on 2010-04-04
system>admin>hardware Drivers 

STA

---

### Post by mcoleman44 on 2010-04-04
Go here if your interested in making the touchscreen work
[http://ubuntuforums.org/showthread.php?t=1252492](http://ubuntuforums.org/showthread.php?t=1252492)

---

