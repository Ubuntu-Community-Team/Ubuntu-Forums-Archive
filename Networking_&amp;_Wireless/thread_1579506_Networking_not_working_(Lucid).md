---
title: "Networking not working (Lucid)"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by outofplace on 2010-09-21
Ok,  I have a computer here running ubuntu 10.04.  The little network icon at the top keeps spinning and when I place the cursor over it I get "Requesting a network address from the wired network..."  I have tried "manual configuration", but I get a warning telling me that it does not work with my operating system.  It gives me a list and I choose ubuntu 8.04.  when I change the settings there they do not seem to take affect.  If I reboot the setting changes are gone.  I have checked the logs on my router it does not show any dhcp requests from the hardware address of the computer in question.  I have tried modifying the /etc/network/interfaces file by including the lines

auto eth0
iface eth0 inet dhcp

when i do this the icon at the top changes to "manual configuration" but I still have no network connection.   One interesting thing I have noticed is that this machine has two network interfaces.  They are both integrated into the motherboard and the first six figures of their macs are the same, yet network manager reports one as being nvidia and one as marvel.  could this all be the result of a driver issue?

---

### Post by outofplace on 2010-09-22
well i just modified the /etc/network/interfaces manually.  it works and i guess that's good enough.  If anyone has anything to say about this one I would still like to hear it. but i'm going to bed.  now if i can just figure out to mark this thread solved...

---

### Post by sikander3786 on 2010-09-22
Glad you got it working. Your motherboard manufacturer might have used 2 different chips/sources for NIC integration i.e, 1 from Nvidia and 2nd from Marvell. No problems there. See your motherboard documentation if you think Ubuntu is not recognizing them properly.

---

