---
title: "Copy damaged optical media"
date: 2012-09-07
forum: Multimedia Software
---

### Post by borgward on 2012-09-07
I tried to copy damaged optical disk w/K3b. Got to sector xyz and got failed message. The imperfect disk displays ok. I would like to copy it anyway, warts and all. I do not care if a pixel is out of place.

Any way I can override K3b to tell it to press on regardlessly?

---

### Post by mc4man on 2012-09-07
I would use either dvdisaster or ddres[COLOR="Navy"]c[/COLOR]ue to create an .iso & then burn elsewhere.

For dvdisaster pretty simple, the default settings should be ok other than one depending on version
Install, put media in drive. close out anything that opens, start dvdisaster

If there are any popups about ecc & or RS01 decline the action, not needed 
You can leave the default output at medium.iso or rename, don;t rename between runs if you do more than one.
 Make sure the drive/media is detected

Then to d. check open the Preferences icon in top  right area. Under the Image tab make sure it's set to ISO/UDF - screen 1
(_do not change the reading strategy from "linear" _

Nothing else needs to be changed/checked for 1st. or only run
*note the most of the settings are also links to help, if they turn blue & your interested then r. click

Back in main window click on the **read button** - let it go. It will dump the disk to the .iso with just 1 read try per sector, if any unreadable will then skip a block of 16 sectors which is generally the right amount.

After it's done, if you wish you can up the read tries & re-run. (just click the read button again
 dvdisaster will only re-read the sectors it missed on 1st. run so can go quicker.

If so i'd up the read tries to about 5. To do that open Preferences > Read Attempts & adjust the middle slider - screen 2

screen 3 shows the interface, in this case after reading a data cd (guess it was still in good shape
You'll find medium.iso or whatever if you named it in home folder

Note: if this happens to be a com. dvd video disk then before starting dvdisaster you need to open the disk in a player to authenticate the drive.

---

### Post by borgward on 2012-09-08
Did you mean ddrescue?

---

