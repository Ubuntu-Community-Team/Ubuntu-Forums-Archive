---
title: "[SOLVED] pictures/videos in firefox"
date: 2008-12-18
forum: Multimedia Software
---

### Post by johnlundy on 2008-12-18
I remember on Windows that whenever I'd click a link to view an image or a video, Firefox would usually navigate to that address and display said picture/video. Now on Ubuntu (Intrepid), I'm always prompted to open in Image Viewer or save it to the desktop. Is there any way to do this other than specifying that Firefox always be the default image/video viewer? Naturally, I don't want pictures/videos on my desktop to be opened in Firefox, but if I click a link for a .jpg, I'd like it to just load up the 'page' with that image on it.

Any suggestions?

Thanks in advance.

---

### Post by ajgreeny on 2008-12-18
That's very odd, as the default is to open jpegs in a firefox page or tab, as far as I'm aware.  Try temporarily renaming your current hidden .mozilla folder in your home folder (hit ctrl+H if it is not showing)  That may give you back the normal? behaviour.  You can then copy back your cookies and bookmarks to the new profile, but I would avoid other parts of the old profile as part of that may be the cause of the problem.

If that doesn't help, I can't think what else may solve it for you.

---

### Post by johnlundy on 2008-12-18
That did work to rename the .mozilla folder, but I can't seem to get my bookmarks to transfer back over.

---

### Post by ajgreeny on 2008-12-19
It's now called **places.sqlite** in your .mozilla/firefox/alphanumeric.default.

---

