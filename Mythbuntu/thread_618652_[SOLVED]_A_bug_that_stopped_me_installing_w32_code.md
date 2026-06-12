---
title: "[SOLVED] A bug that stopped me installing w32 codecs etc for a while"
date: 2007-11-20
forum: Mythbuntu
---

### Post by ubnewbie2 on 2007-11-20
I was trying to use MCC to install the extra codecs. I'd tick them them click on apply, a download dialog would very briefly appear, then go away.  Restarting MCC showed they had not been installed.

I decided to try synaptic. I searched for codecs and found a likely package.  When I tried to install, it asked for the install CD to be put in the drive.  I got to wondering whther this is what MCC needed, so I cancelled synaptic, put the CD in the drive, and started MCC.

This time it installed the codecs - no problems.

So, seems like MCC should be testing for the CD and asking for it first.

---

### Post by superm1 on 2007-11-20
Yeah this bug crept up at the very last moment (CD repositories were the last commit).  It's been reported, and we should have a resolution for hardy at least.

---

### Post by ubnewbie2 on 2007-11-20
> **superm1 said:**
> Yeah this bug crept up at the very last moment (CD repositories were the last commit).  It's been reported, and we should have a resolution for hardy at least.

Great, and thanks for the confirmation.

---

