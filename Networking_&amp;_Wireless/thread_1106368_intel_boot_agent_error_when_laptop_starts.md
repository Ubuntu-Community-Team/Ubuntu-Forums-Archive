---
title: "intel boot agent error when laptop starts"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2009-03-25
has anyone an idea why this happens?

intel pro 1000 PL built-in LAN card in laptop
I get
"PXE-E04 Error reading PCI configuration space"
"PXE-Eo5 lan adapter's configuration is corrupted, something, cannot continue." Then the screen switches to say
"No operating system installed"

Then if I press cntrl-alt-delete, it will boot winXP.

this is duo core Tecra A7 toshiba laptop.
This does not happen every time. Also if the built-in LAN is disabled , the boot is always ok.
The LAN is at the bottom of the boot order list in the bios settings.

ALSO, I was occasionally experiencing a weird hang every second while in XP.
everything would stop, mouse etc... sound would go blurpppp. Only fix was a reboot.

All of this is related to the intel pro 1000 PL LAN card. I upgraded the pro1000 pl driver to the latest intel driver from their site (2008).
And now no weird hangs every second.

Also, the laptop was shutting the LAN card off afte a few minutes, even while plugged into AC power, the little icon would say disconnected, right while using the internet. Only way to re-enable was to reboot

I unchecked the "allow laptop to turn off card to save power" found in the system properties for the device. Now it stays on.

The only continuing problem seems to be the PXE errors on boot up.

---

