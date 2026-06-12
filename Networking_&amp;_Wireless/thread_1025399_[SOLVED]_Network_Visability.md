---
title: "[SOLVED] Network Visability"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by Thundara on 2008-12-30
For the past few months, I've been accessing documents storing on my main computer (Running Vista) via a shared folder as they were both on the wireless network. However, recently, I've been messing with the network configurations on each to force a static internal IP instead of getting it from the DCHP as it helped resolve some issues with port forwarding.

Everything worked fine, until the computer running ubuntu got rebooted, after a bit of messing around with the network settings, I'm able to connect properly to the network, but the computer can no longer be seen by others on the network, making the shared folder unusable and connecting within the network no longer allows for the name of the computer to be used in place of its internal IP (e.g. "computer-linux" instead of "192.168.1.100")

Does anyone know of a fix for this problem, preferably using GNOME's network manager because it overwrites the other network configuration files.

---

### Post by Liviu-Theodor on 2008-12-30
So, you have two computers, one with Vista, the other with ubuntu, connected wireless. Which one can not longer be seen in the network? The ubuntu or the Vista one? And can you try to use again DHCP, not static configuration?

---

### Post by Thundara on 2008-12-30
> **Liviu-Theodor said:**
> So, you have two computers, one with Vista, the other with ubuntu, connected wireless. Which one can not longer be seen in the network? The ubuntu or the Vista one? And can you try to use again DHCP, not static configuration?
The computer running Ubuntu cannot be seen, the other one is still visible on the network to others. I'd rather not use DHCP for them because it means that ports in the router need to be updated every so often whenever a computer disconnects and reconnects inside the network.

---

### Post by Liviu-Theodor on 2008-12-30
So you have also a router. That means you have more computers. You could try then the configuration we have at my workplace: a router, your server(s) with static IP adresses (with two network cards, one for the router, the other for the stations), and the rest with dinamic IP adresses. Our servers are with Fedora, the workstations are with various variants of Windows and just two Ubuntu stations.

Or, simpler, first verify if you have SMB (samba share) installed on your Ubuntu system. This is required for Ubuntu files to be seen under Windows.

Or maybe you have changed your workgroup on the Ubuntu system. In this case try [this advice]("http://ubuntuforums.org/showthread.php?p=6263366#post6263366").

---

### Post by Iowan on 2008-12-30
Another potential solution is to issue a "static lease". Configure the router to assign the same IP address, based on MAC address.

---

### Post by Thundara on 2008-12-30
> **Liviu-Theodor said:**
> So you have also a router. That means you have more computers. You could try then the configuration we have at my workplace: a router, your server(s) with static IP adresses (with two network cards, one for the router, the other for the stations), and the rest with dinamic IP adresses. Our servers are with Fedora, the workstations are with various variants of Windows and just two Ubuntu stations.

Or, simpler, first verify if you have SMB (samba share) installed on your Ubuntu system. This is required for Ubuntu files to be seen under Windows.

Or maybe you have changed your workgroup on the Ubuntu system. In this case try [this advice]("http://ubuntuforums.org/showthread.php?p=6263366#post6263366").

Doh! Samba was installed, but for some reason it hadn't started up, which I found out after messing around a bit with the configuration file and going to restart it. Both the shorthand name and shared folders are now working, thanks for the help!

---

