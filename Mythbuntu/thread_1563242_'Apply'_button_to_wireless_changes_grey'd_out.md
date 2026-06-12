---
title: "'Apply' button to wireless changes grey'd out"
date: 2010-08-28
forum: Mythbuntu
---

### Post by wilma92010 on 2010-08-28
Hi There!

My Mythtv box is connected to my home network via a wireless connection.  For about a year, I connected via a static IP address, but don't remember how I did that exactly, except I just must have used the NetworkManager Applet (0.7.996 Mythbuntu 9.1) and configured it accordingly.

My old linksys router went out, so I bought a new Linksys e1000, which as near as I can tell is the nearest thing to my old WRG...    

My box connects wirelessly to the router via DHCP just great.   But, of course, I would prefer a static IP address, like before.

But whenever I use the pulldown to select 'Manual' for setting up my static IP, the 'Apply' button becomes grey'ed out and I cannot save the settings.   I don't think this is IP/Netmask arithmatic as I duplicated all settings from before.    I authenticate successfully to enter the Applet.   

Does anyone have any suggestions?

Thanks for any help.

Wilma

---

### Post by wilma92010 on 2010-08-28
I solved this myself.

I had to delete the DHCP version of the wireless entry, which was automatically populated when I connected to the SSID.   Once I deleted that entry and created a new entry, things seemed to work (though I thought I did that originally!).

Hope this helps someone.

Wilma

---

