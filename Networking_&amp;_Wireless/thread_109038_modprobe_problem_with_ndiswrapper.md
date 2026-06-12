---
title: "modprobe problem with ndiswrapper"
date: 2005-12-27
forum: Networking &amp; Wireless
---

### Post by Krash1201 on 2005-12-27
just finished installing breezy on my desktop, and after what appeared to be a successful install of the windows drivers through ndiswrapper for my wifi card, i restarted, and the boot locked at loading modules.

the wifi card is an airlink101 awlh3026, there are some existing issues with the driver for this wifi card, but it shouldn't cause problems with the modules.  is there any way i can edit /etc/modules to prevent this problem prior to boot?  thanks.

---

### Post by Nomearod on 2005-12-27
I don't know much about it, but i installed my card this way:

- Install Ndiswrapper and the gui
- Go to System -> Admistration and open " Windows Wireless Drivers" There, install yours XP driver ( in my case it was "lsbcmnds.inf" )
-Restart PC
-Go to System- Administration and open the program to configure the net connections.
-Configure yours wireless card and it should work

You can also try in a terminal this:

sudo modprobe ndiswrapper
sudo echo ndiswrapper /etc/modules/

But i don't know much about this... sorry

---

### Post by Krash1201 on 2005-12-27
right now i can't even get into kubuntu.  i restarted in recovery mode and it stopped at loadndiswrapper failed, followed by ts:  Compaq touchscreen protocol output.  any ideas?

---

### Post by Nomearod on 2005-12-27
Don't know... Maybe install Ubuntu again and try install ndiswrapper with synaptic.

---

### Post by Krash1201 on 2005-12-27
thanks for the replies, i used knoppix to rewrite the modules file and take out what i added, going to unistall the drivers i installed with ndiswrapper and try the gui install.  thanks again.

---

### Post by az on 2005-12-27
Had you installed a windows driver (inf file?)

You could have deleted the /etc/ndiswrapper directory (which would remove installed windows drivers) to see if that is the culprit.   You need to always use the most recent INF file with ndiswrapper - the one that came with your card (or the one that worked with an older version of ndiswrapper) may not work.  They always use the newest driver for development.

---

