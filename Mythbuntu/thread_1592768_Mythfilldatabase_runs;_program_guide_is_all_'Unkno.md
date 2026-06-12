---
title: "Mythfilldatabase runs; program guide is all 'Unknown'"
date: 2010-10-10
forum: Mythbuntu
---

### Post by DrJohn999 on 2010-10-10
Had to revert to 10.04 due to segmentation faults (see [http://ubuntuforums.org/showthread.php?t=1592588](http://ubuntuforums.org/showthread.php?t=1592588)) in the front end with 10.10 (gotta watch that TV!). However, the previous 10.04 install was done as an in-place upgrade from 9.10. This time around it's a fresh install, which went without a hitch until, after configuring the backend and running mythfilldatabase, I opened LiveTV to find that all programs were listed as "unknown." The same setup sequence (see below) in 10.10 earlier did show the actual program listings. I also tried running mythfilldatabase from a terminal, and it appeared to be working with the usual text / disc activity, but did not bring in the program data to the front end.

System: ASUS M3N78-EM, 2 GB, nVidia built-in graphics (and am using nVidia propr. driver), /dev/sda is a 1 TB SATA with XFS partition mapped to /var/lib/mythtv (done at setup so it appears first time mythtv runs), /dev/sdb is a 320 GB drive with root and swap. Boots off of /dev/sda. Using HDMI for TV, and sometimes spdf to 5.1 amp.

Setup procedure: install from bootable USB thumb made on a 10.04 system with Startup Disk Creator. For Mythbuntu 10.04 I find it necessary to set APCI=OFF at first boot from the thumb. Installation then goes through without a problem. Hostname entered as <name>.<domain>.loc (DNS is set up this way locally); the IPs of both the Myth box and the HDHomeRun are fixed-address by MAC via DHCP (none of this mattered before...). Skip running backend setup just yet, update all packages first (198 files now!!), reboot again, then run the frontend, setup, general, and change the database from localhost to the fixed IP address (also resize the GUI screen and allow video to run full-screen). Now run Mythconfig, add the DVD codecs, and start backend setup; set the IP addresses there to the same fixed IP, configure the 2 channels of the HDHR, one instance of SchedulesDirect (set to the regional broadcast channels), and source each HDHR channel from SchedulesDirect (Scan on channel 0, then copy the scan result to channel 1). Channels show up correctly in channel editor, but did not edit any of them.

Leave backend setup and allow mythfilldatabase to run, which it does with what passes for its 'normal' appearance. Start the frontend, or reboot, or run mythfilldatabase from a terminal, no dice -- all channels still 'unknown.'

Since the above works well in 10.10 (and similarly worked in 9.10), my question is, what's different here?

---

### Post by klc5555 on 2010-10-11
A couple of possibilities. The channel editor data for each channel would need the SchedulesDirect xmltvid number edited in, usually by hand in channel editor or from the onscreen menu in livetv, in order for mythfilldatabase to obtain information on a particular channel. You may wish to check as to whether the xmltvid number for any particular channel is actually where it should be. 

Also, when mythfilldatabase runs in default mode, it fills in schedule data starting at midnight on the day after mythfilldatabase has run. So your schedule data may in fact have filled in, scroll forward in the guide a couple of days to see whether it's there. To fill in today's schedule, you'd have run mythfilldatabase --refresh-today   from a terminal.

---

### Post by DrJohn999 on 2010-10-11
The program information is blank for the next 2 weeks.

All of the xmltvid fields were blank in channel editor. I looked them up on SchedulesDirect, Report, and entered 4 or 5 of them, then ran mythfilldatabase -- still no program information; the entered xmltvid values are still there.

This could be a bug in 10.04 LTS:  9.10 and 10.10 both loaded all program data without entering any xmltvid data by hand. And in my particular case previously the system got to 10.04 as an upgrade from 9.10 so would already have had whatever is required to pull in the program info. The difference here is now it's a fresh install.

---

### Post by klc5555 on 2010-10-11
Well, then I suppose you'll need to run mythfilldatabase from a terminal in debug mode to gather some information as to what's going wrong when the script executes, if the information is really not making its way into mythconverg after a "mythfilldatabase --refresh-all --refresh-today". You may also have something inadvertently flukey set up, like 2 video sources, where both tuners are set up on one, but the mythfilldatabase was set to collect only for the other.

You may still end up having to edit in the xmltvid info by hand --I've never personally seen automated xmltvid retrieval work properly on any install I've ever had going back to 7.04, but I suppose there must be those for whom it has worked.

---

### Post by DrJohn999 on 2010-10-11
This appeared in the terminal output of mythfilldatabase: ```
No channels are configured to use grabber.
:
:
DataDirect: Not inserting channels into disconnected source 1.
```

OK <starting to look sheepish> Sources in backend setup shows a blank line followed by the one I set up. Not sure how it got that way. I added SchedulesDirect another time (under a different source name) then deleted the original SD source. Of course then I had to connect the tuners to the source, scan again, and re-run mythfilldatabase.

Yep, that did the trick. <Swears he set it up correctly before but...  }:?> 

Solved, then, but not sure what went wrong in the first place.

---

