---
title: "intermittent error writing to Windows XP machine"
date: 2011-05-09
forum: Networking &amp; Wireless
---

### Post by philatnhs on 2011-05-09
OK, there is a lot I can not change in this situation.  I am running Ubuntu 8.04.  I can not change this.  It runs a commercial application and this version of the Ripper only works (supported) with this version of Ubuntu.
The software is a print ripper, using graphics files like Photoshop or Adobe illustrator to generate files that an industrial printer can use.  The controller for that printer, (and ultimate destination of these generated files,) runs windows XP.
We used to rip files locally to the Ubuntu box, then copy the resulting file to the XP machine.  This was a bit of a pain as each file runs about 4 gigs.  I have reconfigured everything so that the job is ripped directly to the XP box, and now we have a problem.
The log for the ripping software will sometimes show "Error writing data:bad file descriptor."  I am not sure exactly what this means, other than our job is not gonna go through.  We get this error as soon as the job starts, or not at all.  We may have to try three or four times, (though rarely more than twice,) before the job will run, but once it starts running, everything is fine, and 20 minutes or so later, we have a perfectly ripped file.
I have replaced NICs in both the XP machine and the Ubuntu machine.  Replaced all incidental cabling, and all switches between the two machines.  The only thing still the same is a main cable run between two parts of the warehouse, but we have a dozen machines running all networking through this same line, with no problem, so I do not think that this is an issue.
Anyone got a clue I can borrow?
Phil

---

