---
title: "All was well, then vmware player ruined it"
date: 2005-12-14
forum: Networking &amp; Wireless
---

### Post by harty83 on 2005-12-14
Heres the problem.

I'm running breezy, using ndiswrapper with my broadcom card, and am using network manager.  All was working great!

Then, I attempted to install vmware player.  After the installation process finished, my computer locked up.  I did a hard reboot and then I can't connect to the internet.  I uninstalled vmware player.  And am still having issues.

I've disabled my ethernet card, however network manager is still connecting to a wired ethernet!  I don't even have a cable plugged in.  Why is that?  My assumption is that it is connecting to the interface vmware created that is bridged to my eth0 because I right click on network manager, then click on connection information and it says:

Interface: Wired ethernet (eth0)
Ip Address: 169.254.148.138
Broadcast Address: 169.254.255.255
Subnet Mask: 255.255.0.0
Hardware Address: 00:0D:56:36:2E

So a) how do I delete the "hardware" vmware installed (of that is the problem) and get networking working properly again.  And b) how can I get all of the above listed software to work together without jacking things up?

Thanks in adance!

Alan

---

### Post by mlomker on 2005-12-15
Hmm.  I don't use the player but have full VMWare.  Are these modules still running on your machine?  If not then it shouldn't be affecting anything anymore.

```

mlomker@mlomkernote:/$ lsmod | grep vm
vmnet                  37796  3
vmmon                 112236  0

```

---

