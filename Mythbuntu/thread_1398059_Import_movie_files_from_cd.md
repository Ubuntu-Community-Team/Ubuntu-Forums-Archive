---
title: "Import movie files from cd"
date: 2010-02-04
forum: Mythbuntu
---

### Post by unkle1 on 2010-02-04
Hello,

Ive got lots of movie-clips stored on cd-rom that i would like to import to mythvideo.

Is there a way to do it by loading a cd-rom in the tray and then somehow navigate the files choosing which to copy via mythtv ?

Mythmusic sees nothing other than music (of course) when choosing import files and searching the cd-rom.
Mythvideo doesnt seem to have an option for this sort of ripping (some extra plugin needed ?).

Upon loading the tray Mythtv presents the Gallery with the files on the cd-rom but choosing "M"-->"File menu" makes it exit immediately to "Home"-screen.

Mythbuntu 9.10 (extra repos and PPA enabled)

Regards,
Dan

---

### Post by nickrout on 2010-02-04
> **unkle1 said:**
> Hello,

Ive got lots of movie-clips stored on cd-rom that i would like to import to mythvideo.

Is there a way to do it by loading a cd-rom in the tray and then somehow navigate the files choosing which to copy via mythtv ?

Mythmusic sees nothing other than music (of course) when choosing import files and searching the cd-rom.
Mythvideo doesnt seem to have an option for this sort of ripping (some extra plugin needed ?).

Upon loading the tray Mythtv presents the Gallery with the files on the cd-rom but choosing "M"-->"File menu" makes it exit immediately to "Home"-screen.

Mythbuntu 9.10 (extra repos and PPA enabled)

Regards,
Dan

ssh in from another computer and simply use the cp (copy) command to copy them from the cdrom (typically mounted at /media/cdrom/) and your videos directory (/var/lib/mythtv/videos/ )

---

### Post by unkle1 on 2010-02-04
Thanks :)
I already do that though, even made me a script for ripping * from the cds (just cant figure out how to get bash to wait and detect a "cd-inserted").

The goal is to be able to do it all from the TV/remote
Maybe there just isnt any way to do this from the frontend ? Im hoping I just missed the option somewhere.

---

### Post by nickrout on 2010-02-04
Connect your script to a menu item.

---

### Post by unkle1 on 2010-02-06
Thanks, thats a great idea. I did consider it, but thought it would be way too complicated, but I guess it isnt.

Thankyou all for the input!
I'll try to attach my script to a menu-item and see if I can get it working that way.

Perhaps a simple filebrowser-plugin would be an asset to mythtv down the road.

---

