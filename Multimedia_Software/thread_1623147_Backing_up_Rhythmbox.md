---
title: "Backing up Rhythmbox"
date: 2010-11-16
forum: Multimedia Software
---

### Post by tonsil on 2010-11-16
I've been using Linux Mint 9 (Ubuntu-based) for some time and I've installed Ubuntu 10.10 elsewhere. I'd like to backup and move all my radio stations on Rhythmbox so I don't have to manually enter them one by one. How do I do that?

I wish Rhythmbox had 'Backup / Restore settings" à la Evolution.

---

### Post by ajgreeny on 2010-11-16
There are hidden folders in your home in the folders **.cache, .gconf/apps, .gnome2** and finally **.local/share**.

Just copy those rhythmbox folders to your new install in the same places before opening rhythmbox on the new machine, and most, if not all the configuration should be carried across.

---

### Post by pricetech on 2010-11-16
Do back up the original files before overwriting just in case.

---

### Post by ajgreeny on 2010-11-16
> **pricetech said:**
> Do back up the original files before overwriting just in case.
If you have not opened rhythmbox in the new install I don't think those files and folders will exist, but if they do, pricetech's comment is correct.

---

### Post by tonsil on 2010-11-16
> **ajgreeny said:**
> If you have not opened rhythmbox in the new install I don't think those files and folders will exist, but if they do, pricetech's comment is correct.

True, they didn't. I did not find any files related to Rhythmbox in .gnome2 either (in linuxmint 9), so I just copied the rest. It worked perfectly fine. Only the radio stations got merged with my stations and with what comes by default, so I had to delete those I did not want. Now everything is OK. I still wish the developers would consider a Backup/Restore option though.

Thank you so much! :)

---

