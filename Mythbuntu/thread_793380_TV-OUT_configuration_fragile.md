---
title: "TV-OUT configuration fragile?"
date: 2008-05-13
forum: Mythbuntu
---

### Post by dsbw on 2008-05-13
I plugged my MythTV box into my TV via VGA & HDMI and found I could get the right resolution going through the HDMI with a little tweaking (and some grief, since the VGA wanted to go to 640x480). 

But then, when I activated the VNC, it wiped out the HDMI and forced me to go back to VGA. That seemed to happen with some other minor fiddling (though I can't recall which right now).

Do I need to copy my Xorg.conf file once I have it working so that I can copy it back periodically?

---

### Post by dsbw on 2008-05-16
No thoughts, anyone?

---

### Post by agamotto on 2008-05-16
> **dsbw said:**
> No thoughts, anyone?

I am still trying to puzzle out what VNC would have to do with tv-out settings...  Go into the Nvidia settings/tv-out settings and try something like 720p for output and see if that makes any difference.  That should ensure decent output for both VGA and HDMI.

---

### Post by dsbw on 2008-05-16
Thanks, I'll try that and see if it works....

---

