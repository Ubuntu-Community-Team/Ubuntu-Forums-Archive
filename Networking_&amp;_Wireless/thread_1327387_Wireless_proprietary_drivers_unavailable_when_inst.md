---
title: "Wireless proprietary drivers unavailable when installed"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by Bob33 on 2009-11-15
Hi Guys,
I've got a problem with an Inspiron Mini 12. The liveCD enabled me to activate the broadcom driver for the wireless (Broadcom TSA driver) and everything worked fine with the live CD (ubuntu 9.10). 
Then I installed it along windowsXp on the hard drive. 
When booted up from the hard drive I don't have the proprietary driver any more. Then I've tried to plug an ethernet cable but it doesn't work either. 
Now I cannot connect to the Internet and can't get any driver. I'm a bit stuck. 
Thanks for your help! :grin:

---

### Post by fbnaia on 2009-11-15
Hi Bob33, maybe this could be your problem, on the [**relase notes of 9.10**]("http://www.ubuntu.com/getubuntu/releasenotes/910") they state an issue with "Hardware driver tools", stating that "Package list must be manually refreshed before installing drivers"...

Full text:

"The "Hardware Drivers" tool (Jockey) requires up to date package lists before it detects and advertises necessary driver packages. Immediately after a new installation, these package lists will not be present. Before running Jockey for the first time, update the package lists using System->Administration->Software->Update Manager (on Ubuntu) or "KPackageKit" (on Kubuntu). (**[B]462704**[/B])"

Heres the bug report for reference:

[**https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/462704**]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/462704")

---

### Post by Bob33 on 2009-11-19
Hi,
I just tried but didn't manage to do it. 
By System->Administration->Software->Update Manager
do you mean System->Administration->Software sources->Update Manager
 or 
System->Administration->Update Manager

Then what shall I do?
Thanks (sorry I'm really a newbie)

---

### Post by SebastianJB on 2009-11-21
I had a similar problem. After updating my packages (in System->Administration->Update Manager) and rebooting, the drivers were available in System->Administration->Hardware Drivers. Apparently it won't notice the new drivers are available until after reboot.

---

