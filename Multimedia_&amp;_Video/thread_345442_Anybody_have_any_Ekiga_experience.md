---
title: "Anybody have any Ekiga experience?"
date: 2007-01-24
forum: Multimedia &amp; Video
---

### Post by kix on 2007-01-24
I have Ekiga running under the default user (admin privilages), the webcam works fine and connects to other SIP addresses.  When running Ekiga under a different user account (desktop user), the webcam is never detected, but the webcam microphone is listed as an audio source.

Has anybody elese seen this?  It looks like a permissions problem, but which bits do I need to reset?

Can't seem to find anything similar listed on the forums.

Thanks

---

### Post by kix on 2007-02-02
Worked this out now.  Added Wengophone and it had the same problem, no video for anybody other than default user.

chmod 666 /dev/video0

Sorted.

---

### Post by danielph on 2007-02-11
A cleaner solution is to add the user to the video group.

---

