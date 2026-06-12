---
title: "how to use the network manager"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by matt the destroyer on 2009-04-27
**EDIT: ISSUE IS RESOLVED**

Hey everybody

I just installed kubuntu 9.04 and I cannot get the _wired_ network to work via the network manager.

Most solutions that I have read involve installing another network manager, but since I don't have connectivity, I can't install any software.

So, I am trying to connect to a network that does not use DHCP.  I have:

[LIST]
[*]a fixed ip
[*]a subnet mask ( 255.255.255.128 )
[*]the gateway ip
[*]a dns server ip
[/LIST]
I go into system settings->network settings -> manage connections

I input the information above, save it.

I click on the icon in the system tray and try to connect using the connection I just created, but I just get an error message that the connection failed.

I **think** that the problem has to do with the subnet mask: the connection manager asks for the subnet prefix, and this does not save the actual mask (won't accept periods).  I have tried 255 and 128, but neither of them work.

Does anybody know how to use the network manager and how to get it to accept these settings?

Thank you,
matt

---

### Post by kerry_s on 2009-04-27
shouldn't the subnet mask be: 255.255.255.0

---

### Post by matt the destroyer on 2009-04-27
No, it is 255.255.255.128.

I have the documentation in front of me, and that is the setting that works in xp.

It is a managed network, thousands of clients, many subnets.

---

### Post by matt the destroyer on 2009-04-27
OK, I found the answer.  The network manager is looking for the CIDR notation of the subnet mask, which for 255.255.255.128 is 25.

For those of you with the more common 255.255.255.0 mask, the CIDR notation would be 24.

Talk about unnecessarily obscure (not mentioned in the man pages anywhere).  I see what all the negative press for KDE 4.2 is about.

---

### Post by kerry_s on 2009-04-27
glad you found the answer, i looked all over, but was to tired to read. :lolflag:

---

