---
title: "HDHomeRun scan produces duplicate channels"
date: 2010-11-17
forum: Mythbuntu
---

### Post by Explodinglemur on 2010-11-17
Ubuntu 10.04, MythTV 0.23.0+fixes24158-0ubuntu2.

When performing a channel scan (us-cable/QAM256), there is no option to set a channel/PID separator.

After the scan, MythTV reports "Found X new non-conflicting SCTE channel(s)", and then "Found Y new conflicting SCTE channel(s)".  When I have it insert the conflicting channels it asks for me to enter a unique channel number.  When looking at the channel list, it appears to have populated the channels with only the PIDs, rather than channel number/separator/PID (such as 261 instead of 72_261).

Anyone know how to get the scanner to create the channel numbers properly?

---

### Post by iamlindoro on 2010-11-17
Upgrade to .23.1 from the auto-builds.  Alternately, upgrade to .24 from the autobuilds.  Rescan.  the channel numbering conflicts issue has been fixed.

---

### Post by Explodinglemur on 2010-11-18
> **iamlindoro said:**
> Upgrade to .23.1 from the auto-builds.  Alternately, upgrade to .24 from the autobuilds.  Rescan.  the channel numbering conflicts issue has been fixed.

Upgrading to 0.23.1 did indeed fix it.  Thanks!

---

