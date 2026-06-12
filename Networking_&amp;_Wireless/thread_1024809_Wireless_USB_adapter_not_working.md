---
title: "Wireless USB adapter not working"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by richard.e.morton on 2008-12-29
Hi, Merry Christmas!

I have a USB unnamed wireless adapter, when I do an LSUSB with the card in I get the following:

Bus 001 Device 003: ID 0416:0035 Winbond Electronics Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000  

I have searched for drivers to no avail. has anyone any ideas if this card has drivers that work for it in Linux / Ubuntu / Fedora

thanks

Richard

---

### Post by Maddman on 2008-12-29
You might see if ndiswrapper supports your wireless card.  Its a package that allows Windows drivers to work on linux.  You will have to have the windows driver to make this work, which will require identifying the card.

If the USB adapter isn't labeled with a make and model, you might try plugging it into a Windows box and see if it auto-detects.  Then you could see the model number and locate a windows driver for it.

---

### Post by richard.e.morton on 2008-12-29
Hi 

ok, cool. and thanks for the quick reply. to think I was losing faith in these forums...

I will look at NDISWrapper is there much of a CPU overhead in using this over a native driver? latency? cpu/memory increase?

I plan on using it on a low power MiniITX board for video playback as a Myth frontend - it is fine with playback over 100Mbps wired LAN during testing, but the project is nearly finished (being nagged by my other half to get the TV working) and this is before we can finish the decorating and lay all the permanent cables.

thanks

Richard

---

