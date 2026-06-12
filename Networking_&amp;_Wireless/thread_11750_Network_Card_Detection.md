---
title: "Network Card Detection"
date: 2005-01-19
forum: Networking &amp; Wireless
---

### Post by cupz on 2005-01-19
I cant seem to get my nic working under ubuntu. its an onboard 3com, and it doesn't show under dmesg. I tried installing the drivers as per this readme [http://www.geocities.com/cupzonia/readme.txt](http://www.geocities.com/cupzonia/readme.txt) , but when i use 'make' it comes back as "gcc: unknown command".
any help or suggestions would be much appriciated.

Edit: I installed the build essentials, which makes the 'make' command work, but now i get a terminal window filled with errors. is the 3Com Gigabit LOM (3C940) supported at all?

---

### Post by hardcandy on 2005-01-19
[http://www.linuxquestions.org/hcl/showproduct.php?product=1060](http://www.linuxquestions.org/hcl/showproduct.php?product=1060)

[http://www.asus.com/support/download/item.aspx?ModelName=P4P800%20Deluxe&Type=Drivers](http://www.asus.com/support/download/item.aspx?ModelName=P4P800%20Deluxe&Type=Drivers)

[http://www.scyld.com/pipermail/vortex/2004-February/002684.html](http://www.scyld.com/pipermail/vortex/2004-February/002684.html) in this thread it was successful using the scyld build of the  3c59x for an Asus board. What is the readout  of lspci "sudo lspci" ? Or the device manager manager name for it.

---

