---
title: "Shotwell publishing is not working properly"
date: 2012-07-25
forum: Multimedia Software
---

### Post by xbobby_bobx on 2012-07-25
Okay so I'm having a problem with publishing photos via Shotwell to  Facebook.. When I choose the picture and hit publish, it shows up with  the publishing window showing only Piwigo and no other websites.. When I  checked if the plug-ins are enabled, they are there once I uncheck  Piwigo plugin it says I have an incompatible plug-in.. I tried  everything I even reinstalled it many times and I still have the same  problem, can somebody guide me to fix this problem or at least tell me  where is the plug-in directory so I can modify it myself. 

This problem is happening with all the publishing plug-ins except Piwigo

Technical Details: 

Linux OS: Ubuntu 12.04 

Shotwell version: 0.12.3+webaccounts1 

I hope somebody can help.

---

### Post by eric-yorba on 2012-07-26
From the package name, I take it you're using Ubuntu Web Apps.  This replaces the normal build of Shotwell with a version that's been modified by Canonical to support their new Web Apps system.  Sounds like you've hit a bug, so I'd recommend [filing a ticket on Launchpad]("http://www.ubuntu.com/community/report-problem").

Meanwhile, you can revert back to the default version of Shotwell by removing the PPA and purging the package, or by forcing a specific package version (instructions on forcing a version in Synaptic are [here]("http://www.ubuntu.com/community/report-problem").)

---

### Post by xbobby_bobx on 2012-07-26
You are actually right, I installed the web Apps.. Now I regret it.. Anyway I'm going to report it now and install the old one.. Thanks a lot!

---

### Post by switch10 on 2012-09-09
> **eric-yorba said:**
> From the package name, I take it you're using Ubuntu Web Apps.  This replaces the normal build of Shotwell with a version that's been modified by Canonical to support their new Web Apps system.  Sounds like you've hit a bug, so I'd recommend [filing a ticket on Launchpad]("http://www.ubuntu.com/community/report-problem").

Meanwhile, you can revert back to the default version of Shotwell by removing the PPA and purging the package, or by forcing a specific package version (instructions on forcing a version in Synaptic are [here]("http://www.ubuntu.com/community/report-problem").)

Yeah, I had the same issue.  This fixed it.

---

### Post by rkonrad on 2013-03-11
I'm having the same problem.  The link the "here" is the same link as reporting a bug.  Can you let me know what specific version of Shotwell works - thanks!

---

### Post by eric-yorba on 2013-03-11
Oops, that link should point here:
[https://help.ubuntu.com/community/SynapticHowto#How_to_force_the_installation_of_a_package_version](https://help.ubuntu.com/community/SynapticHowto#How_to_force_the_installation_of_a_package_version)

At any rate, this is an old thread and you should start a new one!

---

