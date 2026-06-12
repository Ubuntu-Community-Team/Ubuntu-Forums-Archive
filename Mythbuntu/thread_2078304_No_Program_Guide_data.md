---
title: "No Program Guide data"
date: 2012-10-30
forum: Mythbuntu
---

### Post by wh7qq on 2012-10-30
This is a fresh install of mythbuntu 12.04, mythtv 0.25 on an AMD Athlon x2 box with a HDHomeRun. It is a plain vanilla frontend/backend setup and other than customizing for the HDHomeRun, I went with the default settings. I have a working SchedulesDirect account that works ok on a different box. Everything seems to be working ok...I can watch liveTV on mythtv from the HDHomeRun, but in spite of running mythfilldatabase multiple times, I get no guide data in the schedule. The channel assignments are there and correct for my location but blanks ("unknown") where the program data should be. mythfilldatabase.log is empty....that seems strange.

Hardware:
AMD 64x2 on Biostar TA780G-M2 mobo with 2G pc2700 Ram
Asus nvidia GT210 graphics card w/1M ddr3 HDMI connection to Sony LCD TV
WD 1T Caviar Green HD...0.5T available this partition
HDHomeRun tuner box to OTA antenna

Software:
Mythbuntu 12.04 64K with 3.2.0-32-generic kernel
mythtv 0.25
nvidia 295.40 driver

---

### Post by klc5555 on 2012-10-30
I don't know if by "channel assignments" you mean the 5-digit xmltvid number for each channel (and the schedule info that goes with it). If not, and the xmltvids are frequently not pulled in with a channel scan, these will have to be gotten for each channel from SchedulesDirect after logging in, then entered manually for each channel via Channel Editor in the backend setup. Or via livetv by bringing up the screen editor while each channel is on screen. 

Once all the xmltvids have been entered in, mythfilldatabase is run again, whereupon the scheduling data should fill in beginning with that for tomorrow.

---

### Post by wh7qq on 2012-10-30
I am not sure what you are asking.  When I bring up the program guide, there is a column listing the channels with id info down the left side with time of day on the top and empty boxes corresponding to each time slot in columns below...like a spreadsheet of channels and programs. I have never needed to manually enter any information from this in the previous successful setups I have done,  including one last week.

I will check the Channel Editor.

[COLOR="Red"]Follow-up:  I went back into the backend-setup and the xmltvid was present for all channels but further checking, I found that in the "Program Schedule Download Options" I had not checked (or inadvertently unchecked) the "Automatically update program listing" line.  Running mythfilldatabase again fixed the problem.

With such a bewildering array of options in the setup, it is pretty easy to screw things up.  Thanks to klc5555 for pointing me in the right direction.[/COLOR]

---

