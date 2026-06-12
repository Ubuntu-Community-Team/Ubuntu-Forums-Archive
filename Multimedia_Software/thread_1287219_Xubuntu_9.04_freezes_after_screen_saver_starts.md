---
title: "Xubuntu 9.04 freezes after screen saver starts"
date: 2009-10-09
forum: Multimedia Software
---

### Post by falmeida on 2009-10-09
Hi.  Last weekend  I took my kids old desktop that was barely able to start with XP.  It is a Compaq Presario, Celeron 1.2 Ghz 512MB,RAM  video card, Dlink USB  wireless, and 2 HDD: 20GB with xubunt filesystem and a second 40 GB shared with gigolo  where I have my old XP files including my itunes library that now is available to be shared by every one at home.  Basically netbooks and laptops.   Everything is working fine.  Wireless, internet access,  print server, itunes, you can surf the web, use abiword, etc.  You name it. I revived the good old Compaq with Xubuntu.  The only problem I have is that when the machine is on for several hours and if the screen saver starts,  the screen freezes and   then it is impossible to unfreeze it.  Everything is working but I have to turn it off manually.  There is no way of getting back control of the mouse, keyboard and screen.  Any ideas?

---

### Post by rippin on 2009-10-09
> **falmeida said:**
> Hi.  Last weekend  I took my kids old desktop that was barely able to start with XP.  It is a Compaq Presario, Celeron 1.2 Ghz 512MB,RAM  video card, Dlink USB  wireless, and 2 HDD: 20GB with xubunt filesystem and a second 40 GB shared with gigolo  where I have my old XP files including my itunes library that now is available to be shared by every one at home.  Basically netbooks and laptops.   Everything is working fine.  Wireless, internet access,  print server, itunes, you can surf the web, use abiword, etc.  You name it. I revived the good old Compaq with Xubuntu.  The only problem I have is that when the machine is on for several hours and if the screen saver starts,  the screen freezes and   then it is impossible to unfreeze it.  Everything is working but I have to turn it off manually.  There is no way of getting back control of the mouse, keyboard and screen.  Any ideas?

Check screen saver settings for power management. Start by disabling all power management and add on from there. For gnome-power-preferences, only my display sleeps.

---

### Post by falmeida on 2009-10-11
Rippin.  Nothing happenned.  Power mngmt is out and still have the same problem.

---

### Post by rippin on 2009-10-12
> **falmeida said:**
> Rippin.  Nothing happenned.  Power mngmt is out and still have the same problem.

Thanks for testing that. Look in ~/.xsession-errors after a bad event - if possible before booting in another getty using 'cat'. Also, acpi can be a problem loaded or not - either way - depending on the computer. I've seen where it was a matter of re-seating RAM modules. This is a needle in the haystack scenario! 

What I see here is that, since you unloaded a user's power management to test, there's a system-wide setting/setup needing a look at.

Wish I knew more about your revived Compaq Presario's hardware. There may be a problem which can be researched on the web, one which has been solved, for your particular MODEL. I've found that on some mother boards, I have had to adjust the BIOS power settings to see stable results. We have a Compaq which is about 5 years old and having no problems, although it is on 8.04.

---

### Post by falmeida on 2009-10-13
Thanks for the information Rippin.  The Compaq I have is a Presario 5400 US with 512MB PC 133 SDRAM DIMs, 2 HDDs, 20GB for the file system and 40GB as a shared drive.  The chipset is Intel 815e.  I will check your suggestions over the weekend.  Everything else runs smoothly, everybody at home is happy with Xubuntu, no complains so far.

---

### Post by Van Isle on 2009-10-15
Hi! New user here, Xubuntu 9.04 on a 1.2Ghz w/256 mb RAM. I solved this problem not 2 days ago with a little research! Apparently there is no graphical way to disable this setting. So....

Open terminal.
to disable the lock on screensaver, type:

gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_use_screensaver_settings false

and hit enter.

To disable lock on blankscreen (i.e. after screensaver ends, or laptop lid closes) type:

gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_on_blank_screen false

and hit enter.


Make sure you note all the spaces, and underscore_ vs hyphen-. Also note for a laptop this seems to disable the screen off on close command, but since the screen saver runs for a bit, then powers off the screen after a bit anyways, it's not a problem for me. 

Let us know how it works for your setup.

VI

---

### Post by falmeida on 2009-11-02
Thanks

Worked perfectly.  The screensaver is disabled and the machine never freezes.

By the end of the year will upgrade to 9.10. 

I am now trying Xubuntu in a 4GB pendrive on my dell mini 12.  So far so good.  Will keep vista because of the document sharing but for couch surfing and personal use I will boot from the pendrive.

---

