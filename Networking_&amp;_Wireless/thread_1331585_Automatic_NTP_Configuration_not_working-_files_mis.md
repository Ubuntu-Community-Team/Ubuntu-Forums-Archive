---
title: "Automatic NTP Configuration not working- files missing or ignored."
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by jdos2 on 2009-11-19
Been searching around on this a bit (University of Google...) and haven't found an answer. 

Coming to Ubuntu 9.10 from Debian Squeeze and have found some things different about the networking that I can't wrap my mind around.
Problem 1:
The NTP package isn't installed by default, so I did so, and all the binaries are in their right place, but the file /etc/dhcp3/dhclient-enter-hooks.d/ntp is not. This is the "action file" used by ntpclient to create a file called /etc/ntp/ntp.conf.dhcp using ntp parameters given by the DHCP server. 
Okay so I pulled apart the .deb that Ubuntu stored in the cache, copied the file over, and there it is.
(Problem 2)
But it is COMPLETELY ignored by Network Manager. In fact, it appears that nothing is honored in the /etc/dhcp3 subdirectory when NM has it's grasp on an interface.
So I delete all "Wired" interfaces under NM, create one, select the "Connect Automatically" and allow all users access to it... 
And the system won't try to get a DHCP address automatically. Selecting the "available connection" under the Gnome icon gives... An attempt to connect (spinning icon) and then a system notification that the network is disconnected.
Performing a very simple "dhclient eth0" then not only grabs a DHCP entry, it also creates the appropriate /etc/ntp.conf.dhcp file, HUP's NTP, and everything is... working again- after a fashion. It's not automatic. 

What I want, and what I expect:
My DHCP configured Ethernet interfaces should make use of configuration parameters from the DHCP server. I'm the DHCP admin here at the company and it works for about 30,000 other people- so it's only slightly embarrassing that the DHCP admin can't get a good DHCP configuration (with NTP, Netbios NS, &c., parameters)...
But I'd like to be able to do so reliably. I have modified my DNS servers in one of my DHCP configurations and that's good (okay, Spanish Inquisition time- problem 3!) as long as the DHCP client doesn't re-request, as when it does, I lose my customization in NM for DNS...

Anyway. I know NM has been a tough subject for a long time in Linux. Some of the troubles I'm having are problems in Debian too.

Any ideas?

---

### Post by jdos2 on 2009-11-24
Mrph. I'm thinking that this is related to the context that the DHCP client is running- as again, everything works when I run the client by hand.
Just not a good general solution.

---

