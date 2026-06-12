---
title: "Networking icon misbehaving after HD recovery with ddrescue and BIOS update"
date: 2013-08-04
forum: Networking &amp; Wireless
---

### Post by siersmak on 2013-08-04
Hello,

I just performed a BIOS update on my Sony VAIO laptop (running Ubuntu 11.10) as part of recovering the SSD RAID after one of the physical disks failed.  I used ddrescue to put the linux image(s) that I had ddrescue'd back onto the drive, and was able to boot back into linux with most everything functioning as it did before the drive failed.  The only thing I've noticed so far is that the networking icon in the upper right of the GNOME desktop gets initialized to both Networking and Wireless disabled, even though they are both enabled and I'm connected to my wifi network - I'm typing this post on the laptop, in fact, even though the icon indicates that I'm not connected.  ifconfig reports that wlan0 is up and running.  I've tried enabling both Networking and Wireless in the icon's pulldown menu, and I remain connected but the icon doesn't change.  The icon pulldown menu doesn't include the list of wireless networks available, either.  I've tried plugging in a network cable, and indeed I get a connection through eth0, according to ifconfig.  I've noticed that if I switch the Wireless button on the case of the laptop to off, then wlan0 goes down (of course...)

Quick googling appears to indicate that the BIOS update could have confused the networking icon.

I'm not the primary user of this laptop, and I would like to get the networking icon back to working the way it did before the BIOS update so that if the laptop is brought to a new wifi network the user can get it on that network the way she always has in the past - by selecting the network in the icon's pulldown menu.

I'd prefer to not reinstall or upgrade Ubuntu, if it can be avoided.

Any help anyone can offer will be appreciated.

-Ken

---

### Post by siersmak on 2013-08-05
A bit more info:  I removed network-manager and network-manager-gnome, and then installed wicd, wicd-daemon, python-wicd, and wicd-gtk.  WICD works similarly to how network-manager-gnome used to work before the BIOS update - I'm able to scan for networks and connect to the one I want, so that's great.  I do prefer the appearance of network-manager-gnome, so I'd still like to get it working again, if anyone has any ideas.

Thanks

---

