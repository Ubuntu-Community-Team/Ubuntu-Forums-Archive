---
title: "How to Backoff Fixes Using Update Manager"
date: 2012-02-17
forum: Mythbuntu
---

### Post by jamoody on 2012-02-17
If I apply Mythbuntu fixes via the Mythbuntu Control Center Update Manager, how can I back them off to a previous level if they cause me problems?  Is it relatively "safe" to apply Mythbuntu updates on a whim?

---

### Post by nickrout on 2012-02-17
As long as you stay with the 0.24 series of myth packages (ie up to 0.24.2-fixes) and don't change ubuntu release level (ie don't go from 10.10 to 11.04 etc) you should be fine.

---

### Post by jamoody on 2012-02-18
Should I ever have problems is there an "undo" procedure using Update Manager?  If not, can I save and restore certain directories?  Right now my backup procedure before updating is to clone the drive which is cumbersome and time consuming (3 hours for my 1T boot drive) so I don't apply MythTV fixes as often as I should.

---

### Post by jamoody on 2012-03-08
Is there anyway to back off fixes applied via Update Manager?

---

### Post by klc5555 on 2012-03-08
Kind of, sort of, using Synaptic, but Ubuntu certainly doesn't go out of its way to make it straightforward. See [http://ubuntuforums.org/showthread.php?t=1425849](http://ubuntuforums.org/showthread.php?t=1425849)  

Your drive cloning procedure may well be the most efficient rollback option available for this distro. To this end you might want to consider using a much smaller boot drive while keeping very large data storage drives. For my Mythtv machines, I usually have 2 to 4 large data storage drives in the 1T to 3T range, but for the OS/boot drive I'll usually use a drive in the 60 Gig to 160 Gig range.

---

