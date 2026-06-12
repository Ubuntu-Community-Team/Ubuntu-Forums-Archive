---
title: "Ububtu 10.10: Can't enable network after installing Wicd"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by bliffle on 2011-05-16
The Ubuntu 10.10 on my X60 has been running beautifully for several months, so I just had to go and rock the boat! So I installed "Wicd" and a couple other network things like "wifi radar" , "SWscanner", etc., and now it won't connect to the network (which is wireless, through the builtin adapter and a Cradlepoint CTR500 router). 

When I right-click on the network icon at the top of the screen the "Enable networking" is grayed out! And, of course, none of the Network Tools bring the network up, although they recognize that my router is alive and well and broadcasting.

Also, two other computers are successfully connected through the Cradlepoint router.

So I finally backed out the Wicd, WifiRadar, etc., restarted the computer a couple times and still can't connect. I still can't get the "Enable Networking" enabled on the network icon.

---

### Post by mohdforever on 2011-05-23
exactly what i did ....

sooo what is the solution 

i neeeeeeeeeeed heeeeeeelp 

pleeeeeeeeeeeeeeeeeaase

---

### Post by bliffle on 2011-06-04
I'm in the middle of an experiment to see if I can recover NetworkManager by replacing the ubuntu 10.10 system from the CD. But first I copied that partition to a clean 500gb HDD for backup. I suspect I'll have to restore "/home" after I do the re-install.

I'm sure there's some way to re-install NW using the 10.10CD instead of the internet, but I don't know how to do it. So I'll try the desperate way pretty soon.

---

### Post by nm_geo on 2011-06-04
You can add the CD to the repository list in Synaptic..
Settings-Repositories-Check the Button for CD
Stick CD in pick you package Synaptic will use it.

---

### Post by manzdagratiano on 2011-06-04
When you installed wicd, did you uninstall networkmanager? The two are incompatible and only one should be working at one time. I use wicd instead of networkmanager - as an example, when I upgraded from Maverick to Natty, the update manager installed networkmanager even though wicd was installed. Neither connected to the internet of course, and removing networkmanager immediately fixed the problem. Also, make sure that wicd-gtk is installed.

EDIT: From your original post, it does appear you had not removed networkmanager, since "Enable Networking" is a networkmanager thing.

---

### Post by bliffle on 2011-06-04
I tried this, per nm_geo:

"You can add the CD to the repository list in Synaptic..
Settings-Repositories-Check the Button for CD
Stick CD in pick you package Synaptic will use it."

I also had to uncheck the network downloads in that box.

It went about halfway, loaded 7 of 25 files, and asked for the 10.04CD, which I put in, and then it asked again (as if disatisfied with the CD) and then it just repeated that.

---

### Post by bliffle on 2011-06-05
> **manzdagratiano said:**
> When you installed wicd, did you uninstall networkmanager? The two are incompatible and only one should be working at one time. I use wicd instead of networkmanager - as an example, when I upgraded from Maverick to Natty, the update manager installed networkmanager even though wicd was installed. Neither connected to the internet of course, and removing networkmanager immediately fixed the problem. Also, make sure that wicd-gtk is installed.

EDIT: From your original post, it does appear you had not removed networkmanager, since "Enable Networking" is a networkmanager thing.

No. I had some idea that I could compare the two. I figured if there was a conflict that the installer would block one.

---

### Post by bliffle on 2011-06-05
I'm not having any luck restoring the NetworkManager from CD (although I'd love to learn how to do that for future reference), so I'm going to replace the whole ubuntu system then restore the "/home" from my backup.

So this morning I DLed the 11.04 DTS i386 CD so I can upgrade at the same time. I noticed yesterday when I was thinking to re-install 10.10 that it demanded that I re-format my Ubuntu partition, so I figured to upgrade and get a Long Term Support system at the same time. I'll just have to copy my '/home' backup afterwards, once I figure the best way to do that. I hope there's no residual info in '/home' from 10.10 that will upset 11.04, but surely the system designers wouldn't allow anything like that, would they? Would they? I've ben told that some guys put their '/home' in a separate partition so that a system upgrade just affects a system partition and nothing else. Maybe I should take this opportunity to put the system and '/home' in separate partitions to make fixups like this easier in the future. Except I'm not sure how to tell the system that '/home' is in that other partition.

---

### Post by bliffle on 2011-06-05
OK, I installed the new 11.04 over the old 10.10 (after struggling with some download issues, as before I required the BitTorrent DL to get a clean DL). I now have a /home with only a few empty folders. Now i have to plot moving the old /home to the new 11.04 partition. I guess I can just use filemanager and <ctrl>c, <ctrl>v the main folders, but I wonder if there's a more efficient way (or does filemanager figure it all out?). There's 240,000 items in the old /home.

I just wonder if I should put that /home in a new partition to facilitate future system updates. This would be the time to do it. I could reduce the 11.04 partition to something small, set aside a similar size partition for an extra system in the future, and make a big partition for /home. But I'm not sure how to connect ubuntu system to the /home in a separate partition.

---

