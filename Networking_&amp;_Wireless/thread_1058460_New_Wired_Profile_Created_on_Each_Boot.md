---
title: "New Wired Profile Created on Each Boot?"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by igfud on 2009-02-02
Hi,

I have a desktop here connected via Ethernet to a campus network.  Each time it boots, the wired connection profile is removed and a new profile is created.  Each profile has a new MAC address, and each profile is named consecutively (eth0, eth1....).

I guess normally this wouldn't be too much of a problem, but the campus network requires all MAC addresses to be registered.  I can't think of any reason why the profile would be destroyed and recreated each time, and with a new MAC addresses.  The Network Manager only shows the latest of the profiles on each boot.

What might be causing this?  The MAC address should be static as it is unique to the NIC, but for some reason it appears that the machine is spoofing it.

I should also add this is a fresh Ubuntu installation.

Thanks,
igfud

---

### Post by teethlikelions on 2009-02-02
This may have something to do with the Network Manager in Intrepid.
Consider, for instance, that all static iface configs are lost on reboot.
Try making your own /etc/network/interfaces file and disabling NM?
I can't explain the "spoofed" MAC address, though.

---

