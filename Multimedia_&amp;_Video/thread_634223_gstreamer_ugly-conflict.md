---
title: "gstreamer ugly-conflict"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by pubu on 2007-12-07
i downloaded the files required for the gstreamer through toem movie player.
But after the download it says:

"This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."

However if i switch to synaptec and try to install it.i get an error like this:

gstreamer0.10-plugins-ugly:
 Depends: libid3tag0 (>=0.15.1b) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable

Please understand that i'm a complete novice in LINUX and spend a little of your valuable time helping me out

---

### Post by sunburstgl on 2007-12-22
I HAVE THE SAME EXACT PROBLEM! it's driving me insane, and i have no idea how to fix it.

---

### Post by sunburstgl on 2007-12-22
hm...i think i may have found a way to fix it now

go to the following page
[http://packages.ubuntu.com/dapper/libs/gstreamer0.10-plugins-ugly](http://packages.ubuntu.com/dapper/libs/gstreamer0.10-plugins-ugly)

and scroll down to where it says "libid3tag0" click on it. then install it onto your system.
then follwing that go back to the first page and find the "libmad0" click on that and install it.

go once again back to the first page. this time try installing gstreamer0.10-plugins-ugly and it should work. it worked for me.

if you have any questions or if i wasn't specific enough let me know.

---

### Post by aysiu on 2007-12-22
**Step 1**:
[Get a *fresh* repositories list](http://www.psychocats.net/ubuntu/sources#key)

**Step 2**
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update && sudo apt-get install gstreamer0.10-plugins-ugly
```

---

