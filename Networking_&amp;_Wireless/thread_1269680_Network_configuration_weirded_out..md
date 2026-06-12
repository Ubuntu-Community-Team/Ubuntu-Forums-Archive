---
title: "Network configuration weirded out."
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by gearheadgeek on 2009-09-18
I am trying to get wireless working on a fitpc2.  I configured it with network-admin and it connected to my Airport.  I could ping the other boxes and even surf.  So I rebooted and it did not connect. It seemed to say it was connected. Looking with network-admin, the wireless box was checked and properties had all the right stuff and ifconfig showed packets arriving and leaving.  But I couldn't ping anything.

So, since the fitpc2 has an ethernet port, I plugged in a cable and configured the hard link with network-admin.  I could not see a way to disable the wireless there (it seems like once there was an 'enable' checkbox in the upper left but now it is a 'roaming' checkbox) so I ran ifconfig ra0 down. The hard link worked and I was able to transfer the files off the box.

Next reboot, ifconfig says that eth1 has an ip and ra0 does not.  /etc/network/interfaces only mentions ra0 (ip address, net mask, gateway, essid, etc).  network-admin has a '-' in the hardwired box and a check in the wireless box.  /etc/NetworkManager/system-connections does not exit.

Ubuntu has information stored somewhere causing it to use eth1 instead of ra0 although the configuration says it should be using ra0 instead of eth1.

How do I unravel this mess?

---

