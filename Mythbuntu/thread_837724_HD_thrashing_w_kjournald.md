---
title: "HD thrashing w/ kjournald"
date: 2008-06-22
forum: Mythbuntu
---

### Post by lingenfr on 2008-06-22
Over on the kubuntu forum some folks with a problem similar to mine seem to have narrow the problem down to mythtv or one of it's dependencies. My HD is constantly accessed while my computer is on. When I run 'top' kjournald is nearly always on top (no pun intended). Several other folks found that when they removed mythtv that fixed it. Is there anything less drastic? 

It seems to be a discussed if not known problem? This box is a remote backend/frontend. When I kill the backend process, the disk thrashing stops. Anyone know a solution?

---

### Post by laga on 2008-06-23
Can you start by posting your backend log?

---

### Post by lingenfr on 2008-07-07
laga, good point. I really wasn't using the remote backend on this machine anymore, so I went into mcc and just changed the role to a frontend. Problem solved.

---

### Post by banewman on 2008-07-29
The hd thrashing is kjournald writing to the backend log - check the size of it - it will be huge!:)

---

### Post by lingenfr on 2008-07-30
I didn't have time to fool with it. I really didn't need mythbackend loaded, so I just removed it. That took care of the problem.

---

### Post by nuclearwasted on 2008-10-18
I was having the same problem. It seems mythbackend had the wrong password for the database and so (as mentioned) the log file was being written continuously. A quick tail of the log file revealed the problem.

---

