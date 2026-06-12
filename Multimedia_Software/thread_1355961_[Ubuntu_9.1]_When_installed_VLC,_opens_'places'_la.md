---
title: "[Ubuntu 9.1] When installed VLC, opens 'places' launcher icons."
date: 2009-12-15
forum: Multimedia Software
---

### Post by johnston.ke on 2009-12-15
Prefaced by letting you know that I have searched the forums, and the other fixes do not stick.
[Edit: /facepalm for bad grammar in title.]

Opened computer folder in Nautilus and right clicked each folder and pressed open with file browser. It physically opened the folder in file browser, but left the problem unfixed aside from that.

Ran an alt-f2 nautilus-file-management-properties, went to behavior tab, and the box is checked already for always open in browser windows. Under media tab, removed VLC from list just to be sure, but still opens in VLC.

Right clicking on each folder and selecting properties opens a window with 5 tabs: Basic, emblems, Permission, Notes, Share. No option of "Open With" tab for setting a preference to nautilus.

Problem temporarily solved by uninstalling VLC.

---

### Post by mc4man on 2009-12-15
here's someone with similar issue only with amarok
[http://ubuntuforums.org/showthread.php?p=8500743#post8500743](http://ubuntuforums.org/showthread.php?p=8500743#post8500743)

The file you could try to edit that I didn't mention because the Op hasn't returned is this

```
gedit ~/.local/share/applications/mimeapps.list
```

Look for a line starting with inode/directory= and make it look like this
```

inode/directory=nautilus-folder-handler.desktop;
```

(nothing else needs to be listed on the line

If what I mentioned there or the above don't work then there is one more file that could be edited or file a bug report on launchpad

---

### Post by johnston.ke on 2009-12-15
> **mc4man said:**
> here's someone with similar issue only with amarok
[http://ubuntuforums.org/showthread.php?p=8500743#post8500743](http://ubuntuforums.org/showthread.php?p=8500743#post8500743)

The file you could try to edit that I didn't mention because the Op hasn't returned is this

```
gedit ~/.local/share/applications/mimeapps.list
```Look for a line starting with inode/directory= and make it look like this
```

inode/directory=nautilus-folder-handler.desktop;
```(nothing else needs to be listed on the line

If what I mentioned there or the above don't work then there is one more file that could be edited or file a bug report on launchpad

Thank you, that solved my problem. The line had "vlc.desktop" listed in front of the nautilus line of text you said to have. I simply deleted the VLC command, saved the file, and upon reinstalling VLC, it works as intended.

---

### Post by ChrisNZ on 2009-12-16
> **johnston.ke said:**
> Thank you, that solved my problem. The line had "vlc.desktop" listed in front of the nautilus line of text you said to have. I simply deleted the VLC command, saved the file, and upon reinstalling VLC, it works as intended.

Same here re the Amarok prob - [http://ubuntuforums.org/showthread.php?p=8500743#post8500743](http://ubuntuforums.org/showthread.php?p=8500743#post8500743)

---

### Post by zampes on 2011-02-02
Hi there,
Almost two years later, this solved my problem as well in 10.10. Thanks!:p

---

