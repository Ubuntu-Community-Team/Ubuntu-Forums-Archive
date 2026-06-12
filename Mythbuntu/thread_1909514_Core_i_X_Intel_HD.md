---
title: "Core i X Intel HD"
date: 2012-01-15
forum: Mythbuntu
---

### Post by williammanda on 2012-01-15
If anyone currently uses the core I series and the built in HD graphics with Mythtv, please state your results and setup.
Thanks

---

### Post by nickrout on 2012-01-15
Is that SandyBridge? If so, the hardware acceleration is only accessible via vaapi, not vdpau.

vaapi will not be supported until 0.25, but there have been reports of it working well with the  git master code (which will become 0.25 when finished.

However intel's acceleration is not as mature, or apprently as good, as vdpau.

Then again a decent core iX processor should be able to do most decoding on the cpu, so it may not matter.

---

