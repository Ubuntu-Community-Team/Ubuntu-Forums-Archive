---
title: "gPodder subscription list gone after upgrade to 12.10"
date: 2012-10-19
forum: Multimedia Software
---

### Post by alexgo on 2012-10-19
After I upgraded to lubuntu 12.10 and opened up gPodder(3.2.0) I discovered my subscription list was gone. I looked in my local files and found the gpodder downloads are still there as well as the gpodder folder. Unfortunately I didn't use the online backup or create an export file before the upgrade.

Is there some way easy I can restore all the gpodder settings? This will be the second time I have to manually add every podcast after I couldn't export from Amarok if there is no solution and it's getting a bit old.

---

### Post by echolink on 2012-10-20
I tried to recreate your issue using 12.04, and 12.10. However after looking in user/share/gpodder and in my local home directory there appears to be no local cache of Subscriptions. Unless you export your feeds to your local /home or use gpodder's online sync feature there appears to be now way to recover subcriptions. I find it odd however that during upgrade you lost you subcriptions. I would recommend resubcribing, and exporting to OPML.

---

### Post by gds on 2012-10-21
I had the same problem. Ubuntu 12.10 now ships gpodder 3 which uses a new and incompatible database format. They don't appear to have supplied any conversion tool nor any warning that your old config wouldn't be converted (thanks!). However - it seems gpodder3 keeps it's configuration in a gPodder directory in your home dir, while gpodder 2 was keeping it's configuration in .congfig/gpodder. So I was able to recovery my subscriptions.

Here's what I did: from the [gpodder download site]("http://gpodder.org/src/") I downloaded the last release of version 2 (I used [this one]("http://gpodder.org/src/gpodder-2.9.tar.gz")). Unpack the files somewhere (we don't need to actually install it, just run it once. I put them in /tmp). Make sure gpodder 3 isn't running.

Then from a terminal I ran
```
cd /tmp/gpodder-2.9
bin/gpodder.py
```
Now you can export your subscriptions to an OPML file that gpodder 3 can import (it's on the subscriptions menu). Once you've done it you can quit and run gpodder3. Skip past the initial dialog offering you default subscrptions and you can import the OPML file you created in the last step.

I had an extra problem, because even after this gpodder3 didn't recognize any of my previously downloaded podcasts (it wanted to pull down 3Gb of new shows!). This might be unique to me because I was using a non-standard location for my downloads, but I solved this by the brute-force technique of doing one last sync to my player from gpodder 2 and then telling gpodder3 to consider all the subscriptions up to date. I'm sure we could do better but this was enough for me.

---

### Post by alexgo on 2012-10-22
Thanks guys! gds' method above worked, but in the terminal I had to delete the .py part for the code to work.

I  also had the problem of downloaded files not showing up(wanted to download 20gigs), but found a solution.  the downloads in gpodder 2 were located in gpodder-downloads, but in  gpodder 3 they were located in gpodder/downloads an entirely different  folder. I simply deleted all the podcast folders in the new folder and  dragged in the old ones, restarted gpodder and the files were there!

I ran into one problem with this, a few of the folder names changed for example 99% invisible changed to 99_invisible, in that case I just dragged the audio and cover files to the newly named folders. It didn't work for This American Life though, that podcast only hosts one show at a time, so maybe it has to verify the file with the online feed?

Thanks again!

---

### Post by Guttor on 2013-10-18
gpodder provides a migration utility, gpodder-migrate2tres, which handles the migration automatically without and hassles or gymnastics.

---

