---
title: "LiveTV setup problem after new install"
date: 2008-03-19
forum: Mythbuntu
---

### Post by dlfuller on 2008-03-19
Backend and Frontend both running on the same computer.  I click Watch TV and get this dialog: "MythTV is already using all available inputs for the channel you selected. If you want to watch an in-progress recording, select one from the playback menu. If you want to watch live TV, cancel one of the in-progress recordings from the delete menu."

But if I scan for channels again in the Backend, then Watch TV will work as expected without that dialog.

I have one input device a HDHomeRun linked to SchedulesDirect.

What glitch should I look for?

Also what is the significance of a whole bunch of UNKNOWN63#1, UNKNOWN63#2, etc., channels after a channel scan?  I am scanning Verizon FiOS for Clear QAM channels.

---

### Post by volkswagner on 2008-03-19
I have seen on the forums a possible glitch concerning the HDhomerun and network manager.  From what I remember you can set a delay in the start up or set a static ip and disable network manager.

[http://ubuntuforums.org/showthread.php?t=683389&highlight=hdhomerun+network+manager]("http://ubuntuforums.org/showthread.php?t=683389&highlight=hdhomerun+network+manager")


> Also what is the significance of a whole bunch of UNKNOWN63#1, UNKNOWN63#2, etc. 
This happens when you do multiple scans.  If the information is in schedules direct you may need to sort you first problem.  You can then delete your channels in your lineup.  Start fresh and grab your listings from source.

---

