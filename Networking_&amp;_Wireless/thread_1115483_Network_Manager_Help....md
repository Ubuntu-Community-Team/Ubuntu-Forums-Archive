---
title: "Network Manager Help..."
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by Miroku419 on 2009-04-03
Ok, I just installed "wicd" which is another network manager.. but I didn't like it...  I want to go back to the old one that comes with Ubuntu, but I can't get it back.  I have the notification area shown and all.

:: After I installed wicd the ubuntu network manager stopped.  To get it to start, I tried using "ctrl + alt + backspace" but when it started back up, it didn't show up at all... ::

Please help if ya can... thanks

---

### Post by hobo on 2009-04-03
WICD removes network-manager when installed. If you have also removed Wicd then you can reinstall NM from your Ubuntu CD.

---

### Post by Miroku419 on 2009-04-03
> **hobo said:**
> WICD removes network-manager when installed. If you have also removed Wicd then you can reinstall NM from your Ubuntu CD.

Ok, thanks..  I didn't think it completely removed it - so i was wondering where it was.

---

### Post by hobo on 2009-04-03
> [I]Please note that this will remove network-manager, which is the default GNOME network manager and may cause loss of network connection temporarily. 
[/I]
The quote above is from the WICD site.

If you still have a connection to the net or the CD is added to your sources list:

sudo apt-get install network-manager

---

