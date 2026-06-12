---
title: "Networkmanager dead?"
date: 2010-05-17
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Reiger on 2010-05-17
Is it just me or did network-manager(-kde) die over the past night:

Hibernate a fully functional networked maverick. 
On wakeup: the OS decides to reboot instead.

On that first reboot I get an fsck but nothing at all onerous I'd say. On log in: network manager says that it's been disabled. Rubbish, says I:  checking iwconfig/ifconfig reveals my wired & wireless network devices are down. Odd, they should be definitely _up_.
Reboot: not fixed. Plug in an ethernet cable: no luck.
Boot with an ethernet cable attached to a rootprompt with networking (from the recovery options) I am able to update the system.
Reboot normally with ethernet cable attached: I have internet.
Reboot without the ethernet cable attached: network manager is off to play games again.
Try a few radio rfkill switches: dmesg | tail reveals that these register with the appropriate power management hook (and I get a warning about unknown key being pressed) but network manager doesn't notice anything.
Reinstalling network-manager & network-manager-kde from the rootprompt with networking doesn't fix it either.

Give up and install wicd-gtk from the rootprompt with networking (after plugging in the ethernet cable again) -- everything is fixed now.

Any ideas?

---

### Post by ranch hand on 2010-05-17
I would have filed a bug before installing wicd-gtk.  That way the information would be from the correct configuration for your box.

---

### Post by explemonk on 2010-05-18
This happened to me on my Arch Linux machine a few days ago, and I found the solution here: [http://bbs.archlinux.org/viewtopic.php?pid=728494](http://bbs.archlinux.org/viewtopic.php?pid=728494)

Basically you need to stop NetworkManager, delete /var/lib/NetworkManager/NetworkManager.state (or whatever the Ubuntu location is) and restart NetworkManager.

---

### Post by jppr on 2010-05-18
i had the same defect. take the moment the modem off and all the cables  with out. Network manager isn´t dead = ) after that internet works again :popcorn:

---

### Post by Reiger on 2010-05-18
> **explemonk said:**
> This happened to me on my Arch Linux machine a few days ago, and I found the solution here: [http://bbs.archlinux.org/viewtopic.php?pid=728494](http://bbs.archlinux.org/viewtopic.php?pid=728494)

Basically you need to stop NetworkManager, delete /var/lib/NetworkManager/NetworkManager.state (or whatever the Ubuntu location is) and restart NetworkManager.

Thanks: that did the trick. Removed the file, reinstalled network-manager-(kde) and purged wicd and its gtk/cairo dependencies.

---

