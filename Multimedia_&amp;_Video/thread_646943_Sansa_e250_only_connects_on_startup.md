---
title: "Sansa e250 only connects on startup"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by plr4ever on 2007-12-21
I just got a new Sandisk Sansa e250, and i am having a problem with connecting it. If i leave it plugged in while the computer starts, it recognizes it and everything is fine (i.e. i can transfer/delete/modify files).

 However, if i plug in the sansa after i have booted up, it recognizes and connects for ~15 seconds before i get an "unsafe device remova" windowI have even installed rockbox, but it just restarts to the default firmware when plugged in. This is a MAJOR hassle because i have to restart my computer if i want to reconnect the player, and it makes testing out new files nearly impossible. Does anyone know what i can do to try this out? I restarted hal and dbus, but to no avail. I really might have to install a dual-boot windows if this doesnt start working.

---

### Post by tortsto on 2008-02-20
bump.

I get the same thing.  Running a dmesg gives me different messages everytime.  Often about scsi 7:0:0:1: rejecting I/O to dead device and then usb 4-1.3: reset high speed USB device using ehci_hcd and address 10.

Any tips?  I don't want to have to reboot my machine that's been running for like a week every time I just want to connect to my player.

---

### Post by tortsto on 2008-02-20
Actually, so it was Rhythmbox's autoplay feature which disconnecting it.  Go to System/Preferences/Removable Drives and Media

Under the Multimedia uncheck the Play music files when connected option.

Hope this solves other people's problems too.

---

### Post by tortsto on 2008-02-22
now I only get read access.  will try to figure out what's wrong. 

EDIT:
 I had a corrupted file on it.  Plugged it into a friend's PC, got rid of the bad file, and now works great.  I hope.

---

