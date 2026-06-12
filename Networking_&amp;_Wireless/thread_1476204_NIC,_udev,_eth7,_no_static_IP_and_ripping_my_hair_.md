---
title: "NIC, udev, eth7, no static IP and ripping my hair out!!"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by Anaximander Thales on 2010-05-07
I have no idea what to do about this.  I'm attempting to set my work computer to have a static IP address.  It was set this way prior to 9.04, but after 9.10 it's broken, and I prefer to have a static IP address.

Prior to upgrading to 10.04 (from 9.10), I noticed that my network had switched from a static IP address to a dynamically assigned IP address.  In addition to losing my static IP, I started noticing that my MAC address was changing.  I've tried multiple documents -- remove all the entries in 70-persistent-net.rules except the first rule, set a static connection in network manager, remove network manager and set all your static info in /etc/network/interfaces, add the MAC address into the /etc/network/interfaces, etc.

Nothing worked -- mac address still changes, and a new ethX is created (currently, on the fresh install, and testing things, I'm at eth7).  I am assuming this is having to do with udev and/or  dhcp3-client.  As these documents all tend to point to one or both of those.

However, I'm so friggin' frustrated about this right now, than I'm just not comprehending or able to find anything else useful to try.

All suggestions will be greatly appreciated.

Thanks,
AT

---

### Post by Iowan on 2010-05-07
DHCP leases are kept in (or near...) */var/lib/dhcp3/dhclient.eth0.leases *. You can see if there's a lease left in there somewhere that keeps renewing. I've seen other threads about changing MAC address, but the idea still seems just *wrong*...

---

### Post by Anaximander Thales on 2010-05-12
Thanks --

I checked that, wasn't sure what useful information I found and became confused as to how this might be helpful and re-read my post.

My network remains the same as long as the computer is on.  The issue I'm having only occurs on reboots.  An illustration --

Install completed for 10.04
Log in -- 
look at Network Manager -- Auto Eth1
Do updates
Reboot
Log in
Look at Network Manager -- Auto Eth2
Reboot, etc, etc.

Every time this occurs, I have a new mac address for my network card.  I don't change the mac address, and I don't want it to change.  I want to keep a static ip address on my machine -- however, I can't.

When I use network manager, and create a staticly assigned IP address adn tell it to auto connect [Wired Conenction 1], and remove the auto connect from Auto Eth* it works fine until the reboot.  At which point, Auto Eth*+1 is created, and Wired Connection 1 fails to connect.

Any other suggestions?

Thanks
AT

---

