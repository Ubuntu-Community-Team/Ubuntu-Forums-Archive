---
title: "[SOLVED] DVD won't play after installing new DVD drive"
date: 2008-08-09
forum: Mythbuntu
---

### Post by dmdbdd on 2008-08-09
Good morning:
 
 Mythbuntu 8.04.1
 
 I replaced my CD player with a Sony DRU840A EIDE DVD drive. Can't play a DVD from the MythTV Play Video menu - it seems to recognize the drive, as when I click on 'Play DVD' the screen goes blank for a couple of seconds, and then returns to the menu. I can play a music CD with no problems.
 
I Enable Medybuntu Propietary Codec Support and the libdvdcss2 codec.

I also tried xine - no go.

 Do I need to reinstall Mythbuntu or should the OS recognize new hardware and install it automatically? Or is there a way to manually install new hardware.
 
 Regards,
 
 dmdbdd

---

### Post by tgm4883 on 2008-08-09
most likely mythfrontend isn't looking in the right spot for your dvd drive.  There should be a setting in mythfrontend under media settings for this.

---

### Post by AlecJ on 2008-08-09
There is a setting in the front end, but only if your calling mplayer or xine, vlc etc, the standard "internal" relies on the os setting.
I think I would be looking in the modprode area, as the new drive will have a new name and address.

---

### Post by dmdbdd on 2008-08-16
Good afternoon:

Thanks to all who tried to help :) The answer is, do a reinstall - it seems that linux isn't very good about detecting and configuring new hardware. Sometimes it does and sometimes it doesn't :( I guess if I were a Linux guru, there would be a way to manually get this sucker installed, but I'm not. So a reinstalled solved the problem.

Regards,

dmdbdd

---

