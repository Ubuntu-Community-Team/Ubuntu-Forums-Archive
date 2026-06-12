---
title: "Directly connected Network printer unreachable."
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by soundman64 on 2010-10-03
Hi,
 I have a network printer directly connected via ethernet cable to an Ubuntu netbook, but pinging the printer fails, giving "Host Unreachable".
The network light on the ethernet socket is lit green, and there is  nothing else cable-connected to the network - just a simple cable  connection between the netbook ethernet socket and the Network printer (a HP Laserjet  4200n).
Ping works fine if I plug the cable into a different machine (a Win XP box) and ping from there, so it's not a cable or IP address problem. 

This sounds simple enough and should work, but I'm stumped. Clues, anyone?

---

### Post by relay_man on 2010-10-03
The "host unreachable" response usually results from a mis-configuration of address, or a hardware problem.  I would recommend that you check the netbook address very carefully.
If there are no addressing mistakes, try to ping the address of your printer using your netbook.  If you cannot ping that address and you are sure your addressing is correct, I would try a different cable.  If you are connecting the netbook directly to the printer, without going through a hub or switch, you will need a crossover cable. 
It is possible that the ethernet adapter in your XP box can do autocrossover, and the adapter in your netbook cannot.
If nothing seems to work at all, I always fall back to the basic troubleshooting steps.  Using your netbook:


1) Ping 127.0.0.1 or localhost
This verifies that the IP stack in your netbook is working correctly.

if that is successful, then

2) ping the ip address you've assigned to ethernet adapter in your netbook
(maybe something like 192.168.0.100)

If that is successful, then your adapter is working correctly.

3) It's time to check cables and the interface(s) of other devices you are trying to communicate with.

---

### Post by soundman64 on 2010-10-03
That's it!! Good stuff indeed, Mr Relay_Man. Thank you very much for your reply.

Looks like directly connecting two devices together via their ethernet sockets doesn't work - you need a special crossover cable to do that. These crossover connections are done internally in a hub or a switch. So without using a hub or switch, you must use a crossover cable.

 The fact that it worked OK from my WinXP box confused the hell out of me. As relay_man said, that adaptor must be doing an auto-crossover.

I simply connected the printer and netbook to spare slots on my wireless adaptor, and now I can ping the printer from the netbook.
I didn't know about the crossover issue, so hat's off to relay_man for pointing that out. I guess every day is a school-day, right!!

Thanks again relay_man for taking the time out to reply. I much appreciate the help. I'd still be scratching my head only for you!

---

