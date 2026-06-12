---
title: "Using NTFS partitions with MythVideo"
date: 2009-05-02
forum: Mythbuntu
---

### Post by 123def on 2009-05-02
Hi,

although I'm new to Ubuntu 9.04 (and to Linux in general), I was curious enough to try installing MythTV (which apparently worked). My curiosity didn't stop there, so I even added the MythVideo plugin... ;-)

Here comes the trouble:
As I'm currently using a dual-boot setup (WinXp and Ubuntu on the same machine), I transfered all my videos, music and pictures to a NTFS partition on a physical different hard disk (the operating systems are both on the same).
Accessing this files from Ubuntu is a charm. The NTFS partition was automatically detected, mounted and so on.

My impression was that I just had to add the corresponding folder to the MythVideo folders in the frontend's settings "var/lib/mythtv/videos:/media/MY_NTFS_PARTITION_NAME" (of course, that's not really the name of my partition).
Coming from windows, I was proud to remember that unix is case sensitive, so I was a bit dissapointed, when it didn't work right away.

Obviously my folder is not accepted by MythVideo, as it dissappears from the settings, once I return to the settings page.

Thanks in advance!

---

### Post by 123def on 2009-05-03
Ok, I was able to figure a few things out for myself:

1. For some reason far beyond my knowledge, the MythTV frontend isn't going to real fullscreen when using compiz desktop effects (which I am) under Ubuntu 9.04. Because of that, I wasn't able to see what was written on the lower MythTV icons. Things such as "next" just got lost.
After clicking through all 7 setting pages with "next" (kind of annoying, if you ak me), my folder selection WAS saved.

2. As there were still none of my folders displayed inside the videos section, I decided (decisive as I am), that it might be easier to create shortcuts to my NTFS video folder and just copy this shortcut into the /var/lib/mythtv/videos folder.

I think, the same trick will work with music and pictures, still I'd appreciate if someone would enlighten me, why my naiv approach of just typing in the NTFS folder wasn't successful.

---

### Post by crez79 on 2009-05-03
Have you run video manager? Video manager tells mythtv which files to show. You can also use video manager to add metadata such as director, plot and cover artwork. On page 2 of the general videos config page, there are three option to make the files browsable by default in the various views. Checking these options will make it that you don't have to run video manager, but depending on the number of files in your collecion, will slow down the browsing in mythtv considerably.

You can adjust the size of the full screen using the screen wizards in the general settings menu.

---

