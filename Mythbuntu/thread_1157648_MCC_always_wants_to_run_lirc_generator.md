---
title: "MCC always wants to run lirc generator"
date: 2009-05-12
forum: Mythbuntu
---

### Post by oobe-feisty on 2009-05-12
i have my lirc setup the old way like only one lircrc file for everything and my own configs in /etc/lirc work but the ones lirc generator create dont work every time i change one or two things in mythbuntu-control-centre it seems to think its ok to overwrite my custom lirc settings even though it isnt.

this has been bugging me for a while and i dont think i should have to change the way i do things since i do things the way it has always been done and its mythbuntu that has changed .

what i suggest is a box you can check in MCC under lirc for people who know how to configure there remote and dont want to end up with unusable configurations they could simply check this box.

i.e check this box if you know how to setup lirc yourself and don't wish to use lirc generator since it doesn't know how you like to configure your remote and will most likely fail anyway.

---

### Post by superm1 on 2009-05-13
> **oobe-feisty said:**
> i have my lirc setup the old way like only one lircrc file for everything and my own configs in /etc/lirc work but the ones lirc generator create dont work every time i change one or two things in mythbuntu-control-centre it seems to think its ok to overwrite my custom lirc settings even though it isnt.

this has been bugging me for a while and i dont think i should have to change the way i do things since i do things the way it has always been done and its mythbuntu that has changed .

what i suggest is a box you can check in MCC under lirc for people who know how to configure there remote and dont want to end up with unusable configurations they could simply check this box.

i.e check this box if you know how to setup lirc yourself and don't wish to use lirc generator since it doesn't know how you like to configure your remote and will most likely fail anyway.
Can you please elaborate on the way you are doing things?  MCC has a check box to not overwrite settings when changing remotes.

It's only checked if it detects that you are missing a lircrc in your home directory.  I'd suspect you are doing something nonstandard (or perhaps standardish and we aren't detecting it :))

---

### Post by oobe-feisty on 2009-05-14
Thanks for your reply i suspect im doing somthing non standard to 

ls -l  .lirc*
lrwxrwxrwx 1 oobe oobe   25 2009-05-13 12:46 .lircrc -> /home/oobe/.mythtv/lircrc
-rw-r--r-- 1 oobe oobe  139 2009-05-13 12:50 .lircrc.old
-rw-r--r-- 1 oobe oobe  296 2009-05-04 03:35 .lircrc.old

also  /etc/lirc/hardware.conf points to a symlink

REMOTE_DEVICE="/dev/input/irremote"


this symlink is made using symlink rules in /etc/udev

it over writes configs in /etc then changes the paths in ~/ aswell

it must be how i do things as this isnt a common complaint

---

### Post by superm1 on 2009-05-14
> **oobe-feisty said:**
> Thanks for your reply i suspect im doing somthing non standard to 

ls -l  .lirc*
lrwxrwxrwx 1 oobe oobe   25 2009-05-13 12:46 .lircrc -> /home/oobe/.mythtv/lircrc
-rw-r--r-- 1 oobe oobe  139 2009-05-13 12:50 .lircrc.old
-rw-r--r-- 1 oobe oobe  296 2009-05-04 03:35 .lircrc.old

also  /etc/lirc/hardware.conf points to a symlink

REMOTE_DEVICE="/dev/input/irremote"


this symlink is made using symlink rules in /etc/udev

it over writes configs in /etc then changes the paths in ~/ aswell

it must be how i do things as this isnt a common complaint
Can you try to switch your symlink around?  So instead of putting the "real" lircrc file in /home/oobe/.mythtv/lircrc and the symlink in /home/oobe/.lircrc, put the real one in /home/oobe/.lircrc and the symlink in /home/oobe/.mythtv/lircrc

---

### Post by oobe-feisty on 2009-05-14
that didnt work but when testing i noticed if i uncheck generate dynamic mapping it doesnt want to regenerate lirc settings and i can modify other things with out overwriting things but when i start again it needs to be unchecked manually again

---

