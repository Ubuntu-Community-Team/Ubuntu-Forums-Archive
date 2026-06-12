---
title: "volume unaffected by XF86Audio*Volume"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by KhaaL on 2007-10-16
The situation is as follows:

When I press the volume up media button on my keyboard, the volume bar shows that the volume has changed to 11%, but it dosen't go past that. If i lower it with the other media button, the volume bar shows 0% - but! - the sound is still intact. I can however change the volume with scrollwheel at Kmix' icon in the taskbar...

Now I've tried changing the master channel to front instead of PCM, but still not luck. the behaviour is the same. If I use another keycombination, say, Win+J, then the volume can be raised without a problem. However, the volume bar dosen't show up. 

Now, the volume bar I can live without... but I *really* need to have my volume buttons working... help would be much appriciated!

---

### Post by k0rb0 on 2007-10-18
Had the same problem
I removed kmilo and hotkey-setup with apt, and then I setted myself the hotkey in kmix
There is no display of the volume anymore(when i fn+up), but the volume changes :)

---

### Post by KhaaL on 2007-10-19
> **k0rb0 said:**
> Had the same problem
I removed kmilo and hotkey-setup with apt, and then I setted myself the hotkey in kmix
There is no display of the volume anymore(when i fn+up), but the volume changes :)

Works! thanks for the tip, I was worried Noone would be able to help me on this :)

---

### Post by brazzmonkey on 2007-10-19
nice trick indeed.
but this bug is a regression. have you filed it yet ?

---

### Post by KhaaL on 2007-10-19
No i've not, I'm embarrassed to say that I'm not familiar with how to file bugs in launchpad...
I'll look into how to do it and post once a bug report is filed

Edit: Yep, a bug report was already filed at:
[https://bugs.launchpad.net/ubuntu/+source/kdeutils/+bug/127082](https://bugs.launchpad.net/ubuntu/+source/kdeutils/+bug/127082)

---

### Post by brazzmonkey on 2007-10-20
alright, waiting for a fix then. good thing k0rb0 told us his trick&#8230;

---

