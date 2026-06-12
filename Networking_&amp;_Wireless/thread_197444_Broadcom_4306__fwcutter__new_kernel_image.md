---
title: "Broadcom 4306 / fwcutter / new kernel image"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by jawrat on 2006-06-15
new kernel installed and voila, no more wireless via broadcom 4306.

so, says i, i must have to redo the firmware cutter thingy.  well, it was easier than that.  i just had to copy th3 bcm43xx files over from /lib/firmware/{old kernel rev} over to /lib/firmware/{new kernel rev}.  then it was a simple matter of rmmod bcm43xx and modprobe bcm43xx and poof, back to happy wireless land.  

this is not a report of a problem, just a heads up for those who may not realize the simplicity of the fix, since the kernel image came in through the update manager.

---

