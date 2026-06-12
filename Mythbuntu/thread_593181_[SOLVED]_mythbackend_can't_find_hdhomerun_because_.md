---
title: "[SOLVED] mythbackend can't find hdhomerun because network is not initialized yet"
date: 2007-10-26
forum: Mythbuntu
---

### Post by the Goat on 2007-10-26
I installed a fresh copy of mythbuntu on a new backend setup.  The biggest problem I've found is that mythbackend runs before the network has been initialized.  This means that mythbackend can't connect with my hdhomerun tuners.  Is there an easy workaround for this problem?

---

### Post by superm1 on 2007-10-27
Yes there is.

Close mythfrontend and click on the network icon in the system tray.  Choose manual configuration.  From the dialog that comes up, turn off "roaming" mode.  Setup DHCP in that dialog, and then reboot.

---

### Post by the Goat on 2007-10-27
Thanks that fixed the problem.

---

