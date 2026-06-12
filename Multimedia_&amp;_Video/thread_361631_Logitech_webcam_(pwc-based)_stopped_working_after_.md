---
title: "Logitech webcam (pwc-based) stopped working after recent security update"
date: 2007-02-14
forum: Multimedia &amp; Video
---

### Post by kickaha on 2007-02-14
Hi all,

I was advised by the update manager to install a dozen or so security updates last week, and, following that update, my Logitech QuickCam Pro 4000 stopped working.

When I try to access it in any application (ekiga, camstream, etc.), I get a 50% grey (approx. :) ) box, and no picture.

I'm running the 2.6.17-11 kernel. I haven't done anything with the kernel or drivers. pwc is running, and the driver chain I would expect to see is there. I have another webcam (creative, spca5xx-based) that is working correctly. I did a couple of searches in here, and didn't see anything related to my issue...

Thanks for any info. My apologies if I just missed it in the forum.

Cheers!

---

### Post by kickaha on 2007-02-14
Ok, ok. I should have looked harder.

Bug #56090:
Regression: Webcams using pwc driver produce all-grey images

Sorry for any trouble. If anyone else encounters this, there's a couple of different work-arounds in the bug-tracker.

---

