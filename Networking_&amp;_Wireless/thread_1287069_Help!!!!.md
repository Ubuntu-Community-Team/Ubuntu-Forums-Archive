---
title: "Help!!!!"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by ieruiz on 2009-10-09
All,

Wireless in Ubuntu works ok to my router on an HP pavilion 9225.  

But hard wired lan DOESN'T.   It doesn't seem to pick up the connection when I attach a cable or detach it (not plug and play like windows).

What do I need to do to get it to recognize and connect on a hardwired connection to my router???

Ubuntu 8.04...

Isaac

---

### Post by gdonwallace on 2009-10-09
Check the gnome-network manager and make sure that it is setup for wired connection instead of wireless.  It always defaults to the last good connection.  

If your last connect was through the wireless, then you need to switch it to wired.  That should fix your problem,

---

### Post by cameronedwards on 2009-10-09
Try clicking "System/Administration/Hardware Drivers" and there may be a lan driver or something similar that has not been installed yet.

but make sure you read the description (as some should only be activated if its update isn't working -screanshot provided)

---

### Post by ieruiz on 2009-10-09
I'm a total noob with regard to UBUNTU but I know windows real well (for better or worse).

Don't know what gnome is.  Only know SYSTEM....ADMINISTRATION....Network (or Network Tools).  Any of those = Gnome??

Isaac

---

### Post by cameronedwards on 2009-10-09
> **ieruiz said:**
> 
Only know SYSTEM....ADMINISTRATION....Network (or Network Tools). 
Isaac

if you cant find Hardware drivers right click on the menus (applications places or system anyone) and click "edit menus" 
then enable the thing on the screenshot. (im a noob too i have no idea what half these things are called) and make sure the highlighted menu oppotion is ticked.

---

### Post by ieruiz on 2009-10-09
When I click SYSTEM/ADMINISTRATION/HARDWARE drivers it lists my wireless net card, and my graphics card.  How do I tell it to go find my LAN card drivers?

---

### Post by cameronedwards on 2009-10-09
> **ieruiz said:**
> When I click SYSTEM/ADMINISTRATION/HARDWARE drivers it lists my wireless net card, and my graphics card.  How do I tell it to go find my LAN card drivers?

crud I have no idea sorry.
(like i said "im a noob" that was my only idea)
ok maybe send me your specs and i might be able to figure something out.

---

### Post by ieruiz on 2009-10-09
I LOVE it - the blind leading the blind - often more effective than the seeing leading the seeing!

I'll give it a shot.  Stay tuned.  I appreciate the help.  

Isaac

---

### Post by PrePenguin on 2009-10-09
If you have a onboard lan card you must enable/disable it via the bios or the wireless and lan will conflict. So adjust accordingly on which method you choose to use to connect to internet.

---

