---
title: "Network Manager"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by nunyez on 2009-01-23
Stupidly, I followed a tut over on [ubuntugeek]("http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html") last night that had me run:
```
sudo update-rc.d -f NetworkManager remove
```

Now my network applet says "Network Manager is not running..", I went to the synaptics repo but the frontend is installed still of course, and I don't know which command to get it working again is.

PS: i'm just setting the static ip with my router's dhcp + mac settings

---

### Post by tentotwo on 2009-01-23
If you are using Gnome, check to see if Network Manager is being loaded on Session startup. To do this, go to "System"/"Preferences"/"Sessions" and look for a Network Manager entry there.

If it is missing, create a new entry by clicking "Add" and entering "nm-applet --sm-disable" in the "Command" field.

If it is there but the Icon does not appear, check to see if you have a "Notification Area" in your panel. If in doubt, just right click on the panel, choose "Add to Panel", select "Notification Area" and click "Add").

Jake

---

