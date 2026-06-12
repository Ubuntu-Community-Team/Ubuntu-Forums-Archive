---
title: "Help connecting with motion controller"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by iron_guitarist1987 on 2010-06-09
I'm having a problem connecting a motion controller through the Ethernet port. Here is what it does

If I connect the Ethernet cable from the computer to the controller, the connection is not recognized.
If I connect it from the computer to my router, it will connect automatically.
If the computer is connected to the router, and I unplug the router and quickly connect the controller, it will automatically recognize it.
Also, when I connect the controller with quickly unplugging the router, I can't manually connect it using the  wired connection "Auto eth 2". When I click on it, it thinks for a while and then says Wired Network Disconnected.

Is there a way to initialize the Ethernet port automatically to recognize the motion controller, or is there a way to do it using C++ (that is what I'm suing to communicate to the card since it has special libraries)

I find this kind of weird. I want to just be able to plug in the controller and be able to use it.

Thank you.

---

### Post by Iowan on 2010-06-09
Intriguing... sounds like something I'd like to try.
(What kind of motion controller?)
Is it an addressing problem? Do all "parties" have an IP address, or does the temporary connection to the router get one assigned?

---

### Post by iron_guitarist1987 on 2010-06-10
The controller is a Galil DMC-2123.  I think the router always assign a different IP by default, but I'm not sure. The motion controller has a static IP address.

---

### Post by Iowan on 2010-06-10
Check the "Auto eth2" connection to see if it's trying to get DHCP address. You might need to give it a static address in the same subnet as the motion controller.

---

