---
title: "Jan 13 23:32:31 mythub mythtv-setup[2647]:Can't download lineup from schedules direct"
date: 2013-01-14
forum: Mythbuntu
---

### Post by marc.aronson on 2013-01-14
I'm having a problem with MythBuntu 12.04. Not upgrading an existing system -- clean install and I apply all updates. I then run mythtv-setup. I am able to add my tuner (HDHOMERUN prime). I then add my video source. I specify schedules direct, enter my username and password, hit the "get the lineup" button and no line up comes back. My old 0.24 system (LINHES-7.2 based) works all the time the same username and password. The logs have the following lines:

> Jan 13 23:32:31 mythub mythtv-setup[2647]: I CoreContext videosource.cpp:349 (fillSelections) Fetching lineups from Schedules Direct...
Jan 13 23:32:31 mythub mythtv-setup[2647]: I CoreContext datadirect.cpp:1158 (GrabData) DataDirect: Grabbing channel data
Jan 13 23:32:31 mythub mythtv-setup[2647]: I CoreContext datadirect.cpp:1021 (DDPost) Downloading DataDirect feed
Jan 13 23:32:41 mythub mythtv-setup[2647]: E CoreContext datadirect.cpp:1186 (GrabData) DataDirect: Failed to get data: Download error
Jan 13 23:32:41 mythub mythtv-setup[2647]: E CoreContext videosource.cpp:359 (fillSelections) DDLS: fillSelections did not successfully load selections
Jan 13 23:32:41 mythub mythtv-setup[2647]: I CoreContext datadirect.cpp:573 (~DataDirectProcessor) DataDirect: Deleting temporary files
Jan 13 23:32:45 mythub mythtv-setup[2647]: E CoreContext settings.cpp:204 (setValue) SelectSetting::setValue(): invalid index: -1 size: 
Jan 13 23:32:46 mythub mythtv-setup[2647]: E CoreContext settings.cpp:204 (setValue) SelectSetting::setValue(): invalid index: -1 size: 
Jan 13 23:32:49 mythub mythtv-setup[2647]: I CoreContext videosource.cpp:349 (fillSelections) Fetching lineups from Schedules Direct...
Jan 13 23:32:49 mythub mythtv-setup[2647]: I CoreContext datadirect.cpp:1158 (GrabData) DataDirect: Grabbing channel data
Jan 13 23:32:49 mythub mythtv-setup[2647]: I CoreContext datadirect.cpp:1021 (DDPost) Downloading DataDirect feed
Jan 13 23:32:59 mythub mythtv-setup[2647]: E CoreContext datadirect.cpp:1186 (GrabData) DataDirect: Failed to get data: Download error
Jan 13 23:32:59 mythub mythtv-setup[2647]: E CoreContext videosource.cpp:359 (fillSelections) DDLS: fillSelections did not successfully load selections
Jan 13 23:32:59 mythub mythtv-setup[2647]: I CoreContext datadirect.cpp:573 (~DataDirectProcessor) DataDirect: Deleting temporary files

My username is an email address -- the only non alpha-numeric characters it has are a "." and a "@". My password has only alpha-numeric characters.

Any help would be greatly appreciated!

Marc

---

### Post by larsolav on 2013-01-14
This may be a long shot. I had the very same problem! When no lineups would show up without any error message upon entering my schedules direct credentials, I purposely added the number 1 in the end of my password just to see if I would get an error message for entering the wrong password. I didn't get any error message, but I did get to chose a lineup!!!!
Strange indeed... YMMV, but worth a try?
Cheers!

---

### Post by marc.aronson on 2013-01-14
> **larsolav said:**
> This may be a long shot. I had the very same problem! When no lineups would show up without any error message upon entering my schedules direct credentials, I purposely added the number 1 in the end of my password just to see if I would get an error message for entering the wrong password. I didn't get any error message, but I did get to chose a lineup!!!!
Strange indeed... YMMV, but worth a try?
Cheers!

I will give it a try this evening. I should have added this to the original post -- Adding a lineup fails 90% of the team; 10% of the time it works, but then I can never successfully do the "fetch channel lineup" in the video connection...

---

### Post by marc.aronson on 2013-01-15
I changed my password and after a few more tries it is working. Very strange...

---

### Post by superm1 on 2013-01-15
I believe it could be fixed by this commit:

[https://github.com/MythTV/mythtv/commit/bcc459fa2893f65c1debe9a7f976d3c23e865531](https://github.com/MythTV/mythtv/commit/bcc459fa2893f65c1debe9a7f976d3c23e865531)

It's in autobuilds updates.  So pull the updates from autobuilds and try again.

---

### Post by marc.aronson on 2013-01-15
> **superm1 said:**
> It's in autobuilds updates.  So pull the updates from autobuilds and try again.

I suspect the 60-second timeout will help.

Not sure how to pull updates from "autobuilds". In the mythbuntu control center I have activated the "mythbuntu update repo", the "mythtv update repo" and the "XMLTV updates repo". Is either of these the autobuilds repo? Is there a config file I need to edit? Thanks!

Marc

---

### Post by superm1 on 2013-01-16
Marc, yeah that's the autobuilds repo.  Just use update manager to check for updates and run them now.

---

