---
title: "Network disabled itself"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by JKyleOKC on 2009-10-04
I'm in the process of rebuilding my home office LAN and have encountered a strange situation that has me baffled.

I bought a new Compaq mini-tower box with 3 GB of RAM and Athlon dual-core CPU, and installed a second NIC in it so that it could serve as my WAN gateway to the internet and also be the firewall and router for my LAN, which has three other boxes on it.  I then left Vista Home Premium on the drive but reduced its partition to 10 GB, leaving some 260 GB for Xubuntu, installed Xubuntu 8.04 LTS, and downloaded some 230 updates to bring Hardy to 8.04.3. At this point the second NIC had not been configured. Next, I configured it as eth1, installed Webmin, Tripwire, and Portsentry, and configured iptables to provide NAT action.

After a couple of days of tweaking and troubleshooting, it was all working to my satisfaction. I then put the box into hibernation for the night.

When I tried to bring it back up this morning it did not respond. I rebooted it, twice, before noticing that the KVM switch was set to another box. Once I hit the KVM switch, it booted with no reported errors (I use the old text-summary boot process).

However, the machine would no longer connect to either the WAN or my LAN. It still functions as the router for the LAN, permitting the other boxes to communicate with each other, but all of them fail to find the WAN.

After spending a large part of the day trying to troubleshoot the situation, I re-booted the new box into Vista just to test the hardware involved in getting to the internet. It all works perfectly there, but not at all in Xubuntu.

I'm convinced, now, that it's a configuration problem of some sort, but I've set iptables to accept everything and only handle NAT, with no change resulting. I've tried disabling Network Manager since all my addresses are static (even my DSL line) but then the LAN died also, so I put it back in action.

Any ideas as to what to try next? Incidentally I'm having to post this from my laptop via WinXP, and since XP refuses to connect to my LAN it's difficult to attach file excerpts...

---

### Post by JKyleOKC on 2009-10-05
bump

still no WAN access...

---

### Post by Iowan on 2009-10-05
With multiple interfaces, I presume (at least) one of them is configured in */etc/network/interfaces*. Check the settings there to see if all looks kosher there.

---

### Post by JKyleOKC on 2009-10-05
It all did; however after spending most of a week trying various things, I bit the bullet and re-installed Hardy LTS to wipe out all the mistakes. After the re-install it still didn't work until I checked the syslog file and found that the eth0 and eth1 labels had been automagically swapped by udev! After I edited the appropriate rules in the /etc/udev/rules.d directory (70 and 75 dealing with persistent nets) to prevent such renaming, the re-installed system worked and let me download the 239 updates necessary to go from my CD to the current release level.

I then set out to implement NAT, and after editing /etc/sysctl.conf to match the old one (including adding a couple of lines to deal with a reported Hardy bug) it quit seeing the internet again although the interface was up and running. I went back and undid all the changes there, except for setting the "forwarding" flag, and it's working again.

Apparently the failure after hibernation was caused by the automatic renaming by udev; the sysctl changes were things I had tried later in my attempts to get things going again.

Thanks for the response! Once I complete this project and get it all up and running I think I'd better put together a HOWTO for the Tips and Tutorials section...

---

