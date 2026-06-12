---
title: "Frontend Crash During Recorded Playback"
date: 2009-11-20
forum: Mythbuntu
---

### Post by zosoMythbuntu on 2009-11-20
I am having an issue where Mythtv Frontend crashes during playback of a recorded show.   I am running Mythbuntu 9.10. At some point during playback (it varies in time) Mythtv will close and take me back to the desktop.  I can open the frontend again, but it will crash again and not in the same spot.

Here is what I have found out in my own troubleshooting:
 - I can make this happen much faster by pushing the 3x fast forward button.  It only takes 1-2 minutes when I do that as opposed to 15-40 minutes at normal speed.
 - I can watch the same video in VLC and it will not crash even if I speed it up to 3x fast forward.
 - This does not happen on my remote/dedicated frontend.  It only happens on my backend/frontend machine, which is a computer I just built.
 - I did a fresh install of Mythbuntu on this computer this morning and it still does this.
 - I switched nVidia drivers from 185 to 173 and it still does this.

Any help would be much appreciated.  Let me know if you need more information.

---

### Post by zosoMythbuntu on 2009-11-20
I think I may have fixed this problem by simply changing the BIOS settings from Fail Safe Defaults to Optimized Defaults.  I have it set on 3x and it has been going for almost 20 minutes strait.  That is by far the longest it has gone.

I'm calling this one solved, for now.

---

