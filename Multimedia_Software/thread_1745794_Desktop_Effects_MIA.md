---
title: "Desktop Effects MIA"
date: 2011-05-01
forum: Multimedia Software
---

### Post by rivera151 on 2011-05-01
Hey guys.  I hope you are all enjoying Natty as much as I am.  I have an issue that I'm a little stumped on.  I can't remember if it was during Lucid or Maverick, but at some point I lost all my desktop effects.  When I open the Desktop Effects module under System Settings, under Compositing all I get is "Desktop effects are temporarily disabled."  Pressing "Resume Desktop Effects" does not turn them on successfully.  What's more strange, when I go into the "All Effects" tab, the list is unpopulated (empty), so even if the effects were enabled, I doubt I would be able to do anything with them.  Anyone experience something similar, or wanna take a stab at it.

Ricardo

---

### Post by dabl on 2011-05-01
I haven't seen it exactly as you described -- it sounds as though part of the kde desktop software suite is missing.

Open your GUI package manager (I like muon but you can use kpackagekit) and look at the packages starting with kdebase-bin.  You should have all of them except the -dbg packages installed, down through kdebase-workspace-kgreet-plugins.  Then there are some optional ones below that.

Another thing I would try, in a tty console after shutting down X with ```
sudo service kdm stop
``` is

```
sudo apt-get update && sudo apt-get install --reinstall plasma-desktop
```

Restart X with ```
sudo service kdm start
```

However, depending on the GPU that you have, some or all of the Desktop Effects might have to be disabled to run efficiently.

---

### Post by rivera151 on 2011-05-01
Thanks dabl.  I looked around the internet and someone on the kde forums suggested to someone else to try it first with another user to rule out user screw-up.  I created a new user, and lo and behold, it works.  So obviously, I messed it up.  Unfortunately, that was the last post on that thread, so even if that was the other person's problem, the way to solve it was not there.

Can someone point me in the right direction?  Deleting .kde will probably fix it, but I'd like to try something less drastic first.

Ricardo

---

