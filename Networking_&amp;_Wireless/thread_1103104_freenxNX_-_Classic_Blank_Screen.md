---
title: "freenx/NX - Classic Blank Screen"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by Quantumstate on 2009-03-22
Suddenly yesterday when I tried to connect to my remote machine, after authentication and the NX logo, I got only a blank screen.  On the server it pops up a window saying, "KDE seems to be already running on this display."

So apparently my remote KDE session is trying to step on the local machine's.  Maybe the DISPLAY variable isn't set somewhere, but I have searched everywhere and can't find it.  I've found reference to changing in "nxnode":
DISPLAY=unix:$display
to
DISPLAY=localhost:$display
... but the first line does not exist in any file on my machine, and that suggestion was from 2007.

If I set the client to Shadow I can see that desktop and it works  fine, but the screensize is way off.

I've purged the server, node, and client packages and completely reinstalled, but exactly the same behavior.  Any idea what's wrong?

---

### Post by Quantumstate on 2009-03-23
No one else has had this blank screen lately?

---

