---
title: "Airlive RT2870 Chipset wireless won't start at boot"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by Westedge on 2009-05-07
Hi guys,

I've managed to compile the module for my RT2870 USB wireless adapter and configured the RT2870.dat config file. The driver works fine when loaded via insmod command. How do I get this driver to load at boot? Do I need to copy the rt2870sta.ko module to a specific directory? Any help would be much appeciated. OS is ubuntu 9.04

---

### Post by Ultracrat on 2009-05-07
> **Westedge said:**
> Hi guys,

I've managed to compile the module for my RT2870 USB wireless adapter and configured the RT2870.dat config file. The driver works fine when loaded via insmod command. How do I get this driver to load at boot? Do I need to copy the rt2870sta.ko module to a specific directory? Any help would be much appeciated. OS is ubuntu 9.04

I just went through this myself. :)  I assume you used the source package from the Ralink website?  After you do the "make" command to build the module:

[LIST=1]
[*] Run "**make install**" from the same directory you ran "**make**".  This should run a few commands, including one to copy the module into the right place (should be in the directory **/lib/modules/`uname -r`/kernel/drivers/net/wireless**).

[*] Add the line "rt2870sta" to the file **/etc/modules** with the editor of your choice.  This file tells the system which modules to load at startup.

[*] Go to the directory **/lib/modules/`uname -r`/kernel/drivers/staging/rt2870** and rename the rt2870sta.ko file there to "rt2870sta.ko.disabled".  Actually, renaming it to just about anything different should do.  Ubuntu ships with an rt2870 driver, but it didn't work for my adapter (EDIMAX EW-7717Un).  If you don't rename or remove this file, the system will load this driver instead of the one you installed.  (Figuring this step out took me a few days...)
[/LIST]

Or if you like to live dangerously, these commands should do the job (I haven't tested them so use them at your own risk, but they should be close):

[B]make install
sudo echo "rt2870sta" >> /etc/modules
cd /lib/modules/`uname -r`/kernel/drivers/staging/rt2870
sudo mv rt2870sta.ko rt2870sta.ko.disabled
sudo modprobe rt2870sta[/B]


And that should be it.  I'd reboot at this point to make sure it works.

Hope that helps.

- Keith

---

