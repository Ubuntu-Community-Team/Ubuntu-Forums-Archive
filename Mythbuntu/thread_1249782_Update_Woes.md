---
title: "Update Woes"
date: 2009-08-25
forum: Mythbuntu
---

### Post by Freddie on 2009-08-25
Hi all,

I have a 9.04 mythbuntu system. A few months back in July when I did an upgrade, I found that all sound would be duplicated from mythfrontend, albeit slightly out of sync. I have no idea why.

I fixed this by changing the audio output to /dev/dsp. Not as nice as ALSA, but it worked.

Now I did an update a few days ago and since then audio in mythfrontend often goes out of sync, by several seconds. It happens more so when one pauses or skips a recording. Other frontends do not exhibit this.

The update in question contained a kernel upgrade. However, the kernel never worked properly (it seemed like all modules broke), so I had to revert it by editing menu.lst.

Does anyone have *any* idea what could be causing this mess?

Regards, Freddie.

---

