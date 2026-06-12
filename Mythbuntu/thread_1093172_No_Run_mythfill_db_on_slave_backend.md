---
title: "No Run mythfill db on slave backend"
date: 2009-03-11
forum: Mythbuntu
---

### Post by rodercot on 2009-03-11
So I have a questions and an observation or bug maybe.

 I have a master and slave backend, and I REMEMBER reading not to run a mythfill on the slave. Last night I had an issue with live tv on the slave (WHY can I not remember to hit i for insert when editing a file -DOH!)
 
 I setup on the master b/e to run mythfill db automagically once per week, Which does not seem to be happening by the way. BUT what I noticed when scrolling through the setup on the slave backend last night was that auto run mythfill db was also selected on the slave b/e. Is this being picked up from the master because I did not set this to happen on the slave b/e. I turned it off on the slave but have not checked the master to see if it is turned of there as well.
 
 Dave

---

### Post by newlinux on 2009-03-11
yes - I'm pretty sure that setting is a global setting. Some settings affect all machines, some are for the specific machine. It isn't always clear which ones are and aren't. I'll bet when you go to the master it will show as turned off as well.

As far as why it isn't running, have you looked in your logs? Is it not running, or is it failing when it runs?

---

