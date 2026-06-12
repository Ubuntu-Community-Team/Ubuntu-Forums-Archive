---
title: "HDHomeRun Issues With Mythbuntu 10.04"
date: 2010-08-16
forum: Mythbuntu
---

### Post by Zenguy on 2010-08-16
First, I have been using Mythbuntu for over a year with analog tuners and everything has been working great. Recently, I purchased a HDHomeRun to pull in the HD stations from my cable company.

I performed a clean install of Mythbuntu 10.04 and setup the HDHomeRun. During the channel scan, some channels were added that did not have a station name.

When I attempt to tune my frontend to the HDHomeRun tuner, very frequently the frontend will crash/hang or error out. Very often I just get a black screen and the frontend becomes unresponsive to keyboard and remote clicks. 

I have had some success tuning some stations, but it appears that there are some bad stations that were added during the scan. I tried deleting all of the stations that did not have station names, but it didn't solve the problem.

I have turned on Auto Builds, so in theory I am running the latest and greatest version of Myth.

The logs provide little info. The last error in the frontend log mentions something about attempting to setup a player, but it already exists. Then the frontend crashed back to the desktop.

I have a friend who is having similar problems on his hardware, so I don't think it is particular to my setup. Anyone else having a major headache with HDHomeRun? Is there a solution?

---

### Post by superm1 on 2010-08-16
> **Zenguy said:**
> First, I have been using Mythbuntu for over a year with analog tuners and everything has been working great. Recently, I purchased a HDHomeRun to pull in the HD stations from my cable company.

I performed a clean install of Mythbuntu 10.04 and setup the HDHomeRun. During the channel scan, some channels were added that did not have a station name.

When I attempt to tune my frontend to the HDHomeRun tuner, very frequently the frontend will crash/hang or error out. Very often I just get a black screen and the frontend becomes unresponsive to keyboard and remote clicks. 

I have had some success tuning some stations, but it appears that there are some bad stations that were added during the scan. I tried deleting all of the stations that did not have station names, but it didn't solve the problem.

I have turned on Auto Builds, so in theory I am running the latest and greatest version of Myth.

The logs provide little info. The last error in the frontend log mentions something about attempting to setup a player, but it already exists. Then the frontend crashed back to the desktop.

I have a friend who is having similar problems on his hardware, so I don't think it is particular to my setup. Anyone else having a major headache with HDHomeRun? Is there a solution?

From what i've seen, these channels are usually video-on-demand that are being used by other users on the cable network at that time.  The channels are transient, and won't persist after the other user finishes their video-on-demand program necessarily.

Any channels doing this, I would just remove.

---

