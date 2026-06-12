---
title: "Can't access network printer"
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by afk46 on 2011-01-23
Hello,

I recently installed Xubuntu 10.04 on a desktop computer.  Everything works fine aside from the fact that I can't access my Dell 3010cn network printer. 

The printer is accessible and work flawlessly with every other computers running XP, Vista and Ubuntu 9.10

I installed the drivers and configured the printer with the exact same parameters as on my 9.10 laptop. 

The thing is that the printer is always "offline" as if my computer could not connect to it. Also, when I try to acces its options via its fixed IP adress (192.168.1.107) through Firefox, I cannot reach the printer. However, the printer responds to every other computer in the house.

What am I doing wrong? Is there a firewall in 10.04 that keeps me from accessing to the printer?

Thanks for your help!

Jim

---

### Post by watgrad on 2011-01-23
Not and expert here, but try this (if you haven't already):

Open 'Printing' setup from the System->Administration menu.

Select the Server menu item.  Then Choose "Settings".
Check the box, "Show printers shared by other systems"

Click OK and see if the networked printer shows up in the Printing window.

---

