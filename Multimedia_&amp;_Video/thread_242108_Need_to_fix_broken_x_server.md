---
title: "Need to fix broken x server"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by secdroid on 2006-08-23
- Ubuntu Dapper desktop (Intel), updated to current
- X server worked yesterday, won't start today
- Fedora (dual-boot) on same machine working normally
- No updates or reconfiguration obvious cause of prob
- Don't know how to reconfigure/correct prob
 
- tail /var/log/Xorg.0.log results
--- (II) ATI: Candidate "Device" section "ATI Technologies, Inc. Rage 128 PF/PRO AGP 4x TMDS"
--- (EE) No devices detected
--- Fatal server error.
--- No servers found

Help!!!

---

### Post by tkjacobsen on 2006-08-23
There has been some problems with the updated version of x. See this link: [http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

---

### Post by secdroid on 2006-08-23
Troels, thank you very much!

I saw the xserver-xorg-core update to 10.3 yesterday, but didn't hink of it as the cause of the problem.

Next time, I'll check the sticky threads first...  

Much appreciated.

---

