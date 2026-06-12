---
title: "HVR-1600 driver loading problem"
date: 2008-10-09
forum: Mythbuntu
---

### Post by agent211 on 2008-10-09
When the machine first comes up, the card comes up as /dev/video0.  The backend will not be able to open the device, though.  (This is apparent in the mythbackend log also)  If I go into the Hardware Drivers GUI and disable and re-enable the driver, the card will come up as /dev/video1 and the backend has no problems.  I've scoured every forum I can find and apparently I'm the only person with this problem.  Please help.

---

### Post by dagar on 2008-10-09
[http://ubuntuforums.org/showthread.php?t=850841]("http://ubuntuforums.org/showthread.php?t=850841")

Try this thread.  I followed that and got the analog to work.

---

### Post by agent211 on 2008-10-09
Thanks, but that pretty much installed the driver and firmware that I already had.

UPDATE:  I reinstalled driver/fw using first method I tried from mythtv wiki and it just works now.

[scratches head, notices not much hair left (figuratively)]

---

