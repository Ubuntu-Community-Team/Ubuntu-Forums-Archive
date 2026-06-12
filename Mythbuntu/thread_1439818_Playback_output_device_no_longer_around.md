---
title: "Playback output device no longer around?"
date: 2010-03-26
forum: Mythbuntu
---

### Post by kdx7214 on 2010-03-26
Normally I'd go to setup under playback and pick the output device.  I'm using the 10.04 beta and the playback device is gone so I'm trying to figure out how to make the video show on my Hauppauge PVR 350.

Any ideas out there?

---

### Post by nickrout on 2010-03-28
> **kdx7214 said:**
> Normally I'd go to setup under playback and pick the output device.  I'm using the 10.04 beta and the playback device is gone so I'm trying to figure out how to make the video show on my Hauppauge PVR 350.

Any ideas out there?

Is the 350 still supported as an output device? I had a feeling it was disappearing.

---

### Post by iamlindoro on 2010-03-28
Correct, PVR-350 output code was removed for .23.  If you want to use the PVR-350 output, you should use the X.org driver for it.

---

### Post by kdx7214 on 2010-03-30
Can you explain how to do this?  I've installed the package from the repository but it still runs X off the lcd panel instead of the framebuffer.  Plus, mythtv no longer outputs to the mpeg-2 decoder so it's slower than heck.

I'd love an answer, and barring that, I'll take what the last version of Mythbuntu that supported MythTV 0.21 and stuff was.

I *did* try Mythbuntu 8.something but it would not boot afterwards.

Thanks!
Mike

---

