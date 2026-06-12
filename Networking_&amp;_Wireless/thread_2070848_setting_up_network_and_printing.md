---
title: "setting up network and printing"
date: 2012-10-13
forum: Networking &amp; Wireless
---

### Post by tobythedog on 2012-10-13
hi i would liketo set up a network , all my machine have lubuntu or ubuntu no windows at all, i would also like to set up printers on the network.I have searched google but cannot find much on networks on lubuntu, does anyone know how to do this or any web sites that may help please.

---

### Post by ahallubuntu on 2012-10-13
There's a good chance that your router controls the network you are on and each Lubuntu/Ubuntu machine just gets its network information from the router (via something called "DHCP.").  So if you have a router, it is the place to configure your network.

If you want to set up a printer on your network, you can either get a printer that has built-in network card or built-in wireless and connect it to your router that way...or connect a printer to one of your Lubuntu/Ubuntu computers and share it on the network.

Each device on your network (including the printer if it is separate and not attached/shared via a computer) has its own unique IP address on the network, as controlled (probably) by your router.    When you try to connect a network printer, it can help to know the printer's IP address.  It is often a good idea to "fix" the IP address of your printer using your router - so it always gets the same IP address on your network.  Learn how to configure your router and look for something called "DHCP reservations" that allow the router to always assign the same IP to a device (like your printer).  Then, it will never change, and when you try to print, the printer will always be in the same place.

---

