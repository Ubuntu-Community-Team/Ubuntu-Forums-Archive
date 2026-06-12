---
title: "Myth Frontend Question"
date: 2016-02-09
forum: Mythbuntu
---

### Post by jimiz on 2016-02-09
I hope this has not been posted prior.  I am looking to have my mythbuntu system start directly into Kodi. Currently it is starting mythfrontend. Trying to figure out where this activity is done


Any Help would be appreciated.

---

### Post by MoebusNet on 2016-02-10
I don't use Kodi, but my Mythbuntu 14.04 w/ mythtv version 0.27 has Mythfrontend autostart by default. You can change that by closing Mythfrontend (press 'Esc'>''Do you really want to close MythTV?'>'Yes, exit now') then from the desktop 'Applications>System>Mythbuntu Control Center>Startup Behavior' uncheck the box for 'Automatically start Mythfrontend.

Now you would have to select Mythfrontend from the Applications menu to get it to start after booting up. You'll have to ask someone else how to get Kodi to autostart on boot.

Hope this helps!

---

### Post by aelfric55 on 2016-02-10
In the xfce desktop, in the settings menu there should be a menu item for session startup. Commands and apps to execute automatically when the desktop comes up should be placed there.

---

### Post by jimiz on 2016-02-10
MoebusNet - Thank you.  I ended up doing just that.  Set Kodi as the starting application insetad of Mythfrontend.  I used the command "kodi -fs" to start it in full screen mode.

Thanks again.

---

