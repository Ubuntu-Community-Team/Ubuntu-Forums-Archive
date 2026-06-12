---
title: "Intermittent MultiRec Failure on HD-5500 After Upgrade to 12.04"
date: 2012-09-18
forum: Mythbuntu
---

### Post by jamoody on 2012-09-18
I've recently upgraded from 11.04 to 12.04 and I now get intermittent recording failures which prevent all future recordings until reboot.  I've deleted all tuners and re-added them after the upgrade with no change.  

Several dozen MultiRec recordings will happen just fine, and then a recording gets "stuck" on a tuner and all future recordings on any tuner seem to not get dispatched.  Several hours after the recording should have ended the "stuck" recording is still shown as green in Previous Recordings list along with status O, implying it is still recording, but no file is created; missed recordings don't show in the Previous Recordings list at all.  After reboot the missed recordings show as red with status M in the Previous Recordings list.

So far all failures have occurred only on HD-5500 (2 different systems) and only when MultiRec>=2.  HDHomeRun with default MultiRec=2 so far has not shown the problem.  Also HD-5500 with MultiRec=1 (no MuntiRec) has not shown the problem.

I can't see anything in the mythbackend.log to help identify a problem.  Suggestions?

---

### Post by nickrout on 2012-09-18
> **jamoody said:**
> I've recently upgraded from 11.04 to 12.04 and I now get intermittent recording failures which prevent all future recordings until reboot.  I've deleted all tuners and re-added them after the upgrade with no change.  

Several dozen MultiRec recordings will happen just fine, and then a recording gets "stuck" on a tuner and all future recordings on any tuner seem to not get dispatched.  Several hours after the recording should have ended the "stuck" recording is still shown as green in Previous Recordings list along with status O, implying it is still recording, but no file is created; missed recordings don't show in the Previous Recordings list at all.  After reboot the missed recordings show as red with status M in the Previous Recordings list.

So far all failures have occurred only on HD-5500 (2 different systems) and only when MultiRec>=2.  HDHomeRun with default MultiRec=2 so far has not shown the problem.  Also HD-5500 with MultiRec=1 (no MuntiRec) has not shown the problem.

I can't see anything in the mythbackend.log to help identify a problem.  Suggestions?

Are you using latest 0.25-fixes (available via mythbuntu repos)

---

### Post by jamoody on 2012-09-18
> **nickrout said:**
> Are you using latest 0.25-fixes (available via mythbuntu repos)

Latest as of 9/12 (MythTV v0.25.2-15)

---

### Post by nickrout on 2012-09-18
> **jamoody said:**
> Latest as of 9/12 (MythTV v0.25.2-15)I am on v0.25.2-19-gcf06841 (package name 0.25.2+fixes.20120911.cf06841 indicating it is from 11/9 (how odd I didn't even notice that infamous date had gone by), so you are at least 4 commits behind. However that is still reasonably up to date).

Sounds like a kernel error to me, but I may be wrong. Have you looked in the backend logs and/or the kernel logs?

I think you would have more luck diagnosing this on the mythtv-users mailing list.

---

### Post by jamoody on 2012-11-01
An update to MythTV 0.25.3 seems to have corrected the problem.

---

