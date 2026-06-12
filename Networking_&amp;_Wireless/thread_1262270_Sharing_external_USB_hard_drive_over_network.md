---
title: "Sharing external USB hard drive over network"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by allanlewis on 2009-09-09
I have an old laptop running Ubuntu Netbook Remix 9.04 and several PCs variously running Windows XP, Windows Vista (unfortunately) and Ubuntu/Xubuntu Jaunty. My laptop is currently acting as a server (primarily for MythTV - it isn't that old!) but I intend to build a basic server/HTPC in the near future to replace this.

I'd like to share an old USB hard drive over the network, primarily as storage for MythTV recordings, but also for backup purposes. However, I occasionally need to move my laptop and would like to be able to remove the USB hard drive safely without having to check if any clients are using it over the network. Is this possible? Or is there always the risk that I will unplug the drive while one or more clients are using it?

I'd be willing to have a script (perhaps assigned to one of the laptop's shortcut buttons) that disconnects the hard drive safely, but I don't want to have to manually check if any clients are using the drive. Would the standard "safely remove device" (sorry for the Windows terminology) applet suffice for this purpose?

Any help with how to do this sensibly and safely would be greatly appreciated.

---

### Post by AliTabuger7 on 2009-09-09
I think you should just be able to unmount ```
umount <drivename>
``` it. I don't think it'll let you unmount if it is being used.

There should also be a button in the left panel in nautilus (file browser in ubuntu).



If that doesn't work, I'm sure you could have it simply based on network usage. You could do it yourself and just watch the network usage using the system monitor panel applet.

---

