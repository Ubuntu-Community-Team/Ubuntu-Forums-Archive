---
title: "HD video crashes to login screen after upgrade to 10.10"
date: 2010-11-07
forum: Mythbuntu
---

### Post by Don Geddis on 2010-11-07
I've got a MythTV backend machine and frontend desktop.  Both were running Ubuntu 10.4, and working fine.  I recently upgraded both machines to 10.10.  My myth version is "0.23.1+fixes26437-0ubuntu1".

After the upgrade, I can watch standard definition video (either live or recorded), just fine.  But any attempt to watch high definition video (either live or recorded) causes mythfrontend to crash, and in fact the whole X session to crash, and I'm returned to the Ubuntu login screen.

The last thing in the log file (attached) is "<unknown>: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.", and the one before that is an audio warning, "AudioPulseUtil, Warning: Can not connect to sound server, can not suspend.  Connection terminated"

Any ideas?  Any suggestions for something to try next?

My video card is an nVidia GeForce 8800 GTX, and I've got two 1920x1200 monitors (one LCD, one CRT), as a single desktop via TwinView.  (The mythtv video just runs on the CRT monitor.)

---

### Post by grygub on 2010-11-07
I had the same problem. Check out this thread [http://ubuntuforums.org/showthread.php?t=1604893]("http://ubuntuforums.org/showthread.php?t=1604893").

---

### Post by Don Geddis on 2010-11-07
Success!  Thank you so much, grygub!  You're a lifesaver.

For anyone who might happen upon this thread: something seems to have gotten broken about the XvMC playback software.  The fix: start from mythfrontend main menu, select "Utilities / Setup", select "Setup", select "TV Settings", select "Playback", do "Next" on first page, "Next" on second page.

On third page, "Playback Profiles", the first item is "Current Video PLayback Profile".  Mine was set (by default?) to "CPU+".  If you look at the rules that implies, one was "if rez > 0 0 -> XvMC".  This is apparently causing the trouble.  There are a handful of possible profiles, many of which also use XvMC.  But the next one, "CPU++", is much simpler, with just a single rule: "if rez > 0 0 -> ffmpeg & XVideo".

I made that change, did a bunch of "Next"s to get out, save everything ... and now HD video works again!

I'm thrilled.

---

