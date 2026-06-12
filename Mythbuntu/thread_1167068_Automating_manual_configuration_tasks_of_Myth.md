---
title: "Automating manual configuration tasks of Myth?"
date: 2009-05-22
forum: Mythbuntu
---

### Post by lightning9 on 2009-05-22
Hello all,

Does myth use databases or config files to store the various custom configuration parameters?

Every time I install myth, I manually make these personal customizations via the setup menus:

Setup -> General screens
- set passthrough device to ALSA:iec958
- enable spdif passthrough checkboxes for AC3 and DTS
- set exit menu options to "quit, reboot and shutdown"
- change halt command from "halt" (which doesn't work) to "/usr/share/mythtv/myth-halt.sh"

Setup -> Appearance screens
- select mythbuntu wide skin
- cache 10 skins
- set menu theme to classic

Setup -> Adjust Screen Size
- Adjust my screen size for HDMI

Setup -> Video -> General
- uncheck "show unknown file types"
- check "video list browses files"

Setup -> Video -> File Types
- create file types: mkv, ts, wmv, mp4

Are these values store in a database or the std linux text based config files?
If database, is there documentation showing how to modify the desired tables/fields programmatically?
If text based config files, where are they?

Any help is greatly appreciated!

Thanks,
lightning9

---

### Post by ian dobson on 2009-05-22
Hi,

Have a look in the settings table. Almost everything is stored in the table apart from the "few" parameters required to access the backend server/SQL database.

The table has Hostname,Date and Value fields.

I don't think there's any documentation on these values but you can change them using a simple SQL insert using whatever language you like.

Regards
Ian Dobson

---

### Post by lightning9 on 2009-05-22
Thank you, ian!

Found everything I needed in the settings and videotypes tables. Now all my custom values are set via mysql commands from a bash script and a small set of sql statements. 

Very cool!

---

