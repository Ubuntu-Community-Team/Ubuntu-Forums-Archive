---
title: "Confused on weekly builds for gutsy"
date: 2008-05-19
forum: Mythbuntu
---

### Post by eagle63 on 2008-05-19
Ok, so I've got a normal desktop installation of Gutsy on which I run my mythtv backend.  This was formerly a Feisty install that I since upgraded to Gutsy.  In my /etc/apt/sources.list.d/, I've got a "mythbuntu-feisty.list" file which points to the mythbuntu weekly builds for feisty.  This, however, gets me no higher than Myth .20.2 fixes, so if I want to go to .21 (without upgrading to Hardy) I need to change this entry right?

I tried changing the filename to mythbuntu-gutsy.list, and made it point to:
```
deb http://weeklybuilds.mythbuntu.org/mythbuntu/ubuntu gutsy multiverse universe restricted main 
```

However, now when I open Ubuntu's update manager, it warns me that "Not all updates can be installed.  Run a partial upgrade to install as many updates as possible." 

So what exactly did I do wrong here?  If I close the warning popup and scroll through the list of available updates I can see version .21-fixes for what appears to be all of the relevant myth packages.  Thanks in advance!

---

### Post by .nedberg on 2008-05-20
Might have to do with mytharchive / mythvideo. I don't think mytharchive is needed in 0.21. Just remove that one if it is installed.

---

### Post by FuturePilot on 2008-05-20
Try using Synaptic to apply the updates.
Usually that error means something has to be removed. Update-manager cannot remove packages.

---

### Post by eagle63 on 2008-05-20
Thanks guys, I'll try doing this through Synaptic.  But basically the line I added in /etc/apt/sources.list.d/ looks correct?  Should I also have a line for "gutsy-backports"?

---

### Post by ian dobson on 2008-05-23
Hi,

So does anyone know when the .21-fixes will be comming out for Hardy? I'm having afew memory leaks in mythbackend on some DVB-C channels see [http://ubuntuforums.org/showthread.php?t=800023](http://ubuntuforums.org/showthread.php?t=800023) .

If I add 
deb [http://weeklybuilds.mythbuntu.org/mythbuntu/ubuntu](http://weeklybuilds.mythbuntu.org/mythbuntu/ubuntu) hardy multiverse universe restricted main
To my souces.list I see updates for myth-frontend etc.

Regards
Ian Dobson

---

### Post by laga on 2008-05-23
Try the .uk mirror.

---

### Post by ian dobson on 2008-05-23
Hi laga,

my question is more, is it safe to use the fixes branch. I used the fixes branch in gutsy without any problems, but the Mythbuntu web page still says that when the fixes branch is released they'll update the page.

Regards
Ian Dobson

---

### Post by mrand on 2008-05-23
> **ian dobson said:**
> Hi laga,

my question is more, is it safe to use the fixes branch. I used the fixes branch in gutsy without any problems, but the Mythbuntu web page still says that when the fixes branch is released they'll update the page.

Regards
Ian Dobson
Also confusing is the statement on the [http://www.mythbuntu.org/downloads](http://www.mythbuntu.org/downloads) page:
> The upgrade procedure will only upgrade Mythbuntu packages if you don't have a Gnome or KDE desktop installed. What does this mean?  What procedure must be followed to properly upgrade if you do have Gnome desktop installed somewhere on the system?

[INDENT]Marc[/INDENT]

---

