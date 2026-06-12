---
title: "Ubuntu 10.04 Banshee streamrecorder no longer works after upgrade"
date: 2011-02-04
forum: Multimedia Software
---

### Post by joekm on 2011-02-04
[I]Have Ubuntu 10.04 with the Banshee team PPA repository.  Installed Banshee 1.8.0 which recently upgraded to 1.8.1.  Since the upgrade, the streamrecorder plug-in no longer works nor does it present any conversion options.

Any idea what the problem might be?[/I]

[SOLVED]

The problem seemed to surround "gstreamer element autoaudiosink"

So, first I tried the following...

rm -rf ~/.gconf/system/gstreamer
rm -rf ~/.gstreamer-0.10

Then rebooting...this didn't work


Then I tried simply deleting the  ~/.config/banshee-1 directory and letting Banshee rebuild it when I started it up again.  I had to re-set my preferences, and I lost my one saved radio station, but my liveradio settings were still intact and the streamrecorder plugin now works just fine.

I will post this as [SOLVED] but, if anyone has a more elegant solution, please add it to the thread.

---

