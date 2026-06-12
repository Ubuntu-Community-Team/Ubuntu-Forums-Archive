---
title: "Weird ATI vide playback corruption"
date: 2010-12-07
forum: Mythbuntu
---

### Post by GuiGuy on 2010-12-07
I've had to rebuild my main mythbuntu backend/frontend after the motherboard died. The replacement is ATI/AMD.

When I install the ATI driver video playback works in all applications (Xine, VLC, mplayer) except the MythTV Internal player.

The result's difficult to explain; the video is displayed twice; one display occupying the top half of the screen, the other the bottom half. Seems like some some sort of synchronization issue. 

If I remove the ATI proprietary driver the Internal player will display correctly.

Any thoughts?

---

### Post by iamlindoro on 2010-12-07
Use a playback profile which does not use the Bob2x deinterlacer.

Utilities/Setup->Setup->Tv Settings->Playback, Page Three, change the profile from whatever you have it set to (likely CPU+) to "Slim."  Press Next until you can press "FInish."  Press Finish.

---

### Post by the_pod on 2010-12-07
> **iamlindoro said:**
> Use a playback profile which does not use the Bob2x deinterlacer.

Utilities/Setup->Setup->Tv Settings->Playback, Page Three, change the profile from whatever you have it set to (likely CPU+) to "Slim."  Press Next until you can press "FInish."  Press Finish.

Good stuff. I've always just turned off the deinterlacer.  So other deinterlacers will work, just not the Box2x?

---

### Post by GuiGuy on 2010-12-07
> **iamlindoro said:**
> Use a playback profile which does not use the Bob2x deinterlacer.

Utilities/Setup->Setup->Tv Settings->Playback, Page Three, change the profile from whatever you have it set to (likely CPU+) to "Slim."  Press Next until you can press "FInish."  Press Finish.

Of course. I didn't even look at that. 

Many thanks.

---

### Post by GuiGuy on 2010-12-08
> **iamlindoro said:**
> Use a playback profile which does not use the Bob2x deinterlacer.

Utilities/Setup->Setup->Tv Settings->Playback, Page Three, change the profile from whatever you have it set to (likely CPU+) to "Slim."  Press Next until you can press "FInish."  Press Finish.

To confirm that this worked (I should have known :oops:)

Again, many thanks

---

