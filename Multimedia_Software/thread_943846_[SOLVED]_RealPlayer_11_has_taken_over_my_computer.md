---
title: "[SOLVED] RealPlayer 11 has taken over my computer"
date: 2008-10-10
forum: Multimedia Software
---

### Post by kumoshk on 2008-10-10
I installed RealPlayer 11 for Linux on Ubuntu (Hardy Heron) a while back. Then, I got the Fluendo codecs&#8212;so, it stands to reason that I don't really want to use RealPlayer for as many things (mostly just for files specifically designed for RealPlayer).

The problem I have is that whenever I try to open a media file in Firefox, RealPlayer is set as the default 'open with' application. I can change this, but it only lasts until I open RealPlayer again. Also, it probably does similar things with files outside of Firefox.

Any ideas of how to fix this?

I might just uninstall RealPlayer, but I kind of want it around, just in case I need it for RealPlayer files. Plus, I don't know how to uninstall the thing&#8212;there's no apparent uninstall file, and it doesn't show up in apt-get.

Would deleting the folder I installed it into work, or would that cause errors?

A way to stop it from stealing my file associations is preferable.

---

### Post by kumoshk on 2008-10-10
I've discovered a way to uninstall it:

From the command-line, go to the program folder and then to a folder called postinst.

Then type sudo ./postuninst.sh

That should take care of it. Try running the other uninstall sh files if you just want specific things done.

You'll note that the program still exists, and can be 'reinstalled'. I think I'll keep it around if I want to try it again.

uninstall_moz_plugins.sh is probably what I was looking for, but I'll have to try it another time.

---

