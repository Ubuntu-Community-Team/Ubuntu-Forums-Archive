---
title: "Lost display control due to Nvidia current update"
date: 2013-04-15
forum: Multimedia Software
---

### Post by ineuw on 2013-04-15
Is there a way to reset the video to the basic working defaults and start from the beginning without having to re-install Xubuntu 12.04? This is a simplified list of what works and what doesn't after login. My problems began when I tried to set aliasing (as in ClearType in Windows) because I can hardly read the LCD screen without it, even if the resolution is set 1280 x 720.  

[LIST=1]
[*] It's a single user setup, there is a login screen but no password is required.
[*] After the appearance of the desktop, there is no visible mouse pointer, but guessing the upper left corner menu access it highlights the drop down menu choices and I can navigate to the Settings panel. 
[*] On opening the Settings panel, the mouse shows up as a heavy **X**.
[*] 'Desktop' and 'Display' sub panel contents are visible and function, but the 'Window Manager' and the 'Window Manager Tweaks' sub panels are blank and plain gray.
[*] After closing the Settings panel, the pointer remains as X. 
[*] When selecting any application, the window is flat, no borders or controls to move or size and the windows are frozen in the top left corner of the screen.
[*] There is no full screen display, trying to set focus to a text field to type takes numerous attempts. (Firefox) and the menus don't function, and I can exit  applications only by keyboard shortcuts, Ctrl-Q, etc.
[*] Although the NTFS drives are mounted on startup, they don't show up on Thunar. Also, read/write access to USB is enabled but it remains read only.
[/LIST]

I used all the boot recovery options and it reports that all software is current and the volume is clean. I am sure it's a video related setting

Any suggestions? My gratitude in advance. - My signature shows additional info.

---

### Post by dargaud on 2013-04-15
To reset your configuration, in text mode (after killing X):
$ sudo nvidia-xconfig

---

### Post by ineuw on 2013-04-15
> **dargaud said:**
> To reset your configuration, in text mode (after killing X):
$ sudo nvidia-xconfig
dargaud, many thanks for your reply except how does one kill X (without getting caught or otherwise)?

I found the answer and now everything works. Thanks again!!

---

