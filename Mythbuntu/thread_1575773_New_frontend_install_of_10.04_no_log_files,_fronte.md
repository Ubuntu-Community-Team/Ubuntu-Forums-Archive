---
title: "New frontend install of 10.04: no log files, frontend crashes after several minutes"
date: 2010-09-16
forum: Mythbuntu
---

### Post by hallew on 2010-09-16
Hello,

I have a new install of Mythbuntu 10.04, absolutely stock, frontend only, and when it starts up mythfrontend it shows the background of the menu screen but never displays the menu items, and then after doing this for several minutes it crashes back to the desktop.  There is no mythtv folder in /var/log and after I created one and put a mythfrontend.log file in there, nothing is ever written to this file.

I suspect the underlying reason for the crashing has something to do with display settings since if I open a VNC session to this machine and start mythfrontend in that session, mythfrontend works and doesn't crash, but it behaves as described when its only display is the attached monitor.  I guess I expect that it is a segmentation fault.  But before fixing the bug, I'd like to get logging working (the reason is that it is necessary to VNC into this machine in order to use a mouse and keyboard at the moment, and as soon as there is a VNC session things behave differently than they do when there is only the monitor as the display, so I don't want to attempt to troubleshoot this at all until the normal mythfrontend process can output results to a log).

Any help with getting mythfrontend to write out to a log automatically?  I googled and saw a couple people mention having this no-log bug with default 10.04 installs but I couldn't find any solutions.  This is on an Intel Atom machine connected to a VGA monitor and the network connection is definitely fine at the time that mythfrontend starts. Thanks.

---

### Post by tgm4883 on 2010-09-16
Not sure about the no-log issue. Maybe try running mythfrontend from a terminal and posting the output. Perhaps the frontend logs will tell us why there is no log.

---

### Post by hallew on 2010-09-16
Hi, thanks.  Attached is the output from running mythfrontend in terminal from a VNC session.  After this output mythfrontend started and ran fine because it was run from a VNC session, although it didn't print a log in /var/log/mythtv.

---

### Post by hallew on 2010-09-19
Any suggestions for obtaining logs from mythfrontend in Mythbuntu 10.04?  I see a report of very similar behavior here:

[http://readlist.com/lists/mythtv.org/mythtv-users/33/165176.html](http://readlist.com/lists/mythtv.org/mythtv-users/33/165176.html)

I also had the symptom with the default MythTV UI appearing instead of the default Mythbuntu UI in the frontend. I've filed a bug for the issue but I'd also like to try to salvage my install if anyone has any ideas, thank you.

---

### Post by LowSky on 2010-09-20
from the output file it seems you tried to set a theme and fonts to settings not available or that will correctly work. To fix the frontend back to default type this into a terminal

```
mythfrontend --reset
```

---

### Post by hallew on 2010-09-20
OK, I switched the theme to the Mythbuntu theme (the fact that it was on another theme is related to the original bug apparently) and we'll see if that helps the crashes.  The workaround for the no-log bug was to create the log directory manually with the right permissions.  This has been a weird upgrade to Mythbuntu 10.04 -- I've had this non-logging and crashing client and on the server I lost the ability to update listings due to the Date::Manip/xmltv bug.

---

### Post by SiHa on 2010-09-21
/var/log/mythtv not being created in a frontend-only install has been present since at least 8.04. Not sure why it's so hard to fix...

As you say, though, it's just a case of manually creating it.

For future reference, the logs get chucked in /temp if this folder isn't present, but this folder is cleared each boot.

---

### Post by tgm4883 on 2010-09-21
> **SiHa said:**
> /var/log/mythtv not being created in a frontend-only install has been present since at least 8.04. Not sure why it's so hard to fix...

As you say, though, it's just a case of manually creating it.

For future reference, the logs get chucked in /temp if this folder isn't present, but this folder is cleared each boot.

It's hard to fix because every single frontend-only install i've done from a mythbuntu disk has resulted in the folder being created. Give me exact steps to reproduce it (as I have never reproduced the issue) and we might be able to fix it.

---

### Post by SiHa on 2010-09-21
OK, that sounds like a challenge to me. I'll give it a go when I get a chance. Myth is on a bit of a back-burner right now, as I just don't have time for all the shenanigans when it decides to just stop working after no changes from me. I've actually just bought a Hummy <ducks>

BTW, don't take it personally. I filed a bug way back when, but was never asked for more info.

---

### Post by tgm4883 on 2010-09-21
> **SiHa said:**
> OK, that sounds like a challenge to me. I'll give it a go when I get a chance. Myth is on a bit of a back-burner right now, as I just don't have time for all the shenanigans when it decides to just stop working after no changes from me.

BTW, don't take it personally. I filed a bug way back when, but was never asked for more info.

Didn't take it personally. I would like to get it fixed but cannot if I can't reproduce it.

---

### Post by SiHa on 2010-09-21
OK, I'll have a stab.

What's weird is that every frontend-only install I've ever done has had the fault...

---

### Post by tgm4883 on 2010-09-21
> **SiHa said:**
> OK, I'll have a stab.

What's weird is that every frontend-only install I've ever done has had the fault...

Ok, then I'd recommend going through an install and documenting every setting you choose. I'll try to reproduce here locally. Might also be benefitial to note what hardware you have or if it also works in a virtual machine.

---

