---
title: "eth0 went away with Freescale 9.12 image for i.MX515 dev board"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by lmougen5 on 2010-03-16
<-- Newbie
 
With the Freescale 9.04 image, eth0 came configured on my board with mac address: 00:04:9F:01:06:DC.
 
Upgrading to the Freescale Karmic image, they call 9.12, replaced eth0 with eth2 and the mac changed to: 00:04:9F:00:F7:7F.
 
This thing only has a single nic so I would have thought there'd only be a single wired mac address. Using the Edit Connection dialog box I was able to add Auto eth0 with my desired mac address, and then set it as the only Auto-connect device to push it to the top of the list. Unfortunately this didn't result in getting it listed in the Available list to click on to initiate a connection.
 
Also using Devices - Network Tools only lists the eth2 device, even after adding eth0 (within the GUI).
 
I looked at various configuration files that other posts and google searches pointed to. 
 
Like:
/var/run/network/ifstate : lo=lo
/etc/network/interfaces : auto lo<cr>iface lo inet loopback
 
These look no different in the 9.04 configuration. So can someone point me to what script, file or other that I need to mod to get eth0 and my desired mac address back?
 
In case you're wondering I want to get back to the previous eth0 mac address configuration because that's what I was able to get I.T. to add to our local router to let me get the dev kit onto the net. Getting them to add another mac wouldn't be overly difficult but I'd rather figure this out.
 
Thanks in advance!

---

### Post by suseendran.rengabashyam on 2010-03-18
Hi,

Try the following steps in your Ubuntu Image

1) Open the file /etc/udev/rules.d/70-persistent-net.rules using your favorite editor.

2) Delete all the lines related to network interfaces, in my case it is

```
# PCI device .....
```
```
SUBSYSTEM=="net", ..
```.

Save and close the file.

3) Reboot your Ubuntu Image and check whether eth0 has come up properly with the correct MAC address.

Hope this helps.

---

### Post by lmougen5 on 2010-03-18
Below is the original file, purging it and rebooting resulted in it being populated with just the eth0 from below and noet eth1 or eth2.  What's weird is eth0 still has a different mac than what results from booting to the 9.04 image.  Devices - Network Tools now shows eth0, with the mac from below.  And Network Connections still shows what I added via the GUI and seems unaltered from what was done to 70-persistent-net.rules.  So it must be reading this information from somewhere else.  I tried hard-coding the desired mac address into this file and rebooting but that didn't work.  Instead it created another entry into the file and called the nic eth1.
 
Where can I find the 75-persistent-net-generator.rules file?
 
cat 70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.
# net device ()
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:04:9f:00:f7:3
d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# net device ()
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:04:9f:01:00:a
c", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# net device ()
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:04:9f:00:f7:7
f", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

---

### Post by suseendran.rengabashyam on 2010-03-19
Hi,

You can take a look at the following link

[http://ubuntuforums.org/showthread.php?t=668745](http://ubuntuforums.org/showthread.php?t=668745)

If you don't have /etc/udev/rules.d/75-persistent-net-generator.rules file, you can manually create it.

Hope this helps.

---

### Post by lmougen5 on 2010-04-15
FYI - mac was set as part of redboot for the dev board.  Issue solved through manipulating redboot.

---

