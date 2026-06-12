---
title: "Ethernet port not working"
date: 2012-08-05
forum: Networking &amp; Wireless
---

### Post by lukster91 on 2012-08-05
I have an installation of Windows 7 Home Premium (64-bit) on my PC, I installed Ubuntu 12.04 under Wubi.

I updated Ubuntu and restarted computer to affect updates, upon restarting the Ubuntu installation corrupted and I lost the Ubuntu installation, I couldn't make any changes. Upon selecting Ubuntu in the OS selection screen, Ubuntu would just give a purple screen.

I launched windows and deleted the Wubi OS, and now my Ethernet port no longer works.

I have tried the Ethernet port with 2 different cables and checked both cables with laptop, the ethernet port was working before the corruption on both Windows 7 and Ubuntu.

I can't access the internet to update the driver, and I don't know how to fix my ethernet port.

Can anyone help?

Thanks.

---

### Post by The Cog on 2012-08-05
Have you tried physically powering off and on again? I have known Linux/Windows to leave hardware in a state where the other can't use it without a power reset.

---

### Post by lukster91 on 2012-08-05
"Have you tried turning it off and on again?" 

Lol. Yes, first thing I did.

Thanks though

---

### Post by steeldriver on 2012-08-05
In what way exactly does it no longer work under Windows? does Windows not detect the device at all (possibly BIOS disabled)? do you get an IP address but no connection? can you connect to LAN devices but not internet?

Have you done any network troubleshooting via Windows? what is the output of ipconfig in a Windows cmd window?

---

### Post by lukster91 on 2012-08-05
Sorry, thought I'd been more specific than that.

No register of connection, no ip... network centre says not connected, no available connections. No Lan, nothing. The ethernet light isn't on at the back of the tower. - So ipconfig won't tell me anything new.

I will check the BIOS.

Thanks for the idea!

---

### Post by lukster91 on 2012-08-05
Thanks. It was the BIOS.

I found an option uder AI NET 2 called Check Realtek LAN cable. It was disabled and I set it to Enable.

Doing this solved the problem and I am now online on my desktop.

Thank you.

Luke

---

### Post by choel on 2013-02-13
Thanks, a lot! Been sitting with it for hours, tried restarting my computer and all, but never turned it off completely. Thanks!

---

