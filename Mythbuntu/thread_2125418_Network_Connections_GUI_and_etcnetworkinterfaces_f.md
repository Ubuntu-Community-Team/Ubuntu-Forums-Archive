---
title: "Network Connections GUI and /etc/network/interfaces file"
date: 2013-03-13
forum: Mythbuntu
---

### Post by neutron68 on 2013-03-13
When I set up my Mythbuntu boxes, I set to them to static IP addresses so I can SSH, VNC into them, etc.
I usually manually edit the /etc/network/interfaces file to accomplish this.

I'm doing a new load of Mythbuntu 12.04.2 and decided to experiment with the Network Connections GUI in the Settings section of the GUI.
In the IPv4 tab, I set the Method to Manual, and proceeded to set the static IP Address, Netmask, Gateway and DNS Servers boxes.

When I typed an ifconfig command in a terminal window, the new static IP address was shown.

Then, I went and looked at the /etc/network/interfaces file - NO SIGN of the static IP address lines that I would have entered manually!!

So, does the fact that the Network Connections GUI does not edit the /etc/network/interfaces file for you a problem?
Where is the static IP info stored if not in the /etc/network/interfaces file?

Eric

---

### Post by papibe on 2013-03-13
Hi neutron68.

When the network-manager package is installed, it takes over the network settings and administration. Then the file /etc/network/interfaces becomes less relevant.

The relevant files for NetworkManager are distributed in several directories:
```
/etc/NetworkManager
/var/run
/var/lib/NetworkManager
```
The details you are looking for should be in this file (or similar name):
```
/etc/NetworkManager/system-connections/Auto eth0
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by neutron68 on 2013-03-13
You're right, the info is stored in the /etc/NetworkManager/system-connections/ folder.

But, on my freshly loaded system, its in a file called "Wired connecton 1"

I have to admit, I kinda liked knowing where it was and how to easily edit it.  Having the files "hidden" off in a new place feels more like Windows, where you don't know where system settings are really stored!  

Eric

---

