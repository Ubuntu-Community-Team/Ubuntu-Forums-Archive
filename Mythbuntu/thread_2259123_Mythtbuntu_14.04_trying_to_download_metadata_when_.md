---
title: "Mythtbuntu 14.04 trying to download metadata when not required"
date: 2015-01-02
forum: Mythbuntu
---

### Post by ceesquared on 2015-01-02
I have unchecked download metadata in BE setup but it still tries to download. This is a known bug, but I am looking for a fix. My box does not have internet connection so this bug prevents auto shutdown as looking up metadata is pending in the job queue. Could I replace mythmetadatalookup with a script that returns status 0 so that the backend thinks that metadatalookup is complete and closes down the job?

---

### Post by tgm4883 on 2015-01-02
> **ceesquared said:**
> I have unchecked download metadata in BE setup but it still tries to download. This is a known bug, but I am looking for a fix. My box does not have internet connection so this bug prevents auto shutdown as looking up metadata is pending in the job queue. Could I replace mythmetadatalookup with a script that returns status 0 so that the backend thinks that metadatalookup is complete and closes down the job?

Can you link to the bug?

---

### Post by ceesquared on 2015-01-05
Bug ticket is at [https://code.mythtv.org/trac/ticket/11878#ticket](https://code.mythtv.org/trac/ticket/11878#ticket)
A further thought, if I ignore code 35 in shutdown check(job pending or running) would that stop advert detect from completing? If not, then this is another possibility.

---

### Post by ceesquared on 2015-01-27
I think I have found the fault and have a solution. The job settings in setup are not transferred to the default recording profile. To cure the problem go to FE > manage recordings > recording rules and find default . Open this up and uncheck lookup metadata. Solved.:D

---

### Post by JimLS on 2015-02-19
I am not able to go to the metatdata selection for the default recording rules, only for specific rules.  When moving around on the default rules page it skips over several selections near the bottom including metadata.  I have disabled metadata in the BE.  How do I disable it in the default rules in the FE?  I am having errors in metadata download that clog the job queue and want to disable it completely.

---

### Post by JimLS on 2015-02-19
Was just looking in the wrong place.  It is under "post processing" not "metadata options".

---

