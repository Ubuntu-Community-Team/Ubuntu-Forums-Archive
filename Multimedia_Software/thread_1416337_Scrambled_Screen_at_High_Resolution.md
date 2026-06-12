---
title: "Scrambled Screen at High Resolution"
date: 2010-02-26
forum: Multimedia Software
---

### Post by gameshints on 2010-02-26
I have Ubuntu 9.10.

I have an old IBM Thinkpad X40 laptop in which I plugged a relatively old flat screen monitor (Protron 15") into.  

They started out mirrored at a resolution of 1024 x 768.

I wanted to have dual screens, so I unchecked the box in the display settings, and both monitors become scrambled!  (Orange boxes all over the place).

There are a couple weird things about this:
1) The mouse is still there, and I can move it across both monitors, and it is NOT scrambled like the rest of the screen.
2) Changing the resolution of the second monitor down to 800 x 600 works fine, but my monitor supports 1024 x 768 just fine... and it works when the screens are mirrored.

Any suggestions?

---

### Post by hxcobd on 2010-02-26
I had the exact same problem. I use a Thinkpad X41.

I ended up solving it simply by updating all of the packages involved with xorg.conf. I believe it was actually an Update Manager update. After the update, the problem stopped occurring.

I restarted a few times as well. Definitely didn't edit xorg.conf at all or anything, the fix was really self-explanatory.

---

### Post by gameshints on 2010-02-26
The Update Manager says everything it up to date.  Anything specific I need to do to update Xorg stuff?

---

