---
title: "System clone with different NIC"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by mwilson75 on 2010-11-04
I need to clone a system to a flash drive and boot it on another PC. The other PC doesn't the same type of ethernet card. For obvious reasons the network on system #2 fails.
 
I heard Ubuntu saves the MAC address of existing network cards somewhere. If that's true how do I change it for system #2?... and how can I install both sets of drivers (2 different ethernet cards) on both systems where one does not exist on the other??
 
The system is Ubuntu 10.04.1

---

### Post by gzarkadas on 2010-11-08
Ethernet cards are well supported in the kernel (and it ships with all drivers compiled in, with the exception of either very old or very new hardware). So the failure isn't that obvious; before starting to search for MAC addresses and such low-level stuff, first travel this check-list:

1. Does the second card works with a live cd ?[INDENT]Yes: It is supported
No: It is not supported, so first make it work from a base-install.
[/INDENT]2. Does the cloned usb flash works in the original system ? Boot your first (source) PC with the flash drive and verify cloning is ok.[INDENT]Yes, everything is ok: Cloning is made right.
No: Cloning did not completed successfully; investigate the cause.
[/INDENT]3. Does your source kernel is a stock one or a self-compiled one?[INDENT]Stock: Ethernet drivers are probably there.
Compiled: Check the kernel config for omitted network drivers.
[/INDENT]4. Does your source system has a dynamic network configuration (the default) with network-manager or a static, customised one?[INDENT]Dynamic: Your ethernet card should be recognised automatically.
Customised: You will have to update it for the second system or change to dynamic.
[/INDENT]5. Do the networks attached to PC #1 and #2 are of the same type, or have differences that may inhibit networking without additional setup (such as for example lacking dhcp in #2 network)?[INDENT]Yes: No need to act.
No: Do the necessary configuration to either the network or the usb flash filesystem, so that it can work in PC #2 - it is not a hardware / driver (card) problem.
[/INDENT]Now, if the answer to Q 1-3 are: Yes,Yes,Stock,Dynamic,Yes (or have resolved the issues if different), and the problem persists, then investigate (in the destination, #2, PC):

-- What is the output of `sudo ifconfig' ?
-- What is the output of `sudo lshw | grep UNCLAIMED' ? (this will catch hardware without a driver loaded)
-- What is the brand and model of the network card ?
-- What do your logs say about the network card ? Open the "Log Viewer" application (from System|Administration menu), goto the `syslog' line of the list to the left and scroll down to bottom the right pane; then start reading upwards untill you find entries related to your networking.
-- Does a `sudo service network-manager restart' solves the problem ?

Finally, if you still can't find what the problem is, post your findings back here.

---

