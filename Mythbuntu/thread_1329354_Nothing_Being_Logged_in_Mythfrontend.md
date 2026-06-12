---
title: "Nothing Being Logged in Mythfrontend"
date: 2009-11-17
forum: Mythbuntu
---

### Post by jMon54 on 2009-11-17
I am not seeing anything going to my "mythfrontend.log" file.  In other words, the file is empty.  And I would really like to see what's going on so I can troubleshoot an issue with not being able to record programs but can view live TV.  I have recreated the log file and made sure mythtv can write to it but still nothing is being logged.  I have also run the repair and optimize scripts on the database.  And I went through the mythtv setup to see if there is a place in there to indicate the location of the frontend log but found no reference to this.  Does anyone know how I can get mythtv to resume logging frontend activity?

---

### Post by plantschi35 on 2009-11-18
> **jMon54 said:**
> I am not seeing anything going to my "mythfrontend.log" file.  In other words, the file is empty.  And I would really like to see what's going on so I can troubleshoot an issue with not being able to record programs but can view live TV.  I have recreated the log file and made sure mythtv can write to it but still nothing is being logged.  I have also run the repair and optimize scripts on the database.  And I went through the mythtv setup to see if there is a place in there to indicate the location of the frontend log but found no reference to this.  Does anyone know how I can get mythtv to resume logging frontend activity?

Sorry for my bad English I´m posting from Germany. I have the same problem with 9.10 on my separate frontend. It seams that there is a bug in the installation of 9.10, if you install a machine which only acts as a frontend. The mythfrontend.log should be in /var/log/mythtv, but this directory was not created during setup. I have now installed the secondary backend functionality too, and now the directory is created and the log-files can be found in the directory. Now i have uninstalled the secondary backend functionality, the Directory still exists and logfiles are still in use.

---

