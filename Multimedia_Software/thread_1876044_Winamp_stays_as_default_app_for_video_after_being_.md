---
title: "Winamp stays as default app for video after being uninstalled"
date: 2011-11-05
forum: Multimedia Software
---

### Post by MadPoet on 2011-11-05
I installed Winamp via Winetricks a few days ago because I really like its media library, but after the instalation went smooth, the program didn't run (there was an error message, I don't recall what it said). I went to wintricks again to remove it, which apparently I managed because it doesn't appear there anymore, but despite that it's still the default app when I double-click in a video file (not audio, curiously). Also, on the default applications in the system settings it's SMPlayer that is defined as default app for video, so there's nothing I can change there. Is there any way I can change this?

---

### Post by mc4man on 2011-11-05
run this in a terminal
```
gedit ~/.local/share/applications/mimeapps.list
```

Look for instances of video mimetypes being associated with winamp or wine in the Default section, remove them

Or just r. click on any one Ex. of a video file > **Properties** > open with & switch to something else

---

### Post by MadPoet on 2011-11-05
> **mc4man said:**
> run this in a terminal
```
gedit ~/.local/share/applications/mimeapps.list
```

Look for instances of video mimetypes being associated with winamp or wine in the Default section, remove them

Or just r. click on any one Ex. of a video file > **Properties** > open with & switch to something else
I feel like such a n00b right now... (well, I am a n00b when it comes to linux...) I changed it on the properties. Thanks mate. :D

---

