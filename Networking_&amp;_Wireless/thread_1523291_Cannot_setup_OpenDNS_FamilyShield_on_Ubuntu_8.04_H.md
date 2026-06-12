---
title: "Cannot setup OpenDNS FamilyShield on Ubuntu 8.04 Hardy Heron"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by timzak on 2010-07-03
I posted this on OpenDNS message boards, but not sure if they can help me there.  I thought some Ubuntu gurus might be able to lend a helping hand.

I am having trouble setting up FamilyShield on an Ubuntu 8.04 system. The setup instructions on this (opendns.com) site are for newer versions of Ubuntu. Network Manager settings are different in 8.04 and don't correspond to the instructions. However, given the age of this computer, it cannot run a newer version of Ubuntu, and 8.04 is an LTS supported until 2011, so I am stuck with this OS for now.

Complicating matters is I am living as a guest, so do not have the option of setting FamilyShield on the router. It must be done on my computer.

Here's what I've tried:
System->Administration->Network
go to DNS Tab and add the FamilyShield DNS numbers. BTW, there are two DNS numbers from the internet owner's ISP (Roadrunner) automatically in here already, along with "socal.rr.com" in the Search Domains field. If I try to delete them, they reappear when I reboot. If I add FamilyShield DNS numbers here, either along with, or in place of the ones that automatically appear here, they do not take, and on next boot FamilyShield DNS numbers are gone, but "socal.rr.com" DNS and search domains reappear.

I've also tried:
```
sudo gedit /etc/dhcp3/dhclient.com
```
and added following line at the end:
```
prepend domain-name-servers 208.67.222.123,208.67.220.123
```

When I reboot the system, I'm still using the assigned DNS numbers from "socal.rr.com".

I was able to try a newer version of Ubuntu (on a different machine) on this network, and it worked fine with the setup instructions. So this appears to be a problem specific to how Ubuntu version 8.04 handles DNS number changes.

Any help would be greatly appreciated!

---

### Post by timzak on 2010-07-03
Thanks to Brandon Williams.  I found a thread he responded to that gave me the little extra info I needed to get going here:
[http://ubuntuforums.org/showthread.php?t=1416515&highlight=opendns](http://ubuntuforums.org/showthread.php?t=1416515&highlight=opendns)

If anyone's interested, I'll detail the changes that were required.

---

