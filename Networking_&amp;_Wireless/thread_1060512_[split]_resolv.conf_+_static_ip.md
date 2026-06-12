---
title: "[split] resolv.conf + static ip"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2009-02-04
I am working on a static ip. I see now that its not the resolv.conf for me.

my file looks like this


...

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

# The primary network interface , all the 3rd level "1" were "0"
auto eth0
iface eth0 inet static

address 192.168.1.120
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 68.94.156.1 68.94.157.1

....



As far as i can tell lines 1-4 are correct. I can get to Google if i enter the ip

Is there an issue with line 5?

---

### Post by jpeddicord on 2009-02-04
Split your post into its own thread as it was a bit offtopic.

---

### Post by Iowan on 2009-02-04
As far as I know, Network Manager still has problems with static addresses.  [Here]("http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html") is a How-To for Intrepid static IP address.  There's also a [workaround]("http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html"). A final option is to un-install NM and install the old manager - [here]("http://ubuntuforums.org/showpost.php?p=6623406&postcount=10").

---

### Post by wlraider70 on 2009-02-05
A final option is to un-install NM and install the old manager - here. 

that did it, thanks

---

