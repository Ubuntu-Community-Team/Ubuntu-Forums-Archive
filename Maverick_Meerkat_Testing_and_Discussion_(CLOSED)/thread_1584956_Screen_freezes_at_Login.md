---
title: "Screen freezes at Login"
date: 2010-09-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by santana007 on 2010-09-29
I recently upgraded from Lucid to the latest beta of Maverick. Everything went fine. Today, Update Manager came on with *updates are available*. Started update, went OK until "Applying Changes" stopped at about 3/4 of way through. The Indicator Applet Session Icon went [COLOR=Red]RED[/COLOR]   showing Restart required to complete updates. Restarted but stops at   login screen but no login available. Have coloured background with white   rectangle in centre with the name I gave to computer (touchubuntu) and   white bar at bottom with current date and time. Mouse cursor is frozen   and keyboard doesn't work. Must do a manual reset. Recovery selection   and previous kernels do not work. Recovery halts part way through.  Would  like to recover Home folder, emails and Firefox Bookmarks. Tried  Live  CD but  Home folder has a X on it, says do not have necessary   permissions to view contents of file. Is there anyway to fix the Login   situation or recover Home folder, etc?

---

### Post by NightwishFan on 2010-09-29
Hold shift while booting and go into recovery mode. Choose root prompt with networking. Run this command:
```
sudo apt-get -f install
```

After it is done, type:
```
sudo reboot now
```

Boot up normally and see if it works.

---

### Post by santana007 on 2010-10-01
> **NightwishFan said:**
> Hold shift while booting and go into recovery mode. Choose root prompt with networking. Run this command:
```
sudo apt-get -f install
```After it is done, type:
```
sudo reboot now
```Boot up normally and see if it works.

Thank you but unfortunately your suggestion doesn't work. Cannot start recovery this way. I dual boot with XP so it goes to the Grub menu. If I select the recovery option from there, it starts but stops part way through. I found a way however using a Live CD and Terminal to open the Home folder. You can see it here:```
http://ubuntuforums.org/showthread.php?t=1584931
```

---

