---
title: "Shotwell import database from F-Spot - what is &quot;database file&quot;?"
date: 2011-02-03
forum: Multimedia Software
---

### Post by jcoles on 2011-02-03
The Shotwell "Import from F-Spot" function requests an "F-Spot database file". All I know is the directory where F-Spot stored the photos. Shotwell will not accept a directory name. What would an F-Spot database file be named? 

Yes, I know there's also an Import from Folder function. But I had F-Spot before, so Import from F-Spot should work.

---

### Post by gwm on 2011-03-09
Hi,
I had a similar problem. I added another hard drive and installed 10.10 on it, leaving the old Karmik drive there for backups. So how to get the fotos across to the new drive...?

Google turned up a link that showed me that the f-spot database is located in a hidden folder under the home directory. So I went browsing on my Karmik drive to **/home/gwm/.config/f-spot/photos.db** and there it was. (To view the hidden directories, press ctl-h or use the browser menus).

I didn't know whether Shotwell would copy the files to its own structure or not, so I copied my pictures folder from Karmik to the same location on the new hard drive. Next I copied the .config/f-spot folder, which contained other files that might be relevant, from /home/gwm/.config to the same location on the new drive. Now when I started Shotwell and went to import from f-spot, it found the old stuff and copied the database references over. Then I deleted the .config/f-spot folder.
However, take note:
[LIST]
[*]The imported F-spot files were not transferred to new locations.
[*]Shotwell didn't import tags as a heirarchy from F-Spot :(
[*]New pictures that one imports go to new locations, so set the root folder in the Showell Edit>Preferences menu before importing new pictures.
[*]Trashing pictures, only deletes the references. The pictures remain. Perhaps they go when one empties the trash. (new program - new mind set)
[/LIST]

---

### Post by eric-yorba on 2011-11-03
> **jcoles said:**
> The Shotwell "Import from F-Spot" function requests an "F-Spot database file". All I know is the directory where F-Spot stored the photos. Shotwell will not accept a directory name. What would an F-Spot database file be named? 

You need to enter the F-Spot database file itself, which by default on Ubuntu is in ~/.config/f-spot/photos.db

I highly recommend upgrading to Shotwell 0.11.5 (if you haven't already) before doing the import.

---

