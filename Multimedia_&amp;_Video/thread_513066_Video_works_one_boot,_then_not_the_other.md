---
title: "Video works one boot, then not the other?"
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by jmchaffie on 2007-07-30
Ok, this is a total new one for me. I've tried getting a response with no luck so I'm changing verbiage here.

Installation of Ubuntu feisty goes great and runs fine.
Install nvidia restricted drivers, reboot and runs fine.
Turn off pc, come back later, boot up and no video. 
 -- HOWEVER - pc is actually ok, I can alt-F1 to command no problem
 -- also, where you would normally login to the gui, you can still do so blindly... still hear the lgoin sounds, etc. so the gui session is not dead... just as if the sync was out of range perhaps.


Here's the kicker to the whole thing...

I can revert to my basic vesa xorg.conf.
restart the x-server, re-install the restricted drivers, reboot, and violla!! it all works again!

So I'm a bit confused how it could just be a refresh rate issue or something like that if it works the first time around.

I'm at a loss here. Anyone have a similar issue they've resolved?

Thanks

---

### Post by jynyl on 2007-07-30
Perhaps there is a module that is not getting loaded on boot up?

(I'm using the driver from the nvidia run file on Kubuntu 7.04, so not familiar with your setup.)

HTH

Peter

---

