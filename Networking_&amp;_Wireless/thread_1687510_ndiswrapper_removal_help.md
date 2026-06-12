---
title: "ndiswrapper removal help"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by adlin5000 on 2011-02-14
I have been having problems with my Netgear WG111v3 (RTL8187b) dropping out a lot and generaly having low singnal. 

To see if I could get a better signal I decided to try ndiswrapper. Got the latest driver from Netgear, used wine to install it to get the drivers. Used the GTK frontend, eveything seemed to be OK. Rebooted. 

Well now it won't turn on at all. The only way I could even find that it was being seen is lsusb. Nothing else even showed that it was there. 

So I decided to just go back to the way it was. Used the frontend to uninstall the driver and rebooted. Still nothing.

I'd like to just get it back to the way it was. At least it worked for the most part. Please let me know if I can give you any more info.

Thanks

---

### Post by ajgreeny on 2011-02-14
You don't need wine for ndiswrapper!

On the CD that came with the wireless adapter find the driver folder (at least that is what was on mine for a WG511 v2) and in that look for the WinXP subfolder.  Hopefully there will be a <file>.INF file in there somewhere.

Now in ubuntu run ndisgtk (System ->Administration ->Windows Wireless Drivers) and install the <file>.INF you just found.  It may be easier to copy the WinXP folder from the CD to your hard drive in order to do this.

---

### Post by adlin5000 on 2011-02-14
That would work great if I still had the cd. Unfortunately I don't. Now I'd really like to just get it back to normal without having to do a re-install.

---

### Post by ajgreeny on 2011-02-14
Have you tried just removing ndiswrapper and all the other ndis packages to see if that removes the current useless driver?

---

### Post by adlin5000 on 2011-02-14
Sorry. Forgot to put that in the OP. Yes I did. Did a complete removal of the ndiswrapper and GTK frontend, then reboot. Still nothing. 

It's almost like its just not turning on. lsusb shows it's there, but the light on it wont come on and nothing else shows it's there.

---

