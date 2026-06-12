---
title: "intermittently no sound"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by DrObviousSo on 2007-06-27
I installed Fiesty a week ago or so.  I've been getting it going since then, and have been working my way from the big issues to the small ones since then.  I'm onto a problem that I haven't been able to find much help with via google, ubutntuguide.com, and searching this forum.

When I installed, I had sound, but the sound icon in the tray didn't do anything.  I could mute it or turn it all the way up, and it would have no effect either way.  In program volume controls like in rythembox or mplayer control their volume just fine.

Three times since then, when I've rebooted, I've had no sound.  The first time, 1 reboot gave me sound.  The second time, 2 reboots.  This last time, 4.

I assume this may be some kind of driver issue, but I really don't know how to get started on this.  Any help would be appreicated.

---

### Post by PaulFr on 2007-06-27
My intermittent sound problem was due to alsamixer mute/unmute- now any time I do not have sound, I check alsamixer (see **[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)** for some pointers)

---

### Post by DrObviousSo on 2007-06-27
well, I don't know if that fixed the problem or not, because there's no way to test it, but it might have.  I found out how to sync my sound control up with the correct channel, and have done so.

Thanks for your help!

---

### Post by dabl on 2007-06-27
I have also noticed that Firefox has a way of grabbing the sound output source, when it is run first, leaving the sound file player unable to produce an output.  Run Audacity or Amarok or whatever first, then run Firefox, and the player has the sound output. ;)

---

