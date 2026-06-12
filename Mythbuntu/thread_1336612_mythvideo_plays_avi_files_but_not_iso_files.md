---
title: "mythvideo plays avi files but not iso files"
date: 2009-11-24
forum: Mythbuntu
---

### Post by pinacate on 2009-11-24
I'm moving from KnoppMyth to MythBunutu. I imported all my old videos from KnoppMyth to Mythbuntu. I can see all my videos using MythVideo but I can only play the ones of type 'avi'. Attempts to play iso videos simply fails back to the MythVideo selection screen.

I see the following in mythfrontend.log: 
TV: Attempting to change from None to Watching DVD
libdbdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Can't stat /dev/dvd
No such file or directory

Prior to getting this error the system was complaining that I didn't have libdvdcss installed. I turned on all the settings in MCC/Proprietary Codec Support including Medibuntu GPG Keyring.

I looks like its trying to access /dev/dvd. Why would it do that to play an on hard disk iso?

---

### Post by larsolav on 2009-11-24
Looks like you have storage groups defined for the videos. Mythtv 0.22 does not like ISOs in storage groups (see [_Disadvantages_]("http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide#Disadvantages"))
Check post number 2, [_here _]("http://ubuntuforums.org/showthread.php?t=1318635")on how to turn it off:
> Backend setup > Storage Directories. Select 'Videos' and delete '/var/lib/mythtv/videos'. The entry will default to '/'.

When exiting the setup, it will complain that '//.test/' cannot be written, select 'No thanks, I know what I'm doing'.

In the frontend, Utilitites/Setup > Setup > Media Settings > Media Settings > Video Settings > General, check 'Directories to hold videos' is showing the correct path to the nfs share.

In 'Watch Videos', press 'M' and scan for changes. All videos should be available again, and your .iso's should play.

---

### Post by pinacate on 2009-11-25
Thank you Larsolav! Sure enough. I have inadvertently turned on Storage Groups.

---

