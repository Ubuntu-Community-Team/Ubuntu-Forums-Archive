---
title: "another boinc problem"
date: 2010-05-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2010-05-22
I have just completed moving to my primary backup OS, not due to failure of the OS but due to a failure of boinc.

I have 6.10.52 installed there (...56 here).  I was about to change over there to 56 when my system crashed (yesterdays updates were FUN).  I had one WU that didn't do any work but is marked "complete" and another that finished but will not upload.

The one that will not upload appears to make it so that no communication takes place.  Therefore no new WUs.  Therefore none of the others, more than 24hrs worth will report.

There is an error listed that says something about an element of the WU not being there.

Is there a way that anyone is aware of to salvage this?  I hate to waste the cycles and cause someone else to have to redo the ones I have already completed.

The user name here is the same.  WCG thinks it is the same device.  I have thught of just moving the good, completed and uplaoded (ready to report)  from the /Boinc/projects/www.worldcommunitygrid.org file over to that same file here but do not want to bugger this one.

Then I could just wipe that boinc out and reinstall and start over.  Actually, just copy this one over to there and go on without a problem.

I would just like to save the work done somehow.

---

### Post by Tea4all on 2010-06-13
Did you already run ```
sudo dpkg --configure -a
``` to complete the upgrade?

---

### Post by autocrosser on 2010-06-13
Well my friend---if the /.BOINC Manager master file has been b0rked, you are pretty well done...that is the file that BOINC used to sync everything---best thing is to salvage everything you can & move on---I stop BOINC if there is something that requires a major portion of my systems CPU & restart it after I am done...that's the only way you can be sure that your units stay intact in a uncertain environment....

BOINC was never designed to be running in a testing system--it was designed to be the only testing part of a stable system....So once again we push the envelope as far as possible (and maybe a "bit" too far :)  ).....

---

### Post by ranch hand on 2010-06-13
An upgrade was not the problem.  The problem was a lack of communication between may install and the World Community Grid servers caused by a crash.

I finally just abandoned the WUs and reinstalled a newer version.

I do not use the repo version and it is all installed in the home folder.  That way when one of these alpha buggers takes a dive I can just grab one folder and put it on another and be up and running again instantly.

What I wanted to do was to transfer the old WUs to a new install but they were corrupted.  I have done that with good ones to see if it worked and it should.

The interesting thing is that the buggers never showed up as "late" or "no reply" in the results status files.  They just kind of disappeared.  I guess they were really toasted.  It was a hard crash.

I really do need to reinstall again because I like their testing versions and right now I am on the newest stable which is considerably newer than the one in the 10.10 repo (repo=6.10.17 mine=6.10.52).  Actually now that I look I see that what I thought was testing, 6.10.56 is now stable and the new one, 57, is not available for Linux yet.  I am behind and need to catch up.

---

### Post by ranch hand on 2010-06-13
> **autocrosser said:**
> Well my friend---if the /.BOINC Manager master file has been b0rked, you are pretty well done...that is the file that BOINC used to sync everything---best thing is to salvage everything you can & move on---I stop BOINC if there is something that requires a major portion of my systems CPU & restart it after I am done...that's the only way you can be sure that your units stay intact in a uncertain environment....

BOINC was never designed to be running in a testing system--it was designed to be the only testing part of a stable system....So once again we push the envelope as far as possible (and maybe a "bit" too far :)  ).....
Yup, it was totally screwed.  One of those unexplainable crashes.  I wasn't doing anything, wasn't even in the room.

System not only froze but went to a black screen.  Nothing worked, had to unplug the bugger to reboot.

I really like the 52 model but want to get the 57 when it comes out for Linux.

On my stable system that I run at night (9.04) the version is a lot older and, while stable, I don't like the way it works (9.04 repo install).  One of these days I am going to see if I can clear it and do a "real" install and go with a new stable version.

---

