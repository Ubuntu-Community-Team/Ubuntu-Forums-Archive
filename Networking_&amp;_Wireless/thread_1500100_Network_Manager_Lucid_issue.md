---
title: "Network Manager Lucid issue"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by yeleek on 2010-06-02
Hi,

Been a long term user of Karmic on a machine using a P55M-UD2 motherboard (on board Realtek PCIe GBE Family Controller).

Formatted and installed Lucid about 2-3 weeks ago, no issues.  Did an update I think last week, since then had issues with network manager failing to connect my eth0 properly.  When going into network manager it shows the old connection i was using but isn't actually connected properly to the interface.

Ifconfig shows the interface is there, but has no ipaddress.  Try to use sudo dhclient, and that fails to get a dhcp address.  Restart the machine after its been in ubuntu, into windows (dual booting) and network card doesn't work there either.  

**However**, power off machine all together and start windows, network card detected fine (multiple reboots), again power machine off all together and boot a Karmic cd.  Network card works fine...

Any ideas please?

---

### Post by Iowan on 2010-06-02
I realize this is probably trivial, but right-click Network Manager icon and verify Enable Networking is checked. A few threads have been solved by discovering that an update "turned off" networking.

---

### Post by yeleek on 2010-06-03
Hi,

Yeah enable networking is ticked.

What surprises/confuses me, is why would running ubuntu and then restarting into windows disable the nic?  Yet power off and then straight into windows and only then reboot into windows and nic works fine?

Any ideas?

THanks

---

### Post by Iowan on 2010-06-03
A rehash from another thread:
I've seen a few threads where rebooting from one OS to another leaves the drivers active (apparently OS reboots faster than drivers can reset). Most of them worked OK if machine was powered completely down first...

---

### Post by yeleek on 2010-06-04
FYI - Blew away / and reinstall 10.04, and networking is back, fully updated.  Very odd.

Thanks anyway.

---

