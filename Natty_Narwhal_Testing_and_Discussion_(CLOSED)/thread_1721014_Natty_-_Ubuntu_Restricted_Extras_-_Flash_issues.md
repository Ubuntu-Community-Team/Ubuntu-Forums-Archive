---
title: "Natty - Ubuntu Restricted Extras - Flash issues?"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Orographic on 2011-04-03
Hi all,

Very pleased initially with Natty Beta 1 - it has improved on Alpha 3 for sure.

My issue:

I installed Beta 1, then did all of the updates as per usual. Next I installed Ubuntu Restricted Extras from Synaptic, all good initially. Upon restart, YouTube wouldn't play flash video and kept telling me that I needed to upgrade my Flash Player, both in Firefox and Chromium. 

My solution:

I uninstalled Ubuntu Restricted Extras via Synaptic but noticed Flash Player was still there so uninstalled it too. Then I re-installed Flash Player via Synaptic and all worked fine in FireFox. Then I re-installed Ubuntu Restricted Extras too. All good it seems.

Was this approach okay?

I've never had this issue before, usually installing Restricted Extras works perfectly. It worked fine in Alpha 3. Any ideas?

---

### Post by Orographic on 2011-04-04
I did a re-install of Natty with all updates and this time made a clonezilla image before installing Flash, just in case. This time I installed Ubuntu Restricted Extras without changing the software sources server in Synaptic to Internode (my Australian server) and all worked well with Flash in YouTube. 

Not sure what the issue was the first time around, it may have been changing the synaptic server to Internode, which I always usually do.

---

### Post by beew on 2011-04-04
Flash is already installed if you specifically check the box for restricted programs during OS install (youtube plays out of the box for me)

If you want up to date flash and optimization it is the same way you do with other Ubuntu's versions. Use the flash-aid addon for Firefox, it works in Natty as well. It is by far the best way to handle flash related issues.

---

