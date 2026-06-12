---
title: "Need help- Load driver in SliTaz"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by imjscn on 2009-05-16
I installed SliTaz in Vmware, (added both Bridged and Nat). In SliTaz, after success in pppoe-setup, pppoe-start can't bring up the connection, pppoe-status says it can't read pppoe PID file var/run/pppoe.conf-pppoe.pid.pppoe. I checked the var/run folder, I don't see such a file.

Via google search, I got the instruction from SliTaz's handbook:
"On an installed system you just need to add the module_name to the variable LOAD_MODULES  in /etc/rcS.conf to load your module on each boot" 

In the rcs.conf file, I see that I already have a module loaded on boot:
LOAD_MODULES = "vfat nls_utf8 ohci_hcd intel_agp snd_ens1371" 
I guess this is the sound card driver.

Now, how can I add my network card in this file? Via "lspci", I got a list of drivers, but I don't know which one to add, and how? Here's a picture of the lspci result:

[IMG]http://lh6.ggpht.com/_YiW8RQGg9nU/Sg5QLoB5QHI/AAAAAAAAAlY/DAQA8g_42QU/s800/SliTaz-2009-05-16-12-58-36.jpg[/IMG] 

Please help!

---

### Post by john_spiral on 2009-05-31
give virtualbox a try, had no problems running Slitaz as a virtual machine with full network connectivity.

---

