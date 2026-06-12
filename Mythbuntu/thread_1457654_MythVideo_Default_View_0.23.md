---
title: "MythVideo Default View 0.23"
date: 2010-04-18
forum: Mythbuntu
---

### Post by uncle hammy on 2010-04-18
I have been pulling my hair out on this one.  There used to be an option under Media Settings>Videos Settings>General to set the default view (Gallery, Browse, etc).  I can't find it to save my life with 0.23.  Anyone know where it got to?

---

### Post by My Name on 2010-04-19
Does it not remember the last view setting? It's just a thought...

---

### Post by uncle hammy on 2010-04-19
No, it doesn't.  When I couldn't find it anymore, I thought maybe it had been changed to do so, but no.

---

### Post by iamlindoro on 2010-04-19
> **uncle hammy said:**
> No, it doesn't.  When I couldn't find it anymore, I thought maybe it had been changed to do so, but no.

Actually, it does.  Unfortunately after it was changed to do so, someone broke the set/clear settings code, so right now to see the effect on the "default" you need to restart the frontend.  That is, change the view and restart the frontend, and you will find that it is now set to whatever you changed it to.  We'll get the settings bug fixed in the next few days and push a fix to .23.  As long as you have auto builds enabled you should see it there once we get it fixed.  But yeah, basically the metadata browse modes and views persist upon a change instead of some wacky obscure hidden setting.  It's better this way (when it works).

---

### Post by uncle hammy on 2010-04-19
10-4, thanks for the heads up.

---

### Post by iamlindoro on 2010-04-19
> **uncle hammy said:**
> 10-4, thanks for the heads up.

Fixed and backported.  Probably too late for whenever ubuntu builds nightly packages, so for those running auto-builds, should show up within 48 hours.

---

### Post by My Name on 2010-04-20
Wow! cracking guess!!! :P

---

