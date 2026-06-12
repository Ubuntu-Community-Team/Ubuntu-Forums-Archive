---
title: "D-link G132 USB Wireless Adapter Drivers using Ubuntu Gutsy Gibbon or Heron"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by Howinlinux on 2008-12-12
Hello!

I recently ran across a regression in the Ubuntu Heron version.  While upgrading, the D-Link G132 USB Adapters may not incorporate the drivers correctly upon completion of the install / upgrade.  My question is below this paragragh.  Here are my experiences and the answers from moderators and gurus, I hope they help.

After the upgrade my wireless adapter driver was not working correctly.

I checked for the two driver files (it takes 2 with this card) using: 

ndiswrapper -l

and it showed both drivers A5AGU.INF and the other one where installed, but it only showed that the device was present on the A5AGU.INF (can't remember the name but is is like athmfl.inf or so)


It was working just prior to the upgrade.

I had previously installed the wireless GUI utility for NDISWRAPPER and so I used it to uninstall the drivers and re-install but that didn't work.

I also tried to re-install using:

ndiswrapper -i "MYPATH/a5agu.inf
**THIS IS FINE AND THE DEVICE SHOWS AS PRESENT**

ndiswrapper -i "MYPATH/athmfl.inf 
**THIS STILL DOES NOT LOADS THE DRIVER BUT STATS NO DEVICE PRESENT**
(for those looking for help, MYPATH is actually the path where the drivers are located)

So I am at a loss. What can I try to do?

---

