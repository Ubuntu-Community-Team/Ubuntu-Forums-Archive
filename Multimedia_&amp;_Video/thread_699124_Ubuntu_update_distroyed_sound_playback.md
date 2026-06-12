---
title: "Ubuntu update distroyed sound playback"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by jpe2000 on 2008-02-17
Today, when I had that update icon, I updated it...thinking it was just some usual thing...I get everything up to date as soon as the updates come out.

Anyway, I've noticed that now I have NO audio playback whether it's from the start up sound to something from youtube, I have NO sound!!!

I don't know what happened...I found out that when I turn the volume up really high, you can hear the sound barely with a lot of static. This NEEDS to be fixed immideatlly! I know I have done nothing but update the dang thing...PLEASE, someone help me find a fix for this...

The date was February 16, 2008. I'm using Ubuntu 7.10 on a Dell Dimension 8400.

---

### Post by xc3RnbFO8P on 2008-02-17
Try this:
> 
sudo aptitude install linux-backports-modules-generic

---

### Post by Steah on 2008-02-17
I also had a recent update cause sound trouble.  After updating and rebooting it can no longer find any soundcards.  It screwed up a lot more than that, unfortunately... but that is off topic.

Prior to the update I had no troubles with sound card detection, afterwards it doesn't see the onboard sound card which it was using just fine a few minutes before.

$ dmesg | grep sound
[   26.058871]   No soundcards found.

Is there a decent way to determine which updates were done from the command line?  Similar to looking in the "History" of Synaptic, but accessible from outside the X server?

---

### Post by jpe2000 on 2008-02-17
Thanks Ringi...well, it seems like I'm not the only one with this problem...

Thanks though.

---

### Post by jpe2000 on 2008-02-17
That didn't work...anybody else have any ideas?

---

