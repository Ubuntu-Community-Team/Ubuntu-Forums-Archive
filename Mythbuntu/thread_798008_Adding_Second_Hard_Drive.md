---
title: "Adding Second Hard Drive"
date: 2008-05-17
forum: Mythbuntu
---

### Post by Andrew_Carr on 2008-05-17
I never imagined it'd be so frustrating to add a second hard drive to store movies, otherwise I would've waited on my install. But now that I have 500gigs of movies on my first hard drive, I'm loathe to mess with that setup. So is there a simple way to jury rig a regular mythbuntu install so that a second hard drive is simply seen as extra space in a specific folder? 

   So far I've mounted the second drive to a folder under the videos folder in the mythtv directory. But that simply broke myth transcoding daemon(mtd -n makes it run now and this isn't a big deal, since I just want people to select a movie and hit play). And I can't seem to find a way to change the default save point for the rip process in mythtv. That would also solve the problem since then I could simply rip future DVDs into the new subfolder. 

  Any help on how to simply add more storage space to a mythbuntu install would be greatly appreciated. I'm apparently pretty bad at linux and constantly get tripped up on these seemingly basic tasks.

[Edit:] Not sure if this matters, but I'm running 8.04.

---

### Post by volkswagner on 2008-05-17
Take a look here.

[http://ubuntuforums.org/showthread.php?t=665443&highlight=storage+groups]("http://ubuntuforums.org/showthread.php?t=665443&highlight=storage+groups")

Look into storage groups.  It is included with mythtv .21

---

### Post by Andrew_Carr on 2008-05-17
Yeah, I tried that by mounting the second drive on a sub-directory of the videos folder. It worked, just nothing will save there. I guess I can try moving my old movies to the new hard drive and then saving new movies to the old one when it's empty. Think that'll work?

I'd like to make it so users don't have to navigate directories or anything, just select a movie and hit enter.

---

### Post by nasha on 2008-05-18
[HTML]http://www.mythtv.org/wiki/index.php/Storage_Groups[/HTML]

This explains storage groups because im not sure you understand them.
After mounting your hdd, and placing it in your fstab, you will need to add the mounted directory to your default storage group in mythtv-setup > Storage Groups

Its as simple as that. If you have any issues, it will most likely be due to permissions in your fstab on the mounted directory. I myself have experienced this.

---

### Post by klc5555 on 2008-05-18
> **Andrew_Carr said:**
> Yeah, I tried that by mounting the second drive on a sub-directory of the videos folder. It worked, just nothing will save there. I guess I can try moving my old movies to the new hard drive and then saving new movies to the old one when it's empty. Think that'll work?

I'd like to make it so users don't have to navigate directories or anything, just select a movie and hit enter.

If you've just added this new drive (properly formatted and set in fstab) to an established system, its new mounted directory may still have its owner and group set to "root" rather than mythtv  So mythtv can't write to it. The command ls  -l  of the directory immediately above this directory will tell you who the owner/group is. If still root, then use the chown and chgrp  commands from a terminal to set the owner and the group to mythtv. Permissions on the new mounted directory may also be wrong. Doing a "chmod" to 755 seems to be OK. Thereafter, adding the new drive's directory to the default storage group in mythtv's backend setup will work just fine, and transparently, as others have said. 

Cheers!:)

---

### Post by Andrew_Carr on 2008-05-18
Ok, great. Thanks for the help.

---

