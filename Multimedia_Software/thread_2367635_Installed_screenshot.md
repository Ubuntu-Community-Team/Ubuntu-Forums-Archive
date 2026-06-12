---
title: "Installed screenshot"
date: 2017-08-01
forum: Multimedia Software
---

### Post by steveredshaw on 2017-08-01
:(

Just installed Ubuntu Studio (17.04) and Screenshot (a very useful utility) has got stuck on the Save screen and won't start up with the Area screen. Any ideas how I can reset  - reinstall it - sort it out?

Thanks...

---

### Post by ajgreeny on 2017-08-01
Try renaming the **.config/xfce4/xfce4-screenshooter** in your home where the current settings are stored as a backup and see if that helps.

On my Xubuntu 16.04 and also in the two previous LTS versions I have set keyboard shortcuts of:- 
**Print-Screen** for full screen shots (command *xfce4-screenshooter*)
**Print-screen+Alt** for region (command *xfce4-screenshooter -r*)
**Print-screen+WinKey** for active-window (command *xfce4-screenshooter -w*)

---

### Post by steveredshaw on 2017-08-02
> **.config/xfce4/xfce4-screenshooter**

this does not exist in my setup - the tool used to present options to capture whole screen, active window or selected area, but now the tooltip reports "Take a screenshot of the entire screen", which it does - but where have the initial choices gone?

---

### Post by Dennis N on 2017-08-02
The screenshot panel applet only captures the entire screen. Menu > Accessories > Screenshot gives you options for capture area or active window.

---

### Post by ajgreeny on 2017-08-02
> **Dennis N said:**
> The screenshot panel applet only captures the entire screen. Menu > Accessories > Screenshot gives you options for capture area or active window.
I didn't remember that as I removed the panel app soon after adding it, possibly for that reason.
This is probably why I made those keyboard shortcuts though it's too long ago to remember. I would recommend you give them a try as they are a great saver of time clicking through the menus.

---

### Post by steveredshaw on 2017-08-02
;)
Yes, got that now - thanks for clearing that up - 2 tools, same name, same icon, slightly different modes of operation. On my xfce Add to Panel window, the description of the screen shot tool states "Take screenshots of the entire screen, of the active window or of a region" - however what you actually get is capture of the entire screen. Adding the Screenshot from the Menu to the panel gives you the version that does allow screen, window and region capture. Solved!

---

